# 🎨 Seedream API

本指南提供了如何使用 Seedream API 进行图像生成的说明，以及一个 Python 代码示例。

## API 端点

API 的基础 URL 是：`https://api.tu-zi.com` 用于图像生成的特定端点是：`/v1/images/generations`

## 认证

认证通过 `Authorization` 请求头中的承载令牌（Bearer Token）进行。

**请求头参数：**

* `Authorization`：`string` (可选)
  * 示例：`Bearer {{YOUR_API_KEY}}`

请将 `{{YOUR_API_KEY}}` 替换为您的实际 API 密钥。

## 请求体

请求体应为 `application/json` 格式。

**请求体参数：**

* `model`：`string` (必需)
  * 用于图像生成的模型（例如 "seedream-3.0"）。
* `prompt`：`string` (必需)
  * 对于文生图，提供描述性提示。
  * 对于图生图，提供基础图像的 URL，后跟提示。
    * 示例：`https://tuziai.oss-cn-shenzhen.aliyuncs.com/kling_watermark.png 让这个女人带上眼镜 衣服换个颜色`
* `~~n~~`~~：~~`~~integer~~` ~~(必需)~~
  * ~~要生成的图像数量。~~
* `response_format`：`string` (必需)
  * 响应的格式。
  * 枚举值：`url`、`b64_json`、`oss_url`
    * `url`：有效期 24 小时。
    * `oss_url`：有效期 7 天。
* `size`：`string` (必需)
  * 生成图像的尺寸 (宽x高)。

## 图像尺寸建议

### seedream-4.0

* 默认值：2048x2048
* 方式1 示例：指定生成图像的分辨率，并在prompt中用自然语言描述图片宽高比、图片形状或图片用途，最终由模型判断生成图片的大小。 可选值：`1K`、`2K`、`4K`
* 方式2 示例：指定生成图像的宽高像素值： 默认值：2048x2048 总像素取值范围：\[1024x1024, 4096x4096\] 宽高比取值范围：\[1/16, 16\]
* **推荐的宽高像素值:**
  * 1:1：`2048x2048`
  * 4:3：`2304x1728`
  * 3:4：`1728x2304`
  * 16:9：`2560x1440`
  * 9:16：`1440x2560`
  * 3:2：`2496x1664`
  * 2:3：`1664x2496`
  * 21:9：`3024x1296`

### seedream-3.0

* **推荐：** 1.3K 到 1.5K 分辨率，以获得更好的质量和均衡的性能。1K 和 2K 分辨率的表现可能相对较弱。
* **1.3K 建议比例和尺寸 (宽 x 高)：**
  * 1:1：`1328x1328`
  * 4:3：`1472x1104`
  * 3:2：`1584x1056`
  * 16:9：`1664x936`
  * 21:9：`2016x864`
* **1.5K 建议比例和尺寸 (宽 x 高)：**
  * 1:1：`1536x1536`
  * 4:3：`1472x1104` (注意：这似乎与 1.3K 4:3 相同，请验证是否如此)
  * 3:2：`1584x1056` (注意：这似乎与 1.3K 3:2 相同，请验证是否如此)
  * 16:9：`1664x936` (注意：这似乎与 1.3K 16:9 相同，请验证是否如此)
  * 21:9：`2016x864` (注意：这似乎与 1.3K 21:9 相同，请验证是否如此)

## Python 代码示例 (`seedream-4.0.py`)

```python
import http.client
import json
import os

# 请确保您已将 API Key 存储在环境变量 ARK_API_KEY 中
# 或者直接在下面代码中替换 {{YOUR_API_KEY}}
api_key = "sk-**" # 使用您提供的API Key

conn = http.client.HTTPSConnection("api.tu-zi.com") # 注意：根据您的最新修改，这里可能是 api.tu-zi.com

# 使用原始脚本中的prompt，其他参数来自新示例
payload_dict = {
  "model": "doubao-seedream-4-0-250828",
  "prompt": "鱼眼镜头，一只猫咪的头部，画面呈现出猫咪的五官因为拍摄方式扭曲的效果。", # 来自原始脚本
			
   # image 参数 仅 doubao-seedream-4.0支持
  "image": "https://picx.zhimg.com/v2-d6f44389971daab7e688e5b37046e4e4_720w.jpg?source=172ae18b"
  "response_format": "url", # 返回形式
  "size": "2048x2048" 
}
payload = json.dumps(payload_dict)

headers = {
   'Authorization': f'Bearer {api_key}',
   'Content-Type': 'application/json'
}

conn.request("POST", "/v1/images/generations", payload, headers)
res = conn.getresponse()
data = res.read()
response_data = data.decode("utf-8")

print(f"响应状态: {res.status}")
print(f"响应原因: {res.reason}")
print(f"响应内容: {response_data}")

# 假设返回的json结构中包含一个名为 "data" 的列表，其中每个元素有一个 "url" 字段
# 这部分可能需要根据实际返回的json结构进行调整
try:
    response_json = json.loads(response_data)
    if res.status == 200 and response_json.get("data") and isinstance(response_json["data"], list) and len(response_json["data"]) > 0:
        image_url = response_json["data"][0].get("url")
        if image_url:
            print(f"图片 URL: {image_url}")
        else:
            print("在响应数据中找不到 'url'。")
    else:
        print(f"API 请求失败或返回意外数据。状态: {res.status}")
except json.JSONDecodeError:
    print("解码 JSON 响应失败。")

conn.close()
```

**seedream4.0 以下要使用图生图功能，请按如下方式修改** `**payload_dict**`**：**

```python
# ... (脚本的其他部分)

# 图生图示例:
payload_dict = {
  "model": "seedream-3.0",
  "prompt": "https://tuziai.oss-cn-shenzhen.aliyuncs.com/kling_watermark.png 让这个女人带上眼镜 衣服换个颜色",
  "n": 1,
  "response_format": "url",
  "size": "1328x1328" # 根据需要调整尺寸
}

# ... (脚本的其余部分)
```

请记住将 `"sk-**"` 替换为您的实际 API 密钥或将其设置为环境变量。