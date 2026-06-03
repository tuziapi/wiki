# ⚙️ Python 调用任意模型

### 文本对话

```plaintext
import os from openai import OpenAI

client = OpenAI(     # This is the default and can be omitted     api_key = "sk-u1oNdFZblFE09tVx2c42981a97De42C\*\*\*\*\*",     base_url = "https://api.tu-zi.com/v1", )

chat_completion = client.chat.completions.create(     messages=\[         {             "role": "user",             "content": "背个望庐山瀑布",         }     \],     model="gpt-4", )

print(chat_completion)
```

### 上传图片识别（支持模型gpt-4o-fast，openai-gpt-4o，gpt-4o-all等等）

```plaintext
import base64 import requests

# OpenAI API Key

api_key = "sk-BdFjUwDwNyPjcv78\*\*\*\*\*"

# Function to encode the image

def encode_image(image_path): with open(image_path, "rb") as image_file: return base64.b64encode(image_file.read()).decode('utf-8')

# Path to your image

image_path = r"C:\\Users\\wa\*\*\*\\Downloads\\兔子圆形.png"  # 替换为您本地图片的路径

# Getting the base64 string

base64_image = encode_image(image_path)

# 设置请求头

headers = { "Content-Type": "application/json", "Authorization": f"Bearer {api_key}" }

# 设置请求的payload

payload = { "model": "gpt-4o-fast",  # 使用的模型 "messages": \[ { "role": "user", "content": \[ { "type": "text", "text": "What's in this image?" }, { "type": "image_url", "image_url": { "url": f"data:image/jpeg;base64,{base64_image}" } } \] } \], "max_tokens": 300 }

# 发送POST请求到自定义的API地址

response = requests.post("https://api.tu-zi.com/v1/chat/completions", headers=headers, json=payload)

# 解析响应

response_data = response.json()

# 打印文本内容

print("Text Response:", response_data) 
```