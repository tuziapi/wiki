# ⚙️Openclaw（小龙虾）配置

## 前置要求


1. ✅ 已成功安装 OpenClaw
2. ✅ 拥有有效的 API Key（<https://api.tu-zi.com/token>），此处默认Claude分组（不能用default分组，因为需要支持tools）

 ![](https://wiki.tu-zi.com/api/files.get?sig=eyJhbGciOiJIUzI1NiIsInR5cCI6IkpXVCJ9.eyJrZXkiOiJ1cGxvYWRzL2RiZTJjMjRhLWQ4M2MtNGUxMy1iYzc2LTZlNDBmZGM3YmZlNS80MWFmMjY0My01YmM0LTRmZmMtYmUzOS01OGYwODg4OGQwNWQv5LyB5Lia5b6u5L-h5oiq5Zu-XzM1MDg4ZGQ5LTY1ZjQtNDYyYi1hYWNiLWVmYmRiMTQzZDBjYy5wbmciLCJ0eXBlIjoiYXR0YWNobWVudCIsImlhdCI6MTc4MDQ1NDg5MCwiZXhwIjoxNzgwNDU4NDkwfQ.-AS1j_qOXX_tkJIbIRtbh1sx7ihImqEJCorEWA0UMdk " =595x758")

## 配置步骤

### 步骤 1：打开配置文件

**方式 A：图形界面（推荐新手）**

在终端输入以下命令，系统将自动用「文本编辑」打开配置文件：

```bash
open -e ~/.openclaw/openclaw.json
```

**方式 B：命令行编辑器**

使用文本编辑器打开配置文件：

```bash
# macOS/Linux
nano ~/.openclaw/openclaw.json
# 或使用其他您喜欢的编辑器
vim ~/.openclaw/openclaw.json
```

### 步骤 2：修改配置内容

在配置文件中找到 `"auth"`、`"models"`、`"agents"` 这三个部分，如果还未配置新增即可，将它们**完整替换**为以下内容（注意不要删除其他配置模块）：

#### 2.1 替换/新增 `auth` 配置

```json
"auth": {
  "profiles": {
    "tuzi:default": {
      "provider": "tuzi",
      "mode": "api_key"
    }
  }
}
```


#### 2.2 替换/新增 `models` 配置

> ⚠️ **重要**：将 `"your-api-key-here"` 替换为您实际的 API Key！

```json
"models": {
  "providers": {
    "tuzi": {
      "baseUrl": "https://api.tu-zi.com",
      "apiKey": "your-api-key-here",
      "api": "anthropic-messages",
      "models": [
        {
            "id": "claude-sonnet-4-5-20250929",
            "name": "Claude Sonnet 4.5",
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
            "maxTokens": 8192
          },
          {
            "id": "claude-opus-4-5",
            "name": "Claude Opus 4.5",
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
            "maxTokens": 8192
          }
      ]
    }
  }
}
```

> 💡 **提示**：
>
> * 如果您使用的是`gaccode`方案，更改 `baseUrl` 的地址为：`https://gaccode.com/claudecode`
> * 可以自行更换配置中的模型，只需修改 `models` 数组中的 `id` 和 `name` 即可（模型名称在站点官网-模型价格中获取），注意模型必须为 apiKey 对应分组下可用模型
>
>   \
> * ![修改 id 和 name 字段，即可更换模型](https://wiki.tu-zi.com/api/files.get?sig=eyJhbGciOiJIUzI1NiIsInR5cCI6IkpXVCJ9.eyJrZXkiOiJ1cGxvYWRzL2FjNjBlNmRhLTdjYTQtNDdjMS04ZTQxLTAxMDUyMDAwNzM3NS8zYTUzMzFhYS01MjkwLTQwNTAtOTAwMC05MTYxNDEwMDcxNjUvaW1hZ2UucG5nIiwidHlwZSI6ImF0dGFjaG1lbnQiLCJpYXQiOjE3ODA0NTQ4OTAsImV4cCI6MTc4MDQ1ODQ5MH0.AwoINObJGODvfUAAjZb2dLj-9CHAmb-xnzaHvc6mTq0 " =428x586")


#### 2.3 替换/新增 `agents` 配置

```json
"agents": {
  "defaults": {
    "model": {
      "primary": "tuzi/claude-sonnet-4-5-20250929",
      "fallbacks": [
        "tuzi/claude-opus-4-5"
      ]
    },
    "models": {
      "tuzi/claude-opus-4-5": {},
      "tuzi/claude-sonnet-4-5-20250929": {}
    }
  }
}
```


---

### 步骤 3：完整配置示例

完成后，您的配置文件应该包含以下内容（以及其他原有的配置模块）：

```json
{
  "auth": {
    "profiles": {
      "tuzi:default": {
        "provider": "tuzi",
        "mode": "api_key"
      }
    }
  },
  "models": {
    "providers": {
      "tuzi": {
        "baseUrl": "https://api.tu-zi.com",
        "apiKey": "your-api-key-here",
        "api": "anthropic-messages",
        "models": [
          {
            "id": "claude-sonnet-4-5-20250929",
            "name": "Claude Sonnet 4.5",
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
            "maxTokens": 8192
          },
          {
            "id": "claude-opus-4-5",
            "name": "Claude Opus 4.5",
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
            "maxTokens": 8192
          }
        ]
      }
    }
  },
  "agents": {
    "defaults": {
      "model": {
        "primary": "tuzi/claude-sonnet-4-5-20250929",
        "fallbacks": [
            "tuzi/claude-opus-4-5"
        ]
      },
      "models": {
        "tuzi/claude-opus-4-5": {},
        "tuzi/claude-sonnet-4-5-20250929": {}
      }
    }
  }
}
```

### 步骤 4：保存并重启


1. **保存配置文件**
   * **方式 A 图形界面**：按 `Command + S` 保存，关闭窗口即可
   * **方式 B nano 编辑器**：按 `Ctrl + O` 保存，`Ctrl + X` 退出
   * **方式 B vim 编辑器**：按 `ESC`，输入 `:wq` 保存退出

     \
2. **重启 OpenClaw 使配置生效，在终端输入以下命令：**

```bash
openclaw gateway restart
```


---

## ✅ 验证配置

配置完成后，使用 **TUI（终端用户界面）模式**测试是否配置成功：

```bash
openclaw tui

### 测试对话

在 TUI 界面中输入一个简单的问题来测试：
```
你好，请做个自我介绍

你好！我是运行在 OpenClaw 框架里的 AI 助手，...
```

## 💡 提示

配置完成后，您可以：

* 通过命令行直接进行对话
* 集成到飞书等通讯工具
* 构建自定义 AI 工作流

**祝使用愉快！** 🎉