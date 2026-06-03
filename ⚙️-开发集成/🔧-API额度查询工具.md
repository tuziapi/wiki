# 🔧 API额度查询工具

这是一个简单的Python脚本，用于查询兔子API（api.tu-zi.com）账户令牌信息，包括总额度、已使用额度和剩余额度。

## 功能介绍

该脚本通过调用兔子API的账单接口，获取以下信息：

* 账户总额度（美元）
* 近30天已使用额度（美元）
* 剩余可用额度（美元）

## 代码说明

```python
import requests
import datetime

def get_openai_balance(api_key):
    headers = {
        "Authorization": f"Bearer {api_key}",
        "Content-Type": "application/json"
    }

    # 获取总额度
    subscription_url = "https://api.tu-zi.com/v1/dashboard/billing/subscription"
    subscription_response = requests.get(subscription_url, headers=headers)
    if subscription_response.status_code != 200:
        print("获取总额度失败:", subscription_response.text)
        return
    total_limit = subscription_response.json().get("hard_limit_usd", 0)

    # 获取已使用额度
    end_date = datetime.datetime.now().date()
    start_date = end_date - datetime.timedelta(days=30)  # 查询近30天的使用情况
    usage_url = f"https://api.tu-zi.com/v1/dashboard/billing/usage?start_date={start_date}&end_date={end_date}"
    usage_response = requests.get(usage_url, headers=headers)
    if usage_response.status_code != 200:
        print("获取已使用额度失败:", usage_response.text)
        return
    total_usage = usage_response.json().get("total_usage", 0) / 100  # 转换为美元

    remaining_balance = total_limit - total_usage

    print(f"总额度: ${total_limit:.2f}")
    print(f"已使用: ${total_usage:.2f}")
    print(f"剩余额度: ${remaining_balance:.2f}")

# 使用您的 API Key 调用函数
api_key = "YOUR_API_KEY_HERE"
get_openai_balance(api_key)
```

## 使用方法

### 步骤 1: 准备环境

确保您的Python环境已安装requests库。如果没有，可以使用以下命令安装：

```bash
pip install requests
```

### 步骤 2: 替换API密钥

将代码中的 `YOUR_API_KEY_HERE` 替换为您自己的兔子API密钥。

> **⚠️ 注意：** 请勿将含有真实API密钥的代码分享给他人，以免造成API密钥泄露！

### 步骤 3: 运行脚本

保存文件为 `get_tuziapi_balance.py`，然后通过命令行运行：

```bash
python get_tuziapi_balance.py
```

## 执行结果

脚本运行后，将显示以下信息：

```
总额度: $xx.xx
已使用: $xx.xx
剩余额度: $xx.xx
```

> **📝 说明：**
>
> * 此脚本通过调用兔子API的账单接口获取账户余额信息
> * 已使用额度统计的是近30天的使用情况
> * 所有金额均以美元为单位

## 常见问题

### Q: 为什么会显示"获取总额度失败"或"获取已使用额度失败"？

A: 可能是以下原因之一：

* API密钥不正确或已过期
* 网络连接问题
* 兔子API服务暂时不可用


---

*最后更新时间：2025年05月21日*