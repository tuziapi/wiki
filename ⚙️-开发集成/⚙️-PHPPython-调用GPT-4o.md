# ⚙️ PHP/Python 调用GPT-4o

## 目标

通过最基本的 `curl` 请求调用 Tu-Zi 的 OpenAI 协议对话接口，生成图片结果，并提供 PHP 和 Python 的代码示例。

**解决吉卜力出图问题，以下代码中第一张图找张千与千寻的图，第二张是要转化的图，执行就可以了。**

## 准备工作


1. 登录 [Tu-Zi API Token 页面](https://api.tu-zi.com/token) 创建一个 API Token。
2. API 基础地址为 `https://api.tu-zi.com/v1`，对话请求地址为 `https://api.tu-zi.com/v1/chat/completions`。
3. 指定模型（以下三种模型均可按需选择）：
   * **gpt-4o-all**：按 token 计费，价格便宜，稳定性一般。
   * **gpt-4o-image**：按次计费，价格便宜，不保证稳定性。
   * **gpt-4o-image-vip**：按次计费，价格较高，更为稳定

## PHP代码实现

```php
<?php
/*
* 这个脚本用于调用GPT-4o-all及相关模型，提交提示词和2张图片，并返回结果
* 请确保你已经安装了PHP的cURL扩展
* 请替换$api_token为你自己的API密钥
* 请确保output目录存在或可写入
* 放到web服务器里，浏览器打开地址，只要不成功，就会等20秒刷到出来为止
*/
//提示词和输入图片，图片请放到和脚本同一目录
$prompt = "请参照第一张图片的风格，重绘第二张图片，输出比例按照第二张图片";
$image_1 = "ff945c73-86df-461f-a858-fcb08a7f9939.png";
$image_2 = "9c8b2b03-9c40-4fdd-9585-7b39ba3c28b0.png";

//可以通过http接收外部模型指定，默认是gpt-4o-all
$model = isset($_GET['model']) ? $_GET['model'] : "gpt-4o-all";
// 这个不用改
$api_url = "https://api.tu-zi.com/v1/chat/completions";
// 这个请到 https://api.tu-zi.com/token 自己创建
$api_token = "你的api token";

// 准备请求数据
$data = [
    "model" => $model,
    "stream" => false,
    "messages" => [
        [
            "role" => "user",
            "content" => [
                [
                    "type" => "text",
                    "text" => $prompt,
                ],
                [
                    "type" => "image_url",
                    "image_url" => [
                        "url" => "data:image/png;base64," . base64_encode(file_get_contents($image_1)),
                    ],
                ],
                [
                    "type" => "image_url",
                    "image_url" => [
                        "url" => "data:image/png;base64," . base64_encode(file_get_contents($image_2)),
                    ],
                ],
            ],
        ],
    ],
];

// 初始化cURL请求
$ch = curl_init();
curl_setopt($ch, CURLOPT_URL, $api_url);
curl_setopt($ch, CURLOPT_RETURNTRANSFER, true);
curl_setopt($ch, CURLOPT_POST, true);
curl_setopt($ch, CURLOPT_HTTPHEADER, [
    "Authorization: Bearer $api_token",
    "Content-Type: application/json"
]);
curl_setopt($ch, CURLOPT_POSTFIELDS, json_encode($data));

// 设置超时时间为10分钟
curl_setopt($ch, CURLOPT_TIMEOUT, 1200);

$tm = time();
// 执行请求并获取响应
$response = curl_exec($ch);
//这里debug输入和输出数据便于调试
var_dump($data);
echo "<hr/>";
var_dump($response);
echo "<hr/>";


if (curl_errno($ch)) {
    echo "cURL Error: " . curl_error($ch);
    curl_close($ch);
    exit;
}
curl_close($ch);

// 解析响应
$result = json_decode($response, true);
if (isset($result['error'])) {
    echo "API Error: " . $result['error']['message'];
    //如果是网络问题导致没有请求成功，等20秒再刷页面
    echo "<script>
        setTimeout(function() {
            location.reload();
        }, 20000);
    </script>";
    exit;
}

// 遍历result，提取content字段中的图片地址并保存
if (isset($result['choices']) && is_array($result['choices'])) {
    $download_success = false;
    foreach ($result['choices'] as $choice) {
        if (isset($choice['message']['content'])) {
            $content = $choice['message']['content'];
            // 使用正则表达式提取markdown中的图片地址
            if (preg_match_all('/!\[.*?\]\((https?:\/\/[^\s]+)\)/', $content, $matches)) {
                foreach ($matches[1] as $image_url) {
                    $image_data = file_get_contents($image_url);
                    if ($image_data !== false) {
                        $file_name = $result['id'] . '-' . $choice['index'] . '.png';
                        $output_path = __DIR__ . '/output/' . $file_name;
                        if (!is_dir(__DIR__ . '/output')) {
                            mkdir(__DIR__ . '/output', 0777, true);
                        }
                        file_put_contents($output_path, $image_data);
                        echo "图片已保存到: " . $output_path . "\n";
                        $download_success = true;
                    } else {
                        echo "无法下载图片数据: " . $image_url . "\n";
                    }
                }
            } else {
                echo "未能提取到图片地址。\n";
            }
        }
    }
    if (!$download_success) {
        echo "<script>
            setTimeout(function() {
                location.reload();
            }, 20000);
        </script>";
    }
} else {
    echo "返回值格式错误。\n";
    echo "<script>
        setTimeout(function() {
            location.reload();
        }, 20000);
    </script>";
}
```

## python脚本（含debug，非流模式）

```python
"""
* 此脚本用于调用GPT-4o-all及相关模型，提交提示词和图片，并返回处理结果
* 支持无图、单图或多图（最多10张）的情况
* 请确保已安装Python环境并安装所需依赖库（如requests，python-dotenv）
* 请复制.env.template为.env并填写您的API密钥
* 确保output目录存在或脚本有权限创建该目录
* 脚本会尝试下载返回的图片并保存到output目录： 运行 python gpt.py （看你存什么文件名了）
"""

import os
import base64
import requests
import time
from dotenv import load_dotenv

# 加载环境变量
load_dotenv()

# 提示词和输入图片，图片请放到和脚本同一目录
prompt = "把照片中的人物变成 泡泡玛特 公仔包装盒的风格，以等距视角（isometric）呈现，并在包装盒上标注标题为"某某"（具体见文末）。包装盒内展示的是照片中人物形象，旁边搭配有日常必备物品（具体见文末）同时，在包装盒旁边还应呈现该公仔本体的实物效果，采用逼真的、具有真实感的渲染风格。标题为雷总，日常必备物品帽子、鞋子、耳坠。"
# 图片列表，可以包含0-10张图片
images = [
    "5.jpg"
]

# 从环境变量获取配置
model = os.getenv("MODEL", "gpt-4o-all")
api_url = "https://api.tu-zi.com/v1/chat/completions"
api_token = os.getenv("API_TOKEN")

# 验证API Token
if not api_token:
    print("错误：未设置API_TOKEN环境变量")
    print("请复制.env.template为.env并填写您的API密钥")
    exit(1)

# 准备请求数据
def prepare_image_data(image_path):
    try:
        with open(image_path, "rb") as img_file:
            encoded_data = base64.b64encode(img_file.read()).decode("utf-8")
            print(f"已准备图片数据: {image_path}（内容已隐藏以确保安全）")
            return "data:image/png;base64," + encoded_data
    except Exception as e:
        print(f"准备图片数据时出错: {image_path} - {e}")
        raise

# 验证图片数量
if len(images) > 10:
    print("错误：图片数量不能超过10张")
    exit(1)

# 添加调试信息
print(f"使用的模型: {model}")
print(f"API 地址: {api_url}")
print(f"图片数量: {len(images)}")
for i, img in enumerate(images, 1):
    print(f"图片 {i} 路径: {img}")

# 构建消息内容
message_content = [{"type": "text", "text": prompt}]

# 添加图片到消息内容
for image_path in images:
    try:
        image_data = prepare_image_data(image_path)
        message_content.append({
            "type": "image_url",
            "image_url": {"url": image_data}
        })
    except Exception as e:
        print(f"处理图片时出错: {image_path} - {e}")
        exit(1)

data = {
    "model": model,
    "stream": False, 
    "messages": [
        {
            "role": "user",
            "content": message_content
        }
    ],
}

# 添加调试信息
print(f"请求数据已准备好（图片内容已隐藏）。")

# 发送请求
headers = {
    "Authorization": f"Bearer {api_token}",
    "Content-Type": "application/json",
}

try:
    response = requests.post(api_url, json=data, headers=headers, timeout=1200)
    print(f"响应状态码: {response.status_code}")
    print(f"响应内容: {response.text}")
except Exception as e:
    print(f"发送请求时出错: {e}")
    raise

# 处理响应
if response.status_code != 200:
    print(f"API 错误: {response.status_code} - {response.text}")
    exit()

try:
    result = response.json()
    print(f"响应 JSON 数据: {result}")
except Exception as e:
    print(f"解析响应 JSON 时出错: {e}")
    exit()

if "error" in result:
    print(f"API 错误: {result['error']['message']}")
    exit()

# 遍历result，提取content字段中的图片地址并保存
if "choices" in result and isinstance(result["choices"], list):
    download_success = False
    for choice in result["choices"]:
        if "message" in choice and "content" in choice["message"]:
            content = choice["message"]["content"]
            print(f"正在处理内容: {content}")
            # 使用正则表达式提取markdown中的图片地址
            import re
            matches = re.findall(r"!\[.*?\]\((https?://[^\s]+)\)", content)
            for image_url in matches:
                try:
                    print(f"正在下载图片: {image_url}")
                    image_data = requests.get(image_url).content
                    file_name = f"{result['id']}-{choice['index']}.png"
                    output_dir = os.path.join(os.getcwd(), "output")
                    os.makedirs(output_dir, exist_ok=True)
                    output_path = os.path.join(output_dir, file_name)
                    with open(output_path, "wb") as f:
                        f.write(image_data)
                    print(f"图片已保存到: {output_path}")
                    download_success = True
                except Exception as e:
                    print(f"无法下载图片数据: {image_url} - {e}")
    if not download_success:
        print("未成功下载任何图片。")
else:
    print("返回值格式错误。")
```

.env示例

```
# API Token配置
API_TOKEN=sk-eKf0******

# 模型配置（可选，默认为gpt-4o-all）
MODEL=gpt-4o-image-vip
```

批处理（顺序） https://github.com/wangjueszu/gpt-4o-py