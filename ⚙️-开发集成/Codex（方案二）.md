# Codex（方案二）

# Codex（方案二子文档）

> 适用对象：希望使用 **官方原版 Codex CLI**，并通过 **兔子 API 按量付费** 的用户。

## 1. 这是什么

Codex 是面向开发场景的 CLI 工具。通过兔子 API 接入后，可以继续使用官方原版客户端，同时按实际调用量计费，无需包月。

## 2. 获取 API Key

### 步骤 1：进入兔子 API 平台

访问：<https://api.tu-zi.com/token>

### 步骤 2：创建 API 令牌

在左侧 **API 令牌创建** 中新建 Key。

### 步骤 3：选择正确分组

Codex 请务必选择：`Codex`

> 不建议使用 `default` 分组。Codex 使用专用分组通常更稳定、性能更好。

### 步骤 4：设置限额

建议在后台为该 Key 设置调用限额，避免超预期消耗。

## 3. 安装 Codex CLI

### 方式一：NPM 安装

```bash
npm i -g @openai/codex
codex --version
```

### 方式二：Homebrew 安装（macOS）

```bash
brew update && brew upgrade
brew install codex
codex --version
```

## 4. 配置方法

### 步骤 1：创建配置目录

```bash
mkdir -p ~/.codex
nano ~/.codex/config.toml
```

### 步骤 2：写入配置

```toml
model = "gpt-5"
model_provider = "tuzi"
model_reasoning_effort = "high"
disable_response_storage = true

[model_providers.tuzi]
name = "tuzi"
base_url = "https://api.tu-zi.com/v1"
env_key = "CODEX_API_KEY"
wire_api = "responses"
```

### 步骤 3：设置环境变量

```bash
export CODEX_API_KEY="你的兔子 API Key"
```

也可以写入 shell 配置文件，例如 `~/.zshrc` 或 `~/.bashrc`。

## 5. 开始使用

```bash
codex
```

如果没有把默认 profile 写死，也可以手动指定对应配置。

## 6. 适合客户看的重点

* 使用官方原版 Codex CLI
* 按量计费，不需要包月
* API Key 在兔子 API 后台获取
* 分组一定要选 `Codex`
* 建议设置限额，方便控制成本

## 7. 常见问题

### 1）codex 命令不存在

```bash
npx @openai/codex --version
```

### 2）Node 版本太低

建议升级到 Node.js 18+，推荐 22+ LTS。

### 3）配置后无法调用

优先检查：

* `CODEX_API_KEY` 是否正确
* `base_url` 是否为 `https://api.tu-zi.com/v1`
* API Key 分组是否为 `Codex`