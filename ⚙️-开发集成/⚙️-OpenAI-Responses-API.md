# ⚙️ OpenAI Responses API

# 兔子API调用工具使用说明

## 📖 概述

这是一个用于调用兔子API (`api.tu-zi.com`) 的Python脚本工具，支持OpenAI的response接口进行AI对话交互（如o3-pro仅支持该接口）。脚本会自动保存API响应到带时间戳的文件中，方便后续查看和分析。

## 🚀 快速开始

### 环境要求

* Python 3.6+
* requests库

### 安装依赖

```bash
pip install requests
```

### 基本使用


1. **下载脚本**：将 [response.py](https://tuziai.oss-cn-shenzhen.aliyuncs.com/response.py) 文件下载到本地
2. **配置API密钥**：修改脚本中的Authorization token
3. **运行脚本**：

   ```bash
   python response.py
   ```

## ⚙️ 配置说明

### API配置

在 `response.py` 文件中需要配置以下参数：

```python
# API端点
url = "https://api.tu-zi.com/v1/responses"

# 请求头配置
headers = {
    "Content-Type": "application/json",
    "Authorization": "Bearer YOUR_API_KEY_HERE"  # 替换为您的API密钥
}

# 请求负载
payload = {
    "model": "o3-pro",        # 模型名称
    "input": "您的问题内容"    # 要发送给AI的内容
}
```

### 重要参数说明

| 参数  | 说明  | 示例  |
|-----|-----|-----|
| `model` | 使用的AI模型 | `"o3-pro"` |
| `input` | 发送给AI的提示内容 | `"请帮我写一个Python函数"` |
| `Authorization` | API认证令牌 | `"Bearer sk-xxx..."` |

## 📝 使用方法

### 方法一：直接修改脚本


1. 打开 `response.py` 文件
2. 修改 `payload["input"]` 中的内容为您的问题
3. 确保API密钥正确
4. 运行脚本

### 方法二：创建自定义函数

```python
import requests
import json
from datetime import datetime

def call_tuzi_api(prompt, api_key, model="o3-pro"):
    """
    调用兔子API的封装函数
    
    Args:
        prompt (str): 要发送的提示内容
        api_key (str): API密钥
        model (str): 使用的模型，默认为o3-pro
    
    Returns:
        dict: API响应结果
    """
    url = "https://api.tu-zi.com/v1/responses"
    
    headers = {
        "Content-Type": "application/json",
        "Authorization": f"Bearer {api_key}"
    }
    
    payload = {
        "model": model,
        "input": prompt
    }
    
    try:
        response = requests.post(url, headers=headers, json=payload)
        
        if response.status_code == 200:
            return {
                "success": True,
                "data": response.json()
            }
        else:
            return {
                "success": False,
                "error": f"状态码: {response.status_code}",
                "message": response.text
            }
            
    except requests.exceptions.RequestException as e:
        return {
            "success": False,
            "error": "连接错误",
            "message": str(e)
        }

# 使用示例
api_key = "sk-rhgHhr4F6sPXdOdrdHg4Nt3DMQQXo0I1LUCW1zodmW4LYXyK"
result = call_tuzi_api("请介绍一下Python", api_key)

if result["success"]:
    print("API调用成功:")
    print(json.dumps(result["data"], indent=2, ensure_ascii=False))
else:
    print("API调用失败:")
    print(f"错误: {result['error']}")
    print(f"详情: {result['message']}")
```

## 📁 输出文件

脚本会自动创建带时间戳的输出文件：

* **文件名格式**: `api_response_YYYYMMDD_HHMMSS.txt`
* **文件内容**: 包含完整的请求和响应信息
* **编码**: UTF-8

### 输出文件示例

```
=== API请求开始 - 2024-01-15 14:30:25 ===
请求URL: https://api.tu-zi.com/v1/responses
请求模型: o3-pro

请求成功！
服务器响应：
{
  "content": "这里是AI的回复内容...",
  "model": "o3-pro",
  "usage": {
    "tokens": 150
  }
}

=== 主要内容 ===
这里是AI的回复内容...

=== 请求结束 - 2024-01-15 14:30:28 ===
```

## 🔧 自定义修改

### 修改输出格式

可以修改 `print_and_save` 函数来自定义输出格式：

```python
def print_and_save(content, file_path=output_file):
    """自定义输出格式"""
    timestamp = datetime.now().strftime("%H:%M:%S")
    formatted_content = f"[{timestamp}] {content}"
    print(formatted_content)
    with open(file_path, 'a', encoding='utf-8') as f:
        f.write(formatted_content + '\n')
```

### 添加重试机制

```python
import time

def call_api_with_retry(url, headers, payload, max_retries=3):
    """带重试机制的API调用"""
    for attempt in range(max_retries):
        try:
            response = requests.post(url, headers=headers, json=payload)
            if response.status_code == 200:
                return response
        except requests.exceptions.RequestException as e:
            if attempt < max_retries - 1:
                print(f"第{attempt + 1}次尝试失败，3秒后重试...")
                time.sleep(3)
            else:
                raise e
    return None
```

## ⚠️ 注意事项

### 安全提醒


1. **保护API密钥**: 不要将包含真实API密钥的代码提交到公共仓库
2. **使用环境变量**: 建议通过环境变量管理API密钥

```python
import os
api_key = os.getenv('TUZI_API_KEY', 'your-default-key')
```


3. **访问频率限制**: 注意API的调用频率限制，避免过度请求

### 错误处理

脚本已包含基本的错误处理：

* **网络连接错误**: 自动捕获并显示连接问题
* **HTTP状态码错误**: 显示具体的错误状态码和信息
* **JSON解析错误**: 处理响应格式异常

### 常见问题

**Q: 出现401错误怎么办？** A: 检查API密钥是否正确，确保格式为 `Bearer sk-xxx...`

**Q: 请求超时怎么办？** A: 可以在requests.post中添加timeout参数：

```python
response = requests.post(url, headers=headers, json=payload, timeout=30)
```

**Q: 如何处理中文编码问题？** A: 脚本已设置UTF-8编码，如仍有问题，检查系统终端编码设置

## 🌟 高级用法

### 批量处理

```python
def batch_process(prompts, api_key):
    """批量处理多个提示"""
    results = []
    for i, prompt in enumerate(prompts):
        print(f"处理第{i+1}/{len(prompts)}个请求...")
        result = call_tuzi_api(prompt, api_key)
        results.append(result)
        time.sleep(1)  # 避免请求过快
    return results

# 使用示例
prompts = [
    "什么是机器学习？",
    "Python有什么优势？",
    "如何学习编程？"
]

results = batch_process(prompts, api_key)
```

### 结果分析

```python
def analyze_responses(results):
    """分析API响应结果"""
    success_count = sum(1 for r in results if r["success"])
    total_count = len(results)
    
    print(f"总请求数: {total_count}")
    print(f"成功数: {success_count}")
    print(f"成功率: {success_count/total_count*100:.1f}%")
    
    # 计算平均响应长度
    successful_responses = [r["data"]["content"] for r in results if r["success"]]
    if successful_responses:
        avg_length = sum(len(content) for content in successful_responses) / len(successful_responses)
        print(f"平均响应长度: {avg_length:.0f}字符")
```