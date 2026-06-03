# Claude Code（方案二）

# Claude Code（方案二子文档）

> 适用对象：希望使用 **官方原版 Claude Code**，并通过 **兔子 API 按量付费** 的用户。

## 1. 这是什么

这是方案二里最典型的使用方式：保留官方原版 Claude Code 体验，首次登录需要科学上网，后续模型调用走兔子 API。

## 2. 获取 API Key

### 步骤 1：进入兔子 API 平台

访问：<https://api.tu-zi.com/token>

### 步骤 2：创建 API 令牌

在左侧 **API 令牌创建** 中新建 Key。

### 步骤 3：选择正确分组

Claude Code 推荐选择以下任一分组：

* `Claude-Code`
* `Claude`
* `Claude原价`

> 以上分组通常都比 `default` 分组更稳定。

### 步骤 4：设置限额

建议在后台为 Key 设置调用限额，方便控制成本。

## 3. 安装 Claude Code

```bash
npm install -g @anthropic-ai/claude-code
```

如果此前安装过改版客户端，可先卸载：

```bash
npm uninstall -g @anthropic-ai/claude-code
rm -rf ~/.claude*
```

## 4. 配置方法

### 步骤 1：设置环境变量

```bash
export ANTHROPIC_API_TOKEN=""
export ANTHROPIC_API_KEY="你的兔子 API Key"
export ANTHROPIC_BASE_URL="https://api.tu-zi.com"
```

Windows CMD 可参考：

```bash
setx ANTHROPIC_API_KEY "你的兔子 API Key"
setx ANTHROPIC_BASE_URL "https://api.tu-zi.com"
```

### 步骤 2：把 Key 加入 `.claude.json` 的 approved 列表

```bash
(cat ~/.claude.json 2>/dev/null || echo 'null') | jq --arg key "${ANTHROPIC_API_KEY: -20}" '(. // {}) | .customApiKeyResponses.approved |= ([.[]?, $key] | unique)' > ~/.claude.json.tmp && mv ~/.claude.json.tmp ~/.claude.json
```

## 5. 首次登录与使用

```bash
claude
```

首次身份验证通常仍需科学上网；完成后，后续 API 调用走兔子 API。

## 6. 适合客户看的重点

* 使用官方原版 Claude Code
* 按量计费，适合轻度或不确定使用量的客户
* API Key 在兔子 API 后台获取
* 推荐分组：`Claude-Code` / `Claude` / `Claude原价`
* 不建议使用 `default` 分组
* 建议设置 API 限额控制成本

## 7. 常见问题

### 1）首次登录为什么还需要科学上网

因为官方原版 Claude Code 的首次身份验证流程仍然走官方登录体系。

### 2）已经装过改版怎么办

先卸载改版，再安装官方原版，避免配置冲突。

### 3）设置了 Key 还是不生效

优先检查：

* `ANTHROPIC_API_KEY` 是否正确
* `ANTHROPIC_BASE_URL` 是否为 `https://api.tu-zi.com`
* API Key 分组是否选对
* `.claude.json` 是否已加入 approved 标识