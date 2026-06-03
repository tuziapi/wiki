# ⚙️OpenClaw (小龙虾）添加 Codex Team 账号配置

本文档将指导你如何在 OpenClaw 中配置 OpenAI Codex Team 账号，让你可以使用 Codex 模型。


---

## 📋 前提条件

在开始之前，请确保你已具备：

* ✅ 已安装 OpenClaw 并能正常运行
* ✅ 拥有 OpenAI Team 账号（有 Codex 访问权限）
  * 兔子站30元 Team 账户的购买地址：@[https://store.tu-zi.com/item/57](mention://e591e543-512f-48b7-9f59-d6a0da1be8ea/url/cc19e662-f022-4fcf-8cbe-b167521501a5) 
* ✅ 知道你的 Team 账号邮箱和密码


---

## 🚀 配置步骤

### 第一步：登录 OpenAI Codex 账号

 ![](https://wiki.tu-zi.com/api/files.get?sig=eyJhbGciOiJIUzI1NiIsInR5cCI6IkpXVCJ9.eyJrZXkiOiJ1cGxvYWRzL2FjNjBlNmRhLTdjYTQtNDdjMS04ZTQxLTAxMDUyMDAwNzM3NS9hYTRmNjYwZC0wZDk4LTRhYTYtYmFjNC00N2I0NWZjMjU1MmYvMi0yNC0wMS5naWYiLCJ0eXBlIjoiYXR0YWNobWVudCIsImlhdCI6MTc4MDQ1NDg1NCwiZXhwIjoxNzgwNDU4NDU0fQ.MAQsgiRDApjgAyAH-4tUpqs5hTopmejP0WDuLk7hEQs " =685x358")

打开终端，输入以下命令：

```bash
openclaw configure
```

你会看到一个交互式菜单，按方向键选择 **Credentials（凭证配置）**，然后按回车。

接着选择 **OpenAI Codex**，系统会自动打开浏览器让你登录。

> 💡 **提示**：使用你的 OpenAI Team 账号邮箱和密码登录。

登录成功后，终端会显示 **model picker**，回车跳过后选择 **continue** 结束配置。


---

### 第二步：修改全局配置文件

#### 打开配置文件

 ![](https://wiki.tu-zi.com/api/files.get?sig=eyJhbGciOiJIUzI1NiIsInR5cCI6IkpXVCJ9.eyJrZXkiOiJ1cGxvYWRzL2FjNjBlNmRhLTdjYTQtNDdjMS04ZTQxLTAxMDUyMDAwNzM3NS9lNDdlMmFiYS1hNzBmLTQ4MDQtYjE2YS1kM2RmODJiMTMzMmQvMi0yNC0wMi5naWYiLCJ0eXBlIjoiYXR0YWNobWVudCIsImlhdCI6MTc4MDQ1NDg1NCwiZXhwIjoxNzgwNDU4NDU0fQ.ph4Q2Eo2ksduA3HVWN9pb-ZX2Eeyzw8lCWaGyrMginI " =556x313")


在终端输入以下命令，用 macOS 自带的「文本编辑」应用打开配置文件：

```bash
open -a TextEdit ~/.openclaw/openclaw.json
```

> 💡 **其他编辑器选项**：
>
> * 用 VS Code 打开：`code ~/.openclaw/openclaw.json`
> * 用终端编辑器：`nano ~/.openclaw/openclaw.json`

#### 2.1 添加 auth profile

 ![](https://wiki.tu-zi.com/api/files.get?sig=eyJhbGciOiJIUzI1NiIsInR5cCI6IkpXVCJ9.eyJrZXkiOiJ1cGxvYWRzL2FjNjBlNmRhLTdjYTQtNDdjMS04ZTQxLTAxMDUyMDAwNzM3NS8xY2Q4MWQyZi02ZDNkLTQ2NTgtOTQ2OS02MDgyYWY4NzA0NWQvMi0yNC0wMy5naWYiLCJ0eXBlIjoiYXR0YWNobWVudCIsImlhdCI6MTc4MDQ1NDg1NCwiZXhwIjoxNzgwNDU4NDU0fQ.7UYWuYeE-FTdx29O4MmdTR7HVWEXA3jYWw77Yrvc_hI " =385x301")

找到 `"auth": { "profiles": {` 部分，添加 Codex 配置：

```json
"auth": {
  "profiles": {
    --- 添加 Codex 配置 ---
    "openai-codex:default": {
      "provider": "openai-codex",
      "mode": "oauth"
    },
    --- 添加 Codex 配置 ---
    "你原有的配置...": {}
  }
}
```

#### 2.2 添加 models provider

 ![](https://wiki.tu-zi.com/api/files.get?sig=eyJhbGciOiJIUzI1NiIsInR5cCI6IkpXVCJ9.eyJrZXkiOiJ1cGxvYWRzL2FjNjBlNmRhLTdjYTQtNDdjMS04ZTQxLTAxMDUyMDAwNzM3NS8xNWU5N2RkOS1iODc5LTQyYmMtYThjZi01OThlN2FhNTBhNTQvMi0yNC0wNC5naWYiLCJ0eXBlIjoiYXR0YWNobWVudCIsImlhdCI6MTc4MDQ1NDg1NCwiZXhwIjoxNzgwNDU4NDU0fQ.IS1aiiNYRfq4XJSggjgqLAbJlbq0v6F0twPMpP7YKjQ " =428x342")

找到 `"models": { "providers": {` 部分，添加 Codex 模型配置：

> 💡 **提示**：此处可以自行添加不同codex模型，以下配置包含 codex-mini-latest、gpt-5.3-codex、gpt-5.2-codex 三种模型。

```json
"models": {
  "providers": {
    --- 添加 Codex 配置(此处可选模型) ---
    "openai-codex": {
      "baseUrl": "https://api.openai.com/v1",
      "api": "openai-responses",
      "models": [
          {
           "id": "codex-mini-latest",
           "name": "Codex Mini",
           "reasoning": false,
           "input": ["text"],
           "cost": {"input": 0, "output": 0, "cacheRead": 0, "cacheWrite": 0},
           "contextWindow": 192000,
           "maxTokens": 100000
          },
          {
            "id": "gpt-5.3-codex",
            "name": "GPT-5.3 Codex",
            "reasoning": false,
            "input": [
              "text"
            ],
            "cost": {
              "input": 0,
              "output": 0,
              "cacheRead": 0,
              "cacheWrite": 0
            },
            "contextWindow": 200000,
            "maxTokens": 16384
          },
          {
            "id": "gpt-5.2-codex",
            "name": "GPT-5.2 Codex",
            "reasoning": false,
            "input": [
              "text"
            ],
            "cost": {
              "input": 0,
              "output": 0,
              "cacheRead": 0,
              "cacheWrite": 0
            },
            "contextWindow": 200000,
            "maxTokens": 16384
          }
      ]
    },
    --- 添加 Codex 配置(此处可选模型) ---
    "你原有的配置...": {}
  }
}
```

#### 2.3 修改默认模型（可选）

 ![](https://wiki.tu-zi.com/api/files.get?sig=eyJhbGciOiJIUzI1NiIsInR5cCI6IkpXVCJ9.eyJrZXkiOiJ1cGxvYWRzL2FjNjBlNmRhLTdjYTQtNDdjMS04ZTQxLTAxMDUyMDAwNzM3NS82YTEzMmZiMy1mOGZiLTRkOTItYjkzMy1mODc1YWZlZmQ4YTMvMi0yNC0wNS5naWYiLCJ0eXBlIjoiYXR0YWNobWVudCIsImlhdCI6MTc4MDQ1NDg1NCwiZXhwIjoxNzgwNDU4NDU0fQ.1zR-hiKkUbxlruGHU3UhxwiMJy35oftMYVoRPIbfNmA " =428x342")

如果你想让 Codex 成为默认模型，找到 `"agents": { "defaults": {` 部分，修改：

```json
"agents": {
  "defaults": {
    "model": {
      "primary": "openai-codex/gpt-5.3-codex",
      "fallbacks": ["你的备用模型"]
    },
    "models": {
      "openai-codex/codex-mini-latest": {},
      "openai-codex/gpt-5.2-codex":{},
      "openai-codex/gpt-5.3-codex":{},
      "你原有的模型...": {}
    }
  }
}
```

⚠️修改完成后，按 `Command + S` 保存文件，然后关闭编辑器。


---

### 第三步：检查并切换模型 

#### 3.1 重启 Gateway

```bash
openclaw gateway restart
```

#### 3.2 检查 Codex 是否配置成功

```bash
openclaw models
```

查看输出中是否有 `codex` 相关的信息。

#### 3.3 让 OpenClaw 自动切换模型

如果 Codex 配置成功，你可以直接在聊天中发送以下命令，让 OpenClaw 自动完成模型切换：

**直接发消息给 OpenClaw**

在 Telegram 或其他已连接的渠道发送：

```
请帮我把模型切换到 openai-codex/gpt-5.3-codex
```

OpenClaw 会自动帮你修改 Agent 的配置文件并完成切换。

#### 3.4 验证切换结果

再次检查状态：

```bash
openclaw status
```

检查 `Sessions` 部分，应该显示：

```
Sessions │ xx active · default gpt-5.3-codex (192k ctx) · x stores
```

如果看到 `gpt-5.3-codex`，说明配置成功！🎉


---

## ✅ 测试

在 Telegram 或其他已连接的渠道发送一条消息，看看是否能正常收到 Codex 的回复。


---

## ❓ 常见问题

### Q1: 登录时浏览器没有自动打开？

手动打开浏览器，访问终端显示的 URL 进行登录。

### Q2: 在浏览器登陆后未自动跳转？

将登陆成功后的重定向地址粘贴到终端里：

 ![](https://wiki.tu-zi.com/api/files.get?sig=eyJhbGciOiJIUzI1NiIsInR5cCI6IkpXVCJ9.eyJrZXkiOiJ1cGxvYWRzL2FjNjBlNmRhLTdjYTQtNDdjMS04ZTQxLTAxMDUyMDAwNzM3NS82ZWM4Njk4YS1hOTNhLTQzN2QtYjE4Zi02ZmEzYzkyOWU0MjcvaW1hZ2UucG5nIiwidHlwZSI6ImF0dGFjaG1lbnQiLCJpYXQiOjE3ODA0NTQ4NTQsImV4cCI6MTc4MDQ1ODQ1NH0.wghE_hJEwYQt-ZQFVzNGcrel9NKZYe7boyH5mboYJ2w " =591x121")

 ![](https://wiki.tu-zi.com/api/files.get?sig=eyJhbGciOiJIUzI1NiIsInR5cCI6IkpXVCJ9.eyJrZXkiOiJ1cGxvYWRzL2FjNjBlNmRhLTdjYTQtNDdjMS04ZTQxLTAxMDUyMDAwNzM3NS9mMmZiZjlmZC1lODA3LTQ4ZTQtOTc1NC1mNjZiZjM1NmYyNzQvaW1hZ2UucG5nIiwidHlwZSI6ImF0dGFjaG1lbnQiLCJpYXQiOjE3ODA0NTQ4NTQsImV4cCI6MTc4MDQ1ODQ1NH0.TuPB8If5gdIvCi63GW_LP73Jmbx0zQCzNelAFbV9T_s " =1243x647")

 ![](https://wiki.tu-zi.com/api/files.get?sig=eyJhbGciOiJIUzI1NiIsInR5cCI6IkpXVCJ9.eyJrZXkiOiJ1cGxvYWRzL2FjNjBlNmRhLTdjYTQtNDdjMS04ZTQxLTAxMDUyMDAwNzM3NS8zZTIyMDAyYy00MTM3LTQyNmYtYThiNC1lYjJkZjg3NzU3MTgvaW1hZ2UucG5nIiwidHlwZSI6ImF0dGFjaG1lbnQiLCJpYXQiOjE3ODA0NTQ4NTQsImV4cCI6MTc4MDQ1ODQ1NH0.TT-mhi5AlKvrwvBBrHnNTpd5WvJThZDTBrj1pDiMPkA " =599x289")

如果手动粘贴回调连接依旧显示OAuth认证失败，请参考： [OpenAI OAuth 登陆提示 localhost 连接失败-操作指南](https://wiki.tu-zi.com/doc/openai-oauth-localhost-7SM3WKytBI)

### Q3: 让 OpenClaw 切换模型没有反应？

尝试手动配置（第四步），或者检查：

* 全局配置文件中的 Codex 配置是否正确
* Gateway 是否已重启

### Q4: 提示 "Invalid config"？

检查 JSON 格式是否正确，常见错误：

* 少了逗号 `,`
* 多了逗号（最后一项后面不要加逗号）
* 引号不匹配

可以用这个命令验证 JSON 格式：

```bash
cat ~/.openclaw/openclaw.json | python3 -m json.tool
```


---

## 📚 相关文件路径

| 文件  | 路径  | 说明  |
|-----|-----|-----|
| 全局配置 | `~/.openclaw/openclaw.json` | OpenClaw 主配置文件 |
| Agent 模型配置 | `~/.openclaw/agents/<agent名>/agent/models.json` | 每个 Agent 的模型配置 |
| Agent 认证配置 | `~/.openclaw/agents/<agent名>/agent/auth-profiles.json` | 每个 Agent 的认证配置 |