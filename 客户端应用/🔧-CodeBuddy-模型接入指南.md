# 🔧 CodeBuddy 模型接入指南

# 一、准备信息

* **模型名（id）**：例如 `claude-sonnet-4-6`
* **Base URL**：`https://api.tu-zi.com/v1/chat/completions`
* **API Key**：形如 `sk-xxxxxx`


---

## 二、先去 Tuzi 官网获取 Key（重点）


1. 登录 Tuzi 官网控-工作台
2. 点击创建或复制可用 Key
3. 在模型/线路选择时，选择 **「Claude Code」分组**
4. 在模型价格页面可以查看该分组对应的可用模型（如 sonnet/haiku/opus）


---

## 三、CodeBuddy 配置文件位置

推荐使用**用户级配置**（全局生效），如果目录下没有该配置文件，先新建一个：

* `~/.codebuddy/models.json`

也支持项目级配置（只对当前项目生效）：

* `<project-root>/.codebuddy/models.json`


---

## 四、最小可用模板（可直接复制）

```json
{
  "models": [
    {
      "id": "claude-sonnet-4-6",
      "name": "claude-sonnet-4-6",
      "vendor": "OpenAI-Compatible",
      "url": "https://api.tu-zi.com/v1/chat/completions",
      "apiKey": "你的TuziKey",
      "supportsToolCall": true,
      "supportsImages": true
    }
  ]
}
```


---

## 五、Claude Code 分组常用模型示例

```json
{
  "models": [
    {
      "id": "claude-sonnet-4-6",
      "name": "claude-sonnet-4-6",
      "vendor": "OpenAI-Compatible",
      "url": "https://api.tu-zi.com/v1/chat/completions",
      "apiKey": "你的TuziKey",
      "supportsToolCall": true,
      "supportsImages": true
    },
    {
      "id": "claude-3-5-haiku-latest",
      "name": "claude-3-5-haiku-latest",
      "vendor": "OpenAI-Compatible",
      "url": "https://api.tu-zi.com/v1/chat/completions",
      "apiKey": "你的TuziKey",
      "supportsToolCall": true,
      "supportsImages": true
    },
    {
      "id": "claude-3-5-haiku-20241022",
      "name": "claude-3-5-haiku-20241022",
      "vendor": "OpenAI-Compatible",
      "url": "https://api.tu-zi.com/v1/chat/completions",
      "apiKey": "你的TuziKey",
      "supportsToolCall": true,
      "supportsImages": true
    }
  ]
}
```


---

## 六、配置后如何验证


1. 保存 `models.json`
2. 打开 CodeBuddy 模型下拉
3. 选择你刚添加的模型（如 `claude-sonnet-4-6`）
4. 发起一次对话测试