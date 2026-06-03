# Gemini CLI（方案二）

# Gemini CLI（方案二子文档）

> 适用对象：希望使用 **官方原版 Gemini CLI**，并通过 **兔子 API 按量付费** 的用户。

## 1. 这是什么

Gemini CLI 可以通过兔子 API 接入使用。配置完成后，用户可以保留官方原版使用方式，同时走兔子 API 的线路与结算体系。

## 2. 获取 API Key

### 步骤 1：进入兔子 API 平台

访问：<https://api.tu-zi.com/token>

### 步骤 2：创建 API 令牌

在左侧 **API 令牌创建** 中新建 Key。

### 步骤 3：选择正确分组

如果后台已有 Gemini 专用分组，优先选择 Gemini 对应分组；如果你们当前销售口径有固定分组名称，也建议在这里统一写清楚。

> 如果暂时没有单独展示 Gemini 分组，建议由运营补充明确口径，避免客户误选。

### 步骤 4：设置限额

建议在后台为 Key 设置调用限额，方便控制成本。

## 3. 安装 Gemini CLI

```bash
npm install -g @google/gemini-cli
```

## 4. 配置方法

### macOS / Linux

将以下内容写入 `~/.zshrc` 或 `~/.bashrc`：

```bash
export GOOGLE_GEMINI_BASE_URL="https://api.tu-zi.com"
export GEMINI_API_KEY="你的兔子 API Key"
```

然后执行：

```bash
source ~/.zshrc
```

### Windows

```bash
setx GOOGLE_GEMINI_BASE_URL "https://api.tu-zi.com"
setx GEMINI_API_KEY "你的兔子 API Key"
```

## 5. 开始使用

```bash
gemini
```

## 6. 适合客户看的重点

* 使用官方原版 Gemini CLI
* 按量计费
* API Key 在兔子 API 后台获取
* 建议为 Gemini 单独说明推荐分组
* 建议设置限额，方便控制成本

## 7. 常见问题

### 1）配置后无法使用

优先检查：

* `GEMINI_API_KEY` 是否正确
* `GOOGLE_GEMINI_BASE_URL` 是否为 `https://api.tu-zi.com`
* API Key 分组是否选对

### 2）客户最容易搞混什么

最容易混淆的是：

* 把 Gemini 的 Key 和 Claude / Codex 的配置方式混在一起
* 没写清楚该去哪里创建 Key
* 没写清楚应该选哪个分组

所以建议文档里把"获取 API Key"单独放在 Gemini 小节里讲清楚。