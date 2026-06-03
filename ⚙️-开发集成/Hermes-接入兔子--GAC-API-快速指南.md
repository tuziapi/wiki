# Hermes 接入兔子 / GAC API 快速指南

# Hermes 接入兔子 / GAC API 快速指南

## 场景 1：没有 OpenClaw，首次配置 Hermes

### 1. 启动向导

在终端执行：

```bash
hermes setup
```

### 2. 跳过 OpenClaw 迁移

如果看到：

```text
Would you like to see what can be imported? [Y/n]:
```

输入：

```text
n
```

界面示例如下。如果当前环境检测到历史 OpenClaw 数据，但你这次要走全新配置，输入 `n` 跳过即可。

 ![如果提示可导入 OpenClaw 配置，输入 n 跳过](https://wiki.tu-zi.com/api/files.get?sig=eyJhbGciOiJIUzI1NiIsInR5cCI6IkpXVCJ9.eyJrZXkiOiJ1cGxvYWRzLzA0MTA4NzY3LTk1YjgtNDYzMi05YWFmLTgwNzgwZjIwMmFkMi82YTljNGFiMC01ZDRlLTQxYWQtOWRhNS1lZDQ5NWY0Njk3MTYv6L-B56e7LnBuZyIsInR5cGUiOiJhdHRhY2htZW50IiwiaWF0IjoxNzgwNDU0ODkyLCJleHAiOjE3ODA0NTg0OTJ9.RFxVJJEF7lrA7-Oq3fU7qzURo0705WtHG0fowEqTHfE)

### 3. 选择快速配置

选择：

```text
Quick setup
```

界面示例如下：

 ![在安装向导中选择 Quick setup](https://wiki.tu-zi.com/api/files.get?sig=eyJhbGciOiJIUzI1NiIsInR5cCI6IkpXVCJ9.eyJrZXkiOiJ1cGxvYWRzLzA0MTA4NzY3LTk1YjgtNDYzMi05YWFmLTgwNzgwZjIwMmFkMi9kODQyYWUwZC1iN2FlLTRjMjAtODYyNC0xYmNhMjFhZjE4ZDcv5b-r6YCf6YWN572uLnBuZyIsInR5cGUiOiJhdHRhY2htZW50IiwiaWF0IjoxNzgwNDU0ODkyLCJleHAiOjE3ODA0NTg0OTJ9.PhMUOqEci7P7VnJpeQ6bxBk3Fm11FBce_V5QsfHGhis)

### 4. 进入自定义接口配置

在 provider 列表中选择：

```text
More providers...
```

界面示例如下：

 ![在 provider 列表中选择 More providers...](https://wiki.tu-zi.com/api/files.get?sig=eyJhbGciOiJIUzI1NiIsInR5cCI6IkpXVCJ9.eyJrZXkiOiJ1cGxvYWRzLzA0MTA4NzY3LTk1YjgtNDYzMi05YWFmLTgwNzgwZjIwMmFkMi84MjMxNTI5MS1lODhkLTRiMWItYTI1Yi1iZmVhZGMxNjI1YzMv6Ieq5a6a5LmJ6YWN572uMS5wbmciLCJ0eXBlIjoiYXR0YWNobWVudCIsImlhdCI6MTc4MDQ1NDg5MiwiZXhwIjoxNzgwNDU4NDkyfQ.GzxDX9c5U0fStatbSsawrl4_O2MjxKuq3CAZu6N1Wiw)

然后选择：

```text
Custom endpoint (enter URL manually)
```

界面示例如下：

 ![在更多 provider 中选择 Custom endpoint (enter URL manually)](https://wiki.tu-zi.com/api/files.get?sig=eyJhbGciOiJIUzI1NiIsInR5cCI6IkpXVCJ9.eyJrZXkiOiJ1cGxvYWRzLzA0MTA4NzY3LTk1YjgtNDYzMi05YWFmLTgwNzgwZjIwMmFkMi84YTdjMjFmNy1mMjEzLTRmNDMtYmJmZi1iYmJiNjdlNDI2NjUv6Ieq5a6a5LmJ6YWN572uMi5wbmciLCJ0eXBlIjoiYXR0YWNobWVudCIsImlhdCI6MTc4MDQ1NDg5MiwiZXhwIjoxNzgwNDU4NDkyfQ.F7IIDRniR_ZAHmvY3rk5NhfN0p1UbuDykmVi6MQkIRI)

### 5. 根据业务线路填写接口信息

按提示填写 `API base URL`、`API key`、`Model name`。

填写界面示例如下：

 ![自定义接口配置界面，填写 API base URL 和 API key](https://wiki.tu-zi.com/api/files.get?sig=eyJhbGciOiJIUzI1NiIsInR5cCI6IkpXVCJ9.eyJrZXkiOiJ1cGxvYWRzLzA0MTA4NzY3LTk1YjgtNDYzMi05YWFmLTgwNzgwZjIwMmFkMi81Y2M0NDc4NS05ZDRlLTQyZDMtYTU5My04Yzk1MWJhYzJjNmMv6YWN572uaW5nLnBuZyIsInR5cGUiOiJhdHRhY2htZW50IiwiaWF0IjoxNzgwNDU0ODkyLCJleHAiOjE3ODA0NTg0OTJ9.CClNhF43ILUIBjtUp_rBPghN7YtsZ252n0W9PA5i0aU)

可参考以下填写方式：

#### 兔子主线路

* API base URL：`https://api.tu-zi.com/v1`
* API key：兔子 API Key
* Model name：优先选接口返回的模型；如需推荐示例可填 `gpt-5.4`、`claude-sonnet-4-6`

#### 兔子 Codex Coding 特别线路

* API base URL：`https://coding.tu-zi.com`
* API key：兔子 API Key
* Model name：优先选接口返回的 coding 模型

#### GAC Codex 线路

* API base URL：`https://gaccode.com/codex/v1`
* API key：GAC API Key
* Model name：优先选接口返回的模型；如需推荐示例可填 `gpt-5.4`

#### GAC Claude 线路

* API base URL：`https://gaccode.com/claudecode`
* API key：GAC API Key
* Model name：`claude-sonnet-4-6`、`claude-opus-4-6` 或接口返回的 Claude 模型

说明：

* 如果 Hermes 提示它实际验证成功的地址是 `/v1/models`，这通常是正常现象
* 如果看到了模型列表，优先从列表中选择
* 如果看到 `Context length in tokens [leave blank for auto-detect]:`，直接回车即可

### 7. 跳过消息平台配置

如果看到消息平台配置页面，选择：

```text
Skip
```

如果后续需要接入 Telegram、Discord 等平台，可再执行：

```bash
hermes setup gateway
```

### 8. 启动 Hermes

如果看到：

```text
Launch hermes chat now? [Y/n]:
```

直接按回车。

### 9. 验证是否成功

启动 Hermes：

```bash
hermes
```

或执行测试：

```bash
hermes chat -q "你好" -Q
```

如果 Hermes 能正常回复，就表示配置成功。


---

## 场景 2：已有 OpenClaw，迁移到 Hermes

### 1. 启动向导

```bash
hermes setup
```

### 2. 查看迁移内容

如果看到：

```text
Would you like to see what can be imported? [Y/n]:
```

按回车或输入：

```text
Y
```

### 3. 执行迁移

如果看到：

```text
Proceed with migration? [y/N]:
```

输入：

```text
y
```

### 4. 选择迁移后的默认 provider

根据你原本使用的线路选择，如：

* `tuzi-openclaw-codex`
* `tuzi-openclaw-claude`
* `gac-openclaw-codex`
* `gac-openclaw-claude`

建议：

* 代码、Agent、终端能力：优先选择 Codex 线路
* 对话、写作、分析：优先选择 Claude 线路

### 5. 如果提示手动输入模型名

建议按以下填写：

* 兔子 Codex / GAC Codex：优先选接口返回的模型；推荐示例可用 `gpt-5.4`
* 兔子 Claude / GAC Claude：优先选接口返回的 Claude 模型，如 `claude-sonnet-4-6`

### 6. 迁移后检查协议

迁移完成后，如果后续调用异常，优先检查 `api_mode`：

* Codex / GPT 路线：应为 `codex_responses`
* Claude 路线：应为 `anthropic_messages`

需要时可手动修正：

```bash
hermes config set model.api_mode codex_responses
```

或：

```bash
hermes config set model.api_mode anthropic_messages
```

### 7. 跳过消息平台配置

如果暂时只在本机使用，选择：

```text
Skip
```

### 8. 启动 Hermes

如果看到：

```text
Launch hermes chat now? [Y/n]:
```

直接按回车。


---

## 常用命令

重新运行向导：

```bash
hermes setup
```

修改模型和 provider：

```bash
hermes setup model
```

配置消息平台：

```bash
hermes setup gateway
```

配置工具能力：

```bash
hermes setup tools
```

查看当前配置：

```bash
hermes config show
```

编辑配置：

```bash
hermes config edit
```

启动 Hermes：

```bash
hermes
```


---

## 常见说明

### 为什么 provider 列表里会出现 `tuzi-openclaw-*` 或 `gac-openclaw-*`？

这表示 Hermes 里已经保存过这些 provider，通常来自历史迁移或历史手动配置。

这不代表当前正在重新迁移，只表示这些 provider 已经存在于 Hermes 配置中，可以直接选用。

### 为什么全新安装时不直接让所有用户选择 `tuzi-openclaw-codex`？

因为在真正的全新环境里，这些自定义 provider 不一定会自动出现。

为了保证所有用户都能复现，推荐使用：

```text
More providers... -> Custom endpoint (enter URL manually)
```

### `Some tools are disabled` 是什么意思？

表示部分附加工具还没有配置 API key。

这不会影响 Hermes 的基础聊天功能。

如果后续要补充工具功能，可以执行：

```bash
hermes setup tools
```