# 🎨 香蕉2｜gemini-3-pro-image-preview  快速入门

# 概述

#### **gemini-3-pro-image-preview** API 允许您使用 **gemini-3-pro-image-preview - (nano banana 2)**模型根据文本提示生成和编辑图像（**nano banana 2、gemini-2.5-flash-image**、**gemini-2.5-flash-image-preview**一样操作）。

目前，图像生成可通过 **图像 API** 调用和 **Chat API**调用（目前支持default、Gemini原价分组的令牌，若其中一个满负荷可更换分组）。

**模型概述:**

**同步模型**

**gemini-3-pro-image-preview         (nano-banana-2)       — 生成质量 1k**

**gemini-3-pro-image-preview-hd  (nano-banana-2-hd) — 生成质量 2k**

**gemini-3-pro-image-preview-2k  (nano-banana-2-2k)  — 生成质量 2k**

**gemini-3-pro-image-preview-4k  (nano-banana-2-4k) — 生成质量 4k**


**异步模型**

**gemini-3-pro-image-preview-async**

**gemini-3-pro-image-preview-2k-async**

**gemini-3-pro-image-preview-4k-async**


**分组概括:** 

* 分组价格「Gemini原价分组」>「default」
* default返回格式 : url链接 / base64  （可自定义）
* Gemini原价分组返回base64文件

**api调用概括:**

推荐接口:

推荐使用 chat 接口调用

图像 API 提供四个端点，分别对应不同功能：

| 端点  | 作用  | 调用接口文档 |
|-----|-----|--------|
| **chat** | 对话生成图像（**支持的分组通用**） | **<https://tuzi-api.apifox.cn/343646954e0>** |
| **generate** | 根据文本提示生成图像（**default分组**） | **<https://tuzi-api.apifox.cn/343646956e0>** |
| **edit** | 修改现有图像（可使用新的提示、分区或整体替换）（**default分组**） | **<https://tuzi-api.apifox.cn/343646957e0>** |
| **谷歌格式** | 生成图像（**Gemini原价分组**） | **<https://tuzi-api.apifox.cn/360926406e0>** |

# 一、开箱即用

## 1.1 兔子网站 chat-mj 工具


1. 登录

 ![](https://tuziai.oss-cn-shenzhen.aliyuncs.com/wiki/pasted_graphic1.png)

2\. 点击控制台添加令牌

 ![](https://tuziai.oss-cn-shenzhen.aliyuncs.com/wiki/chat/nextchat/2.png)

3\. 添加一个无限制令牌/ 可以自由设置

 ![](https://tuziai.oss-cn-shenzhen.aliyuncs.com/wiki/chat/%E4%BB%A4%E7%89%8C2.png)

 ![](https://tuziai.oss-cn-shenzhen.aliyuncs.com/wiki/chat/nextchat/3.png)

4\.1. 使用 Chat-MJ 网页版或者客户端均可，操作相同    ![chat-mj-5.png](https://tuziai.oss-cn-shenzhen.aliyuncs.com/wiki/chat/chat-mj/chat-mj-5.png) 

 ![chat-mj-1.png](https://tuziai.oss-cn-shenzhen.aliyuncs.com/wiki/chat/chat-mj/chat-mj-1.png)

4\.2. 修改自定义模型和默认模型

 ![](https://wiki.tu-zi.com/api/files.get?sig=eyJhbGciOiJIUzI1NiIsInR5cCI6IkpXVCJ9.eyJrZXkiOiJ1cGxvYWRzL2I3MTgwNDFlLWUwNjItNDRlMy1iNTljLTlkYzliNjNjODczMi9kNjZlZjdiMi04NmJiLTQ2MmQtYmU3Ny03ODIxNjZhM2ZlMzgvaW1hZ2UucG5nIiwidHlwZSI6ImF0dGFjaG1lbnQiLCJpYXQiOjE3ODA0NTQ5MjcsImV4cCI6MTc4MDQ1ODUyN30.gKASn7VlveswyOpbM1NoXdd4UDmZ1OWxkFbSo4XI0jE " =621x480")     

**nano banana 2 效果**


 ![](https://wiki.tu-zi.com/api/files.get?sig=eyJhbGciOiJIUzI1NiIsInR5cCI6IkpXVCJ9.eyJrZXkiOiJ1cGxvYWRzL2I3MTgwNDFlLWUwNjItNDRlMy1iNTljLTlkYzliNjNjODczMi9hZmYyZWM2OC03ZTYzLTRkOTAtYTIzNi1lOTdjYjk3YjJlZTkvaW1hZ2UucG5nIiwidHlwZSI6ImF0dGFjaG1lbnQiLCJpYXQiOjE3ODA0NTQ5MjcsImV4cCI6MTc4MDQ1ODUyN30.xlXhuEiBX4lnfQfXA-RcrJb2iZYkTM_Qs8a36xIdUiQ " =1484x587")

 ![](https://wiki.tu-zi.com/api/files.get?sig=eyJhbGciOiJIUzI1NiIsInR5cCI6IkpXVCJ9.eyJrZXkiOiJ1cGxvYWRzL2I3MTgwNDFlLWUwNjItNDRlMy1iNTljLTlkYzliNjNjODczMi8zMDhkMzg2Yi00ZTEyLTRlYjMtYjliYS1hM2FkYmJkMjgyMWIvd2Vjb20tdGVtcC0yMTk3NjU4LTIyMzk4N2NkMDc4MjYxYTEzNDZhNjgzYTNmYjJiY2IxLnBuZyIsInR5cGUiOiJhdHRhY2htZW50IiwiaWF0IjoxNzgwNDU0OTI3LCJleHAiOjE3ODA0NTg1Mjd9.c9FDtY2HXFhS0se3sezLuHXWRdduq3EERdAx6X3NLC4 " =1408x768")

 ![](https://wiki.tu-zi.com/api/files.get?sig=eyJhbGciOiJIUzI1NiIsInR5cCI6IkpXVCJ9.eyJrZXkiOiJ1cGxvYWRzL2I3MTgwNDFlLWUwNjItNDRlMy1iNTljLTlkYzliNjNjODczMi9kOTZjNDAzNS0xMWYzLTQ4N2MtOWQyZS1lZDk2OWRkNjg3OWEvMTc2MzYzNzMyMDc2OF8xNzYzNjM3MjU5MjcwNjAzNjAxXzY4NTcucG5nIiwidHlwZSI6ImF0dGFjaG1lbnQiLCJpYXQiOjE3ODA0NTQ5MjcsImV4cCI6MTc4MDQ1ODUyN30.-uvQJLFQTEJz2M-l0_wQPoSFmIAl8OfD65N9Kfx9m7c " =1408x768")

## 1.2 AiTu(无限画布）工具

> 兔子网页接入了一个"无限画布"「AiTu」，可以选中画布中的任何元素（图片、手画图、文本）调用"最新香蕉模型 nano banana 2 、香蕉模型 2 2k 和 4k "，并可以自动将结果继续嵌入画布 

> 无限画布使用教程链接  [无限画布](https://wiki.tu-zi.com/s/8c61a536-7a59-4410-a5e2-8dab3d041958/doc/aitu-cLmaNiGWX7)

### 1.2.1 无线画布配置香蕉模型


 ![](https://wiki.tu-zi.com/api/files.get?sig=eyJhbGciOiJIUzI1NiIsInR5cCI6IkpXVCJ9.eyJrZXkiOiJ1cGxvYWRzL2I3MTgwNDFlLWUwNjItNDRlMy1iNTljLTlkYzliNjNjODczMi85MmI2NTIyOS0yMjE5LTQyOGMtYTBjNC0xYWRiYjYzZGM2YTYvaW1hZ2UucG5nIiwidHlwZSI6ImF0dGFjaG1lbnQiLCJpYXQiOjE3ODA0NTQ5MjcsImV4cCI6MTc4MDQ1ODUyN30.KeJMFVJaJ4DcxdV2aoJKjskvkxmTAhcMGdJQ1-D2uFM " =1717x581")

### 1.2.2 **选择default 分组** 

 ![](https://wiki.tu-zi.com/api/files.get?sig=eyJhbGciOiJIUzI1NiIsInR5cCI6IkpXVCJ9.eyJrZXkiOiJ1cGxvYWRzL2I3MTgwNDFlLWUwNjItNDRlMy1iNTljLTlkYzliNjNjODczMi8xZjJiZWUzNS1jYTQ5LTQ4ZTctODk3NC1kOGQ1MTJhMDhiZmUvaW1hZ2UucG5nIiwidHlwZSI6ImF0dGFjaG1lbnQiLCJpYXQiOjE3ODA0NTQ5MjcsImV4cCI6MTc4MDQ1ODUyN30.ZRwveYbCfD9L1yAIa2V7rtflXOIwqN-v3oIGCgvqJ_o " =1725x779")


### 1.2.3 **设置香蕉模型** 

gemini-3-pro-image-preview  图像质量 1k

gemini-3-pro-image-preview-hd 图像质量 4k

 ![](https://wiki.tu-zi.com/api/files.get?sig=eyJhbGciOiJIUzI1NiIsInR5cCI6IkpXVCJ9.eyJrZXkiOiJ1cGxvYWRzL2I3MTgwNDFlLWUwNjItNDRlMy1iNTljLTlkYzliNjNjODczMi9jNWJhYmNmNi1lODRlLTQzNGYtODAwNi02MmNkNmU1YzNmMzMvaW1hZ2UucG5nIiwidHlwZSI6ImF0dGFjaG1lbnQiLCJpYXQiOjE3ODA0NTQ5MjcsImV4cCI6MTc4MDQ1ODUyN30.1Q_MCA_RwyDpCjITPWBowVaJ0TD51KdTsmIr3dpkd_M " =1821x992")


**提示词：图一的美女在 沙滩上躺着品尝着图二的饮料，并享受着风景**

* **生图效果**

 ![](https://wiki.tu-zi.com/api/files.get?sig=eyJhbGciOiJIUzI1NiIsInR5cCI6IkpXVCJ9.eyJrZXkiOiJ1cGxvYWRzL2I3MTgwNDFlLWUwNjItNDRlMy1iNTljLTlkYzliNjNjODczMi81NjZiY2JiZS0yZTUzLTRmMjEtODU1OS04ZDkxYzllOTViNmIvaW1hZ2UucG5nIiwidHlwZSI6ImF0dGFjaG1lbnQiLCJpYXQiOjE3ODA0NTQ5MjcsImV4cCI6MTc4MDQ1ODUyN30.BPozSdZaNF7HMcCLXlt00Qt3v5Egzeywyd0bezA1fEY " =2172x1053")   

 ![](https://wiki.tu-zi.com/api/files.get?sig=eyJhbGciOiJIUzI1NiIsInR5cCI6IkpXVCJ9.eyJrZXkiOiJ1cGxvYWRzL2I3MTgwNDFlLWUwNjItNDRlMy1iNTljLTlkYzliNjNjODczMi85NGQ4ZWExOC04MDkyLTRkMWYtOTQxMS05YTUyM2RkYjcyODgvaW1hZ2UucG5nIiwidHlwZSI6ImF0dGFjaG1lbnQiLCJpYXQiOjE3ODA0NTQ5MjcsImV4cCI6MTc4MDQ1ODUyN30.SkMj-VIP5SmtpibA8G1iAQkPs2lt1J0za3hvOuZ7Sd0 " =2298x1133")

## 1.3  cheery 兔子优化版 客户端

### 1.3.1 安装方式

提供了window 版 和 mac 版

> **安装链接**    
>
> <https://wiki.tu-zi.com/s/8c61a536-7a59-4410-a5e2-8dab3d041958/doc/8jtlidlhztlrzdmoyzpnalniygg6ag555uu5lul57un-1NXzffJ7U1#h-%F0%9F%93%A9-%E5%AE%A2%E6%88%B7%E7%AB%AF%E4%B8%8B%E8%BD%BD>
>
> \
> **cheery详细使用教程**
>
> <https://wiki.tu-zi.com/s/8c61a536-7a59-4410-a5e2-8dab3d041958/doc/cherry-studio-ZlASThznAB>


### 1.3.2 使用实例


\
 ![](https://wiki.tu-zi.com/api/files.get?sig=eyJhbGciOiJIUzI1NiIsInR5cCI6IkpXVCJ9.eyJrZXkiOiJ1cGxvYWRzL2I3MTgwNDFlLWUwNjItNDRlMy1iNTljLTlkYzliNjNjODczMi8zZjlkOWI3NC1jMTg0LTQyMTUtYjU4Ny05MzhkYTA5OTE5YjAvaW1hZ2UucG5nIiwidHlwZSI6ImF0dGFjaG1lbnQiLCJpYXQiOjE3ODA0NTQ5MjcsImV4cCI6MTc4MDQ1ODUyN30.8YOnKQdF6uBv2Poeeo57phc42_GVL_k5FimhLjIIEqU " =956x593")


\
**1 进入兔子api站点 获取 key** 


 ![](https://wiki.tu-zi.com/api/files.get?sig=eyJhbGciOiJIUzI1NiIsInR5cCI6IkpXVCJ9.eyJrZXkiOiJ1cGxvYWRzL2I3MTgwNDFlLWUwNjItNDRlMy1iNTljLTlkYzliNjNjODczMi8zMjQ5OGYzZS0yMmFjLTQzZWUtOWZkNC1hZWRiZTE2MTg2ZGUvaW1hZ2UucG5nIiwidHlwZSI6ImF0dGFjaG1lbnQiLCJpYXQiOjE3ODA0NTQ5MjcsImV4cCI6MTc4MDQ1ODUyN30.NpF-mU0PZYMm4ZjdiEyzR8ltCS39Bmrg5OoHCtbFwNo " =1213x159")


\

 ![](https://wiki.tu-zi.com/api/files.get?sig=eyJhbGciOiJIUzI1NiIsInR5cCI6IkpXVCJ9.eyJrZXkiOiJ1cGxvYWRzL2I3MTgwNDFlLWUwNjItNDRlMy1iNTljLTlkYzliNjNjODczMi84MDk4ZGE1YS1jZGFkLTQyMjUtYWU0OS1lNDIxN2Y5ZWUxOGQvaW1hZ2UucG5nIiwidHlwZSI6ImF0dGFjaG1lbnQiLCJpYXQiOjE3ODA0NTQ5MjcsImV4cCI6MTc4MDQ1ODUyN30.nsSvpkHgpCMGqBH1Ij6extmU1P5BZceCu-EnGWbq1tA " =944x371")


\
 ![](https://wiki.tu-zi.com/api/files.get?sig=eyJhbGciOiJIUzI1NiIsInR5cCI6IkpXVCJ9.eyJrZXkiOiJ1cGxvYWRzL2I3MTgwNDFlLWUwNjItNDRlMy1iNTljLTlkYzliNjNjODczMi9jZTMyNmU4MS1iNGM2LTQ2NTAtOGFjYS0xZTBiZGU4MDNhMDYvaW1hZ2UucG5nIiwidHlwZSI6ImF0dGFjaG1lbnQiLCJpYXQiOjE3ODA0NTQ5MjcsImV4cCI6MTc4MDQ1ODUyN30.qxj3xMH2m9IMG9DHNzbl0DQB6NgUYFp1zQDAxpUiGbI " =719x559")


\
**2 搜索 gemini-3-pro-image-preview (nano banana 2) 模型 并添加**

 ![](https://wiki.tu-zi.com/api/files.get?sig=eyJhbGciOiJIUzI1NiIsInR5cCI6IkpXVCJ9.eyJrZXkiOiJ1cGxvYWRzL2I3MTgwNDFlLWUwNjItNDRlMy1iNTljLTlkYzliNjNjODczMi84M2Y3ZDJiMC00YzBlLTQ4MTUtOTM4Ny04NWRkZWMyODdkZjMvaW1hZ2UucG5nIiwidHlwZSI6ImF0dGFjaG1lbnQiLCJpYXQiOjE3ODA0NTQ5MjcsImV4cCI6MTc4MDQ1ODUyN30.OxDvMVoHY2-WE1vgKQpXzrDddKfcZhs9J4czK47D9bM " =943x593")


**3 开启 nano banana 2视觉模式**

 ![](https://wiki.tu-zi.com/api/files.get?sig=eyJhbGciOiJIUzI1NiIsInR5cCI6IkpXVCJ9.eyJrZXkiOiJ1cGxvYWRzL2I3MTgwNDFlLWUwNjItNDRlMy1iNTljLTlkYzliNjNjODczMi9kMzQyYTcwMS1jOGU4LTQzNmQtOTY4OS1jNDQ5MjdiZjk5Y2EvaW1hZ2UucG5nIiwidHlwZSI6ImF0dGFjaG1lbnQiLCJpYXQiOjE3ODA0NTQ5MjcsImV4cCI6MTc4MDQ1ODUyN30.cF0j2tzma7DIkSbeJ9UxvHX8t0a_rZffhHZj5d3NeNg " =750x327")


 ![](https://wiki.tu-zi.com/api/files.get?sig=eyJhbGciOiJIUzI1NiIsInR5cCI6IkpXVCJ9.eyJrZXkiOiJ1cGxvYWRzL2I3MTgwNDFlLWUwNjItNDRlMy1iNTljLTlkYzliNjNjODczMi8zM2UzYzY5Yi0xYTdhLTQyZDItODQ4NC0xMmE2ODdkMzNiZDcvaW1hZ2UucG5nIiwidHlwZSI6ImF0dGFjaG1lbnQiLCJpYXQiOjE3ODA0NTQ5MjcsImV4cCI6MTc4MDQ1ODUyN30.XE5nJYEvuh3ilJP8lJ8ClkM8A70v8SXIpUSkRdA9KYQ " =738x547")

**4 进行有趣的对话**

 ![](https://wiki.tu-zi.com/api/files.get?sig=eyJhbGciOiJIUzI1NiIsInR5cCI6IkpXVCJ9.eyJrZXkiOiJ1cGxvYWRzL2I3MTgwNDFlLWUwNjItNDRlMy1iNTljLTlkYzliNjNjODczMi8wMjdjYTExMS1iMzFjLTQ3NTgtODkxZS0xOTJkNTI5ODE5NGQvaW1hZ2UucG5nIiwidHlwZSI6ImF0dGFjaG1lbnQiLCJpYXQiOjE3ODA0NTQ5MjcsImV4cCI6MTc4MDQ1ODUyN30.NuiB_oUzXXoKyJiWHayMBupJsjcTvAiQ-oWyy28oTsk " =1291x912")


# 二、API接口调用

> **banana-2 、2k 、4k 调用接口文档：**
>
> **chat 格式：<https://tuzi-api.apifox.cn/343646954e0>**
>
> **generations 格式 :  <https://tuzi-api.apifox.cn/343646956e0>**
>
> **images 格式: <https://tuzi-api.apifox.cn/343646957e0>**
>
> **谷歌 格式 ：<https://tuzi-api.apifox.cn/360926406e0>**


## 同步接口

### 2.1 生成图像 （chat 必须流式请求）

示例1 简单版本

```python

"""
Gemini API 图像处理工具 v1.3
================================
功能描述：
- 支持向 Gemini AI 模型发送单张或多张图片进行分析和生成
- 自动处理API返回的混合内容（文字、base64图片、URL图片）
- 智能重试机制处理API配额超限和超时错误
- 使用流式响应确保大型图片数据的完整接收
- 将所有输出内容整理保存到带时间戳的目录中

作者：兔子CC
更新日期：2025-08-28
"""

import os
import base64
import re
import requests
import time
import json
from datetime import datetime
from openai import OpenAI

# ====================================
# 用户配置变量 - 请根据需要修改以下设置
# ====================================

# API配置
API_KEY = "sk-**"  # 请替换为你的实际API密钥
BASE_URL = "https://api.tu-zi.com/v1"  # 请替换为你的实际基础URL
MODEL_NAME = "gemini-3-pro-image-preview"  # 使用的模型名称

# 图片路径（可以是单个路径或路径列表）
IMAGE_PATHS = [
    r"C:\Users\20wj2\Downloads\下载2.png",  # 第一张图片
    r"C:\Users\20wj2\Downloads\sz.png",  # 可以添加更多图片
    # r"C:\Users\20wj2\Downloads\image3.png",
]
# 为了向后兼容，如果只有一张图片也可以直接使用字符串
# IMAGE_PATHS = r"C:\Users\20wj2\Downloads\下载2.png"

# 提示词设置
PROMPT_TEXT = "依据上传图片，生成新的图片。图片1中的女士抱着图片2中人物形象的公仔，在睡觉。"  # 自定义提示词

# 重试设置
MAX_RETRIES = 10  # 最大重试次数
RETRY_DELAY = 0  # 重试延迟时间（秒），0表示立即重试

# API调用超时设置
API_TIMEOUT = 120  # API调用超时时间（秒），建议120秒以等待图片生成
USE_STREAM = True  # 必须使用流式响应才能获取完整的图片数据！

# ====================================
# 以下为功能代码，一般情况下无需修改
# ====================================

def prepare_image_data(image_path):
    """准备图片数据，转换为base64格式"""
    try:
        with open(image_path, "rb") as img_file:
            encoded_data = base64.b64encode(img_file.read()).decode("utf-8")
            return "data:image/png;base64," + encoded_data
    except Exception as e:
        print(f"准备图片数据时出错: {image_path} - {e}")
        raise

def create_output_directory():
    """创建输出目录"""
    timestamp = datetime.now().strftime("%Y%m%d_%H%M%S")
    output_dir = f"output_{timestamp}"
    os.makedirs(output_dir, exist_ok=True)
    return output_dir

def save_base64_image(base64_data, output_dir, image_index):
    """保存base64图片到本地"""
    try:
        # 移除data:image/png;base64,前缀（如果存在）
        if base64_data.startswith('data:image/'):
            base64_data = base64_data.split(',', 1)[1]
        
        # 解码base64数据
        image_data = base64.b64decode(base64_data)
        
        # 保存图片
        image_filename = f"image_{image_index}.png"
        image_path = os.path.join(output_dir, image_filename)
        
        with open(image_path, "wb") as img_file:
            img_file.write(image_data)
        
        print(f"已保存base64图片: {image_path}")
        return image_path
    except Exception as e:
        print(f"保存base64图片时出错: {e}")
        return None

def download_image_from_url(url, output_dir, image_index):
    """从URL下载图片到本地"""
    try:
        response = requests.get(url, stream=True)
        response.raise_for_status()
        
        # 获取文件扩展名
        content_type = response.headers.get('content-type', '')
        if 'png' in content_type.lower():
            ext = 'png'
        elif 'jpg' in content_type.lower() or 'jpeg' in content_type.lower():
            ext = 'jpg'
        elif 'gif' in content_type.lower():
            ext = 'gif'
        else:
            ext = 'png'  # 默认扩展名
        
        # 保存图片
        image_filename = f"image_url_{image_index}.{ext}"
        image_path = os.path.join(output_dir, image_filename)
        
        with open(image_path, "wb") as img_file:
            for chunk in response.iter_content(chunk_size=8192):
                img_file.write(chunk)
        
        print(f"已下载URL图片: {image_path}")
        return image_path
    except Exception as e:
        print(f"下载URL图片时出错: {e}")
        return None

def save_mixed_content(content, output_dir):
    """保存混合内容（文字、base64图片、URL图片）"""
    try:
        # 查找base64图片
        base64_pattern = r'data:image/[^;]+;base64,([A-Za-z0-9+/=]+)'
        base64_matches = re.finditer(base64_pattern, content)
        
        # 查找URL链接
        url_pattern = r'https?://[^\s<>"]+\.(png|jpg|jpeg|gif)'
        url_matches = re.finditer(url_pattern, content, re.IGNORECASE)
        
        # 保存文字内容到文件
        text_content = content
        image_index = 1
        
        # 处理base64图片
        for match in base64_matches:
            full_match = match.group(0)
            base64_data = match.group(1)
            
            # 保存base64图片
            saved_path = save_base64_image(base64_data, output_dir, image_index)
            if saved_path:
                # 在文本中替换base64数据为文件路径
                text_content = text_content.replace(full_match, f"[保存的图片: {saved_path}]")
                image_index += 1
        
        # 处理URL图片
        for match in url_matches:
            url = match.group(0)
            
            # 下载URL图片
            saved_path = download_image_from_url(url, output_dir, image_index)
            if saved_path:
                # 在文本中替换URL为文件路径
                text_content = text_content.replace(url, f"[下载的图片: {saved_path}]")
                image_index += 1
        
        # 保存处理后的文字内容
        text_filename = os.path.join(output_dir, "content.txt")
        with open(text_filename, "w", encoding="utf-8") as text_file:
            text_file.write(text_content)
        
        print(f"已保存文字内容: {text_filename}")
        
        # 同时保存原始内容
        original_filename = os.path.join(output_dir, "original_content.txt")
        with open(original_filename, "w", encoding="utf-8") as original_file:
            original_file.write(content)
        
        print(f"已保存原始内容: {original_filename}")
        
    except Exception as e:
        print(f"保存混合内容时出错: {e}")

def is_quota_exceeded_error(error_message):
    """检查是否为配额超出错误"""
    quota_keywords = [
        "exceeded your current quota",
        "quota exceeded",
        "billing details",
        "plan and billing"
    ]
    error_str = str(error_message).lower()
    return any(keyword in error_str for keyword in quota_keywords)

def call_api_raw(api_key, base_url, model, messages, timeout=API_TIMEOUT, use_stream=False, output_dir=None):
    """使用原始HTTP请求调用API，获取完整响应"""
    headers = {
        "Authorization": f"Bearer {api_key}",
        "Content-Type": "application/json"
    }
    
    data = {
        "model": model,
        "messages": messages,
        "stream": use_stream
    }
    
    url = f"{base_url}/chat/completions"
    
    try:
        print(f"发送原始HTTP请求到: {url}")
        if use_stream:
            print("使用流式响应模式...")
        
        response = requests.post(url, headers=headers, json=data, timeout=timeout, stream=use_stream)
        response.raise_for_status()
        
        if use_stream:
            # 处理流式响应
            full_content = ""
            all_chunks = []
            
            for line in response.iter_lines():
                if line:
                    line_str = line.decode('utf-8')
                    if line_str.startswith('data: '):
                        data_str = line_str[6:]
                        if data_str != '[DONE]':
                            try:
                                chunk = json.loads(data_str)
                                all_chunks.append(chunk)
                                if 'choices' in chunk and len(chunk['choices']) > 0:
                                    delta = chunk['choices'][0].get('delta', {})
                                    if 'content' in delta:
                                        full_content += delta['content']
                            except json.JSONDecodeError:
                                pass
            
            # 保存所有流式数据（调试用）
            if output_dir:
                debug_path = os.path.join(output_dir, "stream_chunks.json")
                with open(debug_path, "w", encoding="utf-8") as f:
                    json.dump(all_chunks, f, ensure_ascii=False, indent=2)
            
            print(f"流式响应: 接收到 {len(all_chunks)} 个数据块")
            if len(full_content) > 1000:
                print(f"获取到完整数据: {len(full_content)} 字符（包含图片）")
            else:
                print(f"获取到文本内容: {len(full_content)} 字符")
            
            # 构造标准响应格式
            json_response = {
                "choices": [{
                    "message": {
                        "role": "assistant",
                        "content": full_content
                    }
                }],
                "stream_chunks": all_chunks
            }
        else:
            # 获取完整的JSON响应
            json_response = response.json()
        
        # 保存原始JSON响应用于调试
        if output_dir:
            debug_path = os.path.join(output_dir, "raw_api_response.json")
            with open(debug_path, "w", encoding="utf-8") as f:
                json.dump(json_response, f, ensure_ascii=False, indent=2)
            print(f"原始API响应已保存到: {debug_path}")
        
        return json_response
    except requests.exceptions.RequestException as e:
        print(f"HTTP请求失败: {e}")
        raise

def call_openai_with_retry(client, model, messages, max_retries=MAX_RETRIES, retry_delay=RETRY_DELAY, timeout=API_TIMEOUT):
    """带重试功能的OpenAI API调用"""
    for attempt in range(max_retries):
        try:
            print(f"第 {attempt + 1} 次尝试调用API...")
            if timeout > 60:
                print(f"设置超时时间: {timeout}秒 (等待图片生成)")
            
            completion = client.chat.completions.create(
                model=model,
                messages=messages,
                timeout=timeout
            )
            
            print("API调用成功！")
            return completion
            
        except Exception as e:
            error_message = str(e)
            print(f"API调用失败: {error_message}")
            
            # 检查是否为配额超出错误或超时错误
            if is_quota_exceeded_error(error_message):
                if attempt  0:
                        print(f"检测到配额超出错误，将在 {retry_delay} 秒后进行第 {attempt + 2} 次重试...")
                        time.sleep(retry_delay)
                    else:
                        print(f"检测到配额超出错误，立即进行第 {attempt + 2} 次重试...")
                    continue
                else:
                    print("已达到最大重试次数，仍然配额超出，请检查账户余额和计费设置。")
                    raise
            elif "timeout" in error_message.lower() or "timed out" in error_message.lower():
                if attempt  500 else response_content)

# 保存混合内容到本地
save_mixed_content(response_content, output_directory)
print(f"\n所有内容已保存到目录: {output_directory}")
```

### 2.2 文本生图 - generate端点（default分组、gemini-mix分组）

示例1 简单版本

```python
from openai import OpenAI
import base64
import requests
import os

# 获取环境变量，如果未设置则使用默认值
api_key = os.environ.get("TUZI_API_KEY", "sk-***")
api_base = os.environ.get("TUZI_API_BASE", "https://api.tu-zi.com/v1")

client = OpenAI(
    base_url=api_base,
    api_key=api_key
)

result = client.images.generate(
    model="gemini-3-pro-image-preview",
    prompt="生成一副清明上河图"
)

print(result)
print(result.data)

image_base64 = result.data[0].b64_json
image_url = result.data[0].url

if image_base64:
    image_bytes = base64.b64decode(image_base64)
    with open("blackhole1.png", "wb") as f:
        f.write(image_bytes)
    print("图片已通过base64保存为 blackhole.png")
elif image_url:
    response = requests.get(image_url)
    response.raise_for_status()
    with open("blackhole.png", "wb") as f:
        f.write(response.content)
    print(f"图片已通过url下载并保存为 blackhole.png，url: {image_url}")
else:
    raise ValueError("API 没有返回图片的 base64 数据或图片链接！")
```

### 2.3 修改现有图像 - edit端点（default分组）

示例1 简单版本

```python
from openai import OpenAI
import base64
import requests
import os

# 从环境变量获取API密钥和基础URL
# 可以通过以下方式设置环境变量:
# Windows (CMD):
#   set TUZI_API_KEY=sk-your-api-key
#   set TUZI_API_BASE=https://api.tu-zi.com/v1
# Windows (PowerShell):
#   $env:TUZI_API_KEY="sk-your-api-key"
#   $env:TUZI_API_BASE="https://api.tu-zi.com/v1"
# Linux/macOS:
#   export TUZI_API_KEY=sk-your-api-key
#   export TUZI_API_BASE=https://api.tu-zi.com/v1

# 获取环境变量，如果未设置则使用默认值
api_key = os.environ.get("TUZI_API_KEY", "sk-***")
api_base = os.environ.get("TUZI_API_BASE", "https://api.tu-zi.com/v1")

client = OpenAI(
    base_url=api_base,
    api_key=api_key
)

result = client.images.edit(
    model="gemini-3-pro-image-preview",
    image=open("C:/Users/north/Pictures/Saved Pictures/tuzisleep.jpg", "rb"),
    # mask=open("C:/Users/north/Pictures/Saved Pictures/bff77acc-daee-4c96-b86c-1ba8049ec788.jpg", "rb"),
    prompt="将图二的人物以近景的的形式输出图片",
    response_format="url"  # 返回格式 例如  b64_json
)

print(result)
print(result.data)

image_base64 = result.data[0].b64_json
image_url = result.data[0].url

if image_base64:
    image_bytes = base64.b64decode(image_base64)
    with open("gift-basket.png", "wb") as f:
        f.write(image_bytes)
    print("图片已通过base64保存为 gift-basket.png")
elif image_url:
    response = requests.get(image_url)
    response.raise_for_status()
    with open("gift-basket.png", "wb") as f:
        f.write(response.content)
    print(f"图片已通过url下载并保存为 gift-basket.png，url: {image_url}")
else:
    raise ValueError("API 没有返回图片的 base64 数据或图片链接！")
```

### 2.4 谷歌官方格式 （gemini原价分组）

```python
import requests
import base64
import os
import mimetypes

# 配置参数
BASE_URL = "https://api.tu-zi.com"  # 兔子域名
MODEL = "gemini-3-pro-image-preview" # 模型
API_KEY = "sk-***"  # tuzi API Key
IMAGE_PATH = "C:/Users/north/Pictures/Saved Pictures/tuzisleep.jpg"   # 上传图片
API_URL = f"{BASE_URL}/v1beta/models/{MODEL}:generateContent"

# 读取并编码图片
try:
    with open(IMAGE_PATH, "rb") as f:
        image_base64 = base64.b64encode(f.read()).decode('utf-8')
    # 自动检测MIME类型
    mime_type, _ = mimetypes.guess_type(IMAGE_PATH)
    if not mime_type or not mime_type.startswith('image/'):
        mime_type = "image/png"  # 默认PNG
except FileNotFoundError:
    print(f"图片文件不存在: {IMAGE_PATH}")
    exit(1)

# 构建请求
headers = {
    "Authorization": f"Bearer {API_KEY}",
    "Content-Type": "application/json"
}

payload = {
    "contents": [{
        "parts": [
            {"inline_data": {"mime_type": mime_type, "data": image_base64}},
            {"text": "画一个跳拉丁舞的女生."}   # 提示词
        ]
    }],
    "generationConfig": {"maxOutputTokens": 7680, "temperature": 0.1}
}

# 发送请求
try:
    response = requests.post(API_URL, headers=headers, json=payload)
    
    if response.status_code == 200:
        result = response.json()
        candidate = result["candidates"][0]
        
        for i, part in enumerate(candidate["content"]["parts"]):
            if "text" in part:
                print("生成的文本:", part["text"])
            elif "inlineData" in part:
                # 保存生成的图片
                image_data = base64.b64decode(part["inlineData"]["data"])
                response_mime = part["inlineData"]["mimeType"]
                ext = "png" if "png" in response_mime else "jpg"
                filename = f"generated_image_{i + 1}.{ext}"
                
                with open(filename, "wb") as f:
                    f.write(image_data)
                    
                print(f"生成图片已保存: {filename} ({response_mime})")
        
        print(f"Token消耗: {result['usageMetadata']['totalTokenCount']}")
    else:
        print(f"请求失败: {response.status_code}")
        print(response.text)
        
except requests.RequestException as e:
    print(f"网络请求错误: {e}")
```


## 异步接口


**📌 简介**

这是一个**异步图片生成API**，你可以通过发送一个请求来创建一个生图任务，然后轮询查询结果。

> 什么是异步？简单说就是：你提交任务后立即得到一个"任务ID"，不用等待生成完成，可以稍后查询结果。


---

**快速开始**

### 第一步：基础信息

* **API 地址**：`https://api.tu-zi.com`
* **请求方式**：`POST`
* **请求路径**：`/v1/videos`
* **需要认证**：是（Bearer Token）

### 第二步：最简单的请求示例

```bash
curl -X POST https://api.tu-zi.com/v1/videos \
  -H "Authorization: Bearer 你的TOKEN" \
  -F "model=gemini-3-pro-image-preview-async" \
  -F "prompt=一只可爱的小猫"
```

**返回示例**：

```json
{
  "id": "472886112156536836",
  "object": "video",
  "model": "gemini-3-pro-image-preview-async",
  "status": "queued",
  "progress": 0,
  "created_at": 1769600979
}
```

✅ 成功！现在你已经创建了一个生图任务，拿到了 `id`。

### 第三步: 查询图片接口

```javascript
curl -X GET 'https://api.tu-zi.com/v1/videos/472886112156536836' \
--header 'Authorization: Bearer <token>'
```

**返回示例**：

```javascript
{
    "created_at": 1769600979578,
    "id": "472886112156536836",
    "object": "video",
    "progress": 100,
    "status": "completed",
    "video_url": "https://apioss3.sydney-ai.com/img/35/t9il_91djAoxYvqytvWzR9JNk7wye8LwY7BNR7op_Aom_8owjpMm1xku10Qu1xhu1awNeDXL_4oue7nltJoxtvWlDsYzRvFN1a_sfakm1a3mXxhlX03mX0Mqf5llXp3A1xQlf0FrXx1p10wTXxLO1a_sfakm1a3mX4VK_v_=/1769601006844004289-470221485763309569_1769601006.jpg"
}
```


---


 **参数说明**

**必填参数**

| 参数  | 说明  | 可选值 |
|-----|-----|-----|
| **model** | 选择模型/分辨率 | 见下表 |
| **prompt** | 你的图片描述 | 任意文本（中英文都可以） |

**模型选择（model 参数）**

| 模型  | 分辨率 | 说明  |
|-----|-----|-----|
| `gemini-3-pro-image-preview-async` | 1K  | 基础版，生成速度快 |
| `gemini-3-pro-image-preview-2k-async` | 2K  | 标准版，质量更好 |
| `gemini-3-pro-image-preview-4k-async` | 4K  | 高质量版，细节最丰富 |

**建议**：

* 首次测试：用 1K 版本
* 需要高质量：用 4K 版本

**可选参数**

| 参数  | 说明  | 可选值 | 默认值 |
|-----|-----|-----|-----|
| **size** | 图片宽高比例 | 见下表 | `16:9` |
| **input_reference** | 参考图片 | 图片文件或URL | 无   |

**尺寸选择（size 参数）**

```
1:1    正方形
2:3    竖式(1080x1620)
3:2    横式
3:4    竖式
4:3    横式
4:5    竖式
5:4    横式
9:16   手机竖屏
16:9   宽屏/横屏
21:9   超宽屏
```


---

 **常见用法示例**

**示例 1️⃣：生成手机壁纸**

```bash
curl -X POST https://api.tu-zi.com/v1/videos \
  -H "Authorization: Bearer YOUR_TOKEN" \
  -F "model=gemini-3-pro-image-preview-4k-async" \
  -F "prompt=梦幻紫色星空，流星划过" \
  -F "size=9:16"
```

**示例 2️⃣：基于参考图生成**

```bash
curl -X POST https://api.tu-zi.com/v1/videos \
  -H "Authorization: Bearer YOUR_TOKEN" \
  -F "model=gemini-3-pro-image-preview-2k-async" \
  -F "prompt=类似这个风格的科幻城市夜景" \
  -F "input_reference=@/path/to/reference.jpg" \
  -F "size=16:9"
```

**示例 3️⃣：多参考图片**

```bash
curl -X POST https://api.tu-zi.com/v1/videos \
  -H "Authorization: Bearer YOUR_TOKEN" \
  -F "model=gemini-3-pro-image-preview-4k-async" \
  -F "prompt=融合这两张图片的风格" \
  -F "input_reference=@image1.jpg" \
  -F "input_reference=@image2.jpg"
```


---

 **Python 示例**

```python
import requests

def create_image_task(prompt, model="gemini-3-pro-image-preview-async",
                     size="16:9", token="YOUR_TOKEN"):
    """创建图片生成任务"""

    url = "https://api.tu-zi.com/v1/videos"

    headers = {
        "Authorization": f"Bearer {token}"
    }

    files = {
        "model": (None, model),
        "prompt": (None, prompt),
        "size": (None, size),
    }

    response = requests.post(url, headers=headers, files=files)

    if response.status_code == 200:
        task_info = response.json()
        print(f"✅ 任务创建成功")
        print(f"任务ID: {task_info['id']}")
        print(f"状态: {task_info['status']}")
        return task_info['id']
    else:
        print(f"❌ 创建失败: {response.text}")
        return None

# 使用示例
task_id = create_image_task("一个宇航员在月球上漫步")
```


---

 **响应说明**


**返回字段**

| 字段  | 说明  | 例子  |
|-----|-----|-----|
| `id` | **任务ID**（最重要！用来查询结果） | `472886112156536836` |
| `object` | 对象类型 | `video` |
| `model` | 使用的模型 | `gemini-3-pro-image-preview-async` |
| `status` | 当前状态 | `queued`（排队中） |
| `progress` | 进度百分比 | `0`（刚开始） |
| `created_at` | 创建时间戳 | `1769600979` |

**状态含义**

| 状态  | 含义  |
|-----|-----|
| `queued` | 排队中，等待处理 |
| `processing` | 正在生成 |
| `completed` | ✅ 生成完成 |
| `failed` | ❌ 生成失败 |


---

 **查询结果（下一步）**

得到 `id` 后，你需要定期查询任务状态来获取结果。通常需要调用另一个"查询" API：

```bash
curl -X GET https://api.tu-zi.com/v1/videos/{task_id} \
  -H "Authorization: Bearer YOUR_TOKEN"
```

**建议查询间隔**：

* 1K 模型：每 10 秒查询一次
* 2K 模型：每 15 秒查询一次
* 4K 模型：每 20 秒查询一次


---

##  常见问题

### Q1：Prompt 怎么写才能生成好图？

**A：**

* 要具体、有细节："一只穿着花裙子的小兔子在草地上" 比 "小兔子" 好
* 可以指定风格："油画风格"、"赛博朋克"、"日漫"
* 可以指定质量："4K 高清"、"精美的"

### Q2：生成需要多久？

**A：**

* 1K 版本：通常 2-5 分钟
* 2K 版本：通常 2-5 分钟
* 4K 版本：通常 2-5 分钟

### Q3：参考图片怎么上传？

**A：** 支持两种方式：

* **本地文件**：`-F "input_reference=@/path/to/image.jpg"`
* **URL链接**：`-F "input_reference=https://example.com/image.jpg"`

### Q4：可以上传多个参考图吗？

**A：** 可以，多次使用 `-F "input_reference=..."` 即可

### Q5：错误了怎么办？

**A：** 检查这些点：

* ✅ Bearer Token 是否正确
* ✅ 模型名称是否拼写正确
* ✅ Prompt 不能为空
* ✅ Size 参数是否是有效的比例


---

##  工作流示意图

```
1. 发送请求 (POST /v1/videos)
       ↓
2. 得到任务ID
       ↓
3. 定期查询 (GET /v1/videos/{task_id})
       ↓
4. 状态 = completed？
       ├─ 是 → 获取结果图片 ✅
       └─ 否 → 继续查询...
```


---

##  更多信息

* **API 文档完整版**：<https://tuzi-api.apifox.cn/412175236e0>
* **获取 Token**：需要先注册账户
* **速率限制**：根据账户等级有不同限制


---

**祝你生图愉快！** 🎨