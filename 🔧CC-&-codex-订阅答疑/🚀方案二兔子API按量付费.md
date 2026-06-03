# 🚀方案二:兔子API按量付费

## 1. 方案概览

按量付费，按实际用量结算；无需包月，适合轻度或不确定用量的用户。与方案一相比：保持官方原版体验，首次登录需科学上网，其余调用走兔子API高速线路。



| A 官方原版体验 | B 成本可控 |
|----------|--------|
| 使用 **官方 Claude Code** 客户端 | 后台可设置调用限额 |
| 无绑定设备限制，多端可用 | 轻量使用性价比更优 |
| 首次登录需科学上网，后续调用无需翻墙 | 同一 Key 可同时支持 Codex |


> **提示:**  现已支持 OpenAI Codex，使用同一 API Key 即可在 Codex CLI 中按量使用。

## 2. 快速流程

### 2.1 获取 API Key

在兔子API后台创建 Key，并选择合适的分组

### 2.2 安装 Claude Code 或 Codex

按系统要求安装官方 Claude Code 或 Codex CLI

### 2.3 配置环境变量

设置 ANTHROPIC_API_KEY 与 ANTHROPIC_BASE_URL（Codex 使用 CODEX_API_KEY）

### 2.4 首次登录

Claude Code 浏览器登录并粘贴绑定 code 完成验证

### 2.5 开始使用

开始日常工作流，按量计费，可在后台设置限额

## 3. 获取兔子API Key

> **🐇 方案二特点：** 使用官方原版Claude Code + 兔子API，按量付费，适合轻度使用用户。

### 步骤 1：访问兔子API平台

访问 <https://api.tu-zi.com/token>

### 步骤 2：创建API令牌

在左侧「**API 令牌创建**」处生成 Key

> **📝 重点：**
>
> * **Claude Code 使用：** 分组选择 `Claude-Code` 或 `Claude` 或 `Claude原价`
> * **Codex 使用：** 分组选择 `Codex`（专用分组，性能更优）
>
> 以上分组都比 `default` 分组稳定得多

### 步骤 3：设置调用限额

记得在后台为 API Key 设置调用限额，控制使用成本。

## 4. Claude Code 使用详解

### 4.1 系统要求

* > * **操作系统**：macOS 10.15+ / Ubuntu 20.04+ / Debian 10+ / Windows
  > * **硬件**：≥ 2 GB RAM
  > * **软件**：Node.js 18+、Git 2.23+（可选）、GitHub/GitLab CLI（可选）
  > * **网络**：
  >   * 首次身份验证需「科学上网」（非中国大陆及港澳台）
  >   * 若使用兔子 API 或 gaccode，后续 AI 调用阶段无需继续翻墙

### 4.2 安装 Claude Code

```bash
# 全局安装（更多用法见官方文档）
npm install -g @anthropic-ai/claude-code
```

> **如果已经安装过改版的需要卸载，可执行如下卸载：**
>
> ```bash
> npm uninstall -g @anthropic-ai/claude-code
> rm -rf ~/.claude*
> ```

> **安装claude 遇到问题**
>
> 点击下面链接
>
> **[claudecode 无法连接Anthropic 服务](https://wiki.tu-zi.com/s/8c61a536-7a59-4410-a5e2-8dab3d041958/doc/claudecode-anthropic-kBqvPtVURx)**

### 4.3 配置兔子API环境变量

```bash
# 注意，我们用的是key，不是token，为防止冲突，强行重置
export ANTHROPIC_API_TOKEN=""
export ANTHROPIC_API_KEY=sk-xxxxxxxxxxxxxxxxx  # 替换为你的兔子API Key
export ANTHROPIC_BASE_URL=https://api.tu-zi.com

# Windows CMD（命令提示符）中
# setx ANTHROPIC_API_KEY "sk-xxxxxxxxxxxxxxxxx"
# setx ANTHROPIC_BASE_URL "https://api.tu-zi.com"
```

 ![](https://wiki.tu-zi.com/api/files.get?sig=eyJhbGciOiJIUzI1NiIsInR5cCI6IkpXVCJ9.eyJrZXkiOiJ1cGxvYWRzL2I3MTgwNDFlLWUwNjItNDRlMy1iNTljLTlkYzliNjNjODczMi83YmI2NGRiNS0xMWU1LTRlOTUtYWM1Mi0wZWIzODFhOWE3MzkvaW1hZ2UucG5nIiwidHlwZSI6ImF0dGFjaG1lbnQiLCJpYXQiOjE3ODA0NTQ5NTUsImV4cCI6MTc4MDQ1ODU1NX0.kus-L4brurViG9HmVycSU75jLmsK-Dpz_Zmljg0gIV0 " =942x80")

#### 把 Anthropic API Key 的最后 20 位加入 `.claude.json` 中的 "approved" 列表，作为一个已允许的 key 标识

```javascript
(cat ~/.claude.json 2>/dev/null || echo 'null') | jq --arg key "${ANTHROPIC_API_KEY: -20}" '(. // {}) | .customApiKeyResponses.approved |= ([.[]?, $key] | unique)' > ~/.claude.json.tmp && mv ~/.claude.json.tmp ~/.claude.json
```

 ![](https://wiki.tu-zi.com/api/files.get?sig=eyJhbGciOiJIUzI1NiIsInR5cCI6IkpXVCJ9.eyJrZXkiOiJ1cGxvYWRzL2I3MTgwNDFlLWUwNjItNDRlMy1iNTljLTlkYzliNjNjODczMi9kNjM4NjhjYS02OTM1LTRkOWMtYjc5Ni1kMWJkMDFlY2M3MzQvaW1hZ2UucG5nIiwidHlwZSI6ImF0dGFjaG1lbnQiLCJpYXQiOjE3ODA0NTQ5NTUsImV4cCI6MTc4MDQ1ODU1NX0._D8t44bPJo3P0eGejnCQcHVcKJSItkqHQhRMBaQd09U " =1840x226")


**启动 claude code**

```javascript
claude
```


> **⚠️ 重要提醒：**
>
> * 请将 `sk-xxxxxxxxxxxxxxxxx` 替换为你在兔子API平台获得的实际API Key
> * 每次使用前都需要设置这些环境变量，或者将其添加到系统环境变量中
> * 首次身份验证仍需「科学上网」，但后续使用无需翻墙
> * 按量付费模式，建议设置合理的API调用限额控制成本

### 4.4 初始化与演示

#### 步骤 1：选择外观

 ![](https://wiki.tu-zi.com/api/files.get?sig=eyJhbGciOiJIUzI1NiIsInR5cCI6IkpXVCJ9.eyJrZXkiOiJ1cGxvYWRzL2I3MTgwNDFlLWUwNjItNDRlMy1iNTljLTlkYzliNjNjODczMi8xYzEzODM0Mi1jMDc2LTQxNTUtYjQ4Yy1hYTJmODExOWQxNjMvaW1hZ2UucG5nIiwidHlwZSI6ImF0dGFjaG1lbnQiLCJpYXQiOjE3ODA0NTQ5NTUsImV4cCI6MTc4MDQ1ODU1NX0.s9wIoj0_Xt3JVexPDyAAtXS3UMZvSJS8XPRBDMi6ykk " =841x627")


#### 步骤 2：按 enter 进入claude

 ![](https://wiki.tu-zi.com/api/files.get?sig=eyJhbGciOiJIUzI1NiIsInR5cCI6IkpXVCJ9.eyJrZXkiOiJ1cGxvYWRzL2I3MTgwNDFlLWUwNjItNDRlMy1iNTljLTlkYzliNjNjODczMi8wNzIyZDc1NC0zYTBjLTRiODgtYWIwMS1mODZiZGM4YmZhNDkvaW1hZ2UucG5nIiwidHlwZSI6ImF0dGFjaG1lbnQiLCJpYXQiOjE3ODA0NTQ5NTUsImV4cCI6MTc4MDQ1ODU1NX0.NHjrYKr36ucE4XlL-VFkRWA14BRZveLTIu7tD8lSjhE " =817x527")

#### 步骤 3：同意协议

 ![](https://wiki.tu-zi.com/api/files.get?sig=eyJhbGciOiJIUzI1NiIsInR5cCI6IkpXVCJ9.eyJrZXkiOiJ1cGxvYWRzL2I3MTgwNDFlLWUwNjItNDRlMy1iNTljLTlkYzliNjNjODczMi9lY2I0OGI3YS02YzNhLTQ5M2UtYTBiMi00NWUxMjFlZTVhMGEvaW1hZ2UucG5nIiwidHlwZSI6ImF0dGFjaG1lbnQiLCJpYXQiOjE3ODA0NTQ5NTUsImV4cCI6MTc4MDQ1ODU1NX0.VFrU8kujznPXkpzRQ5wCscTUxRSEV4FLENcthXmqY88 " =932x352")

#### 步骤 4：开始使用

 ![](https://wiki.tu-zi.com/api/files.get?sig=eyJhbGciOiJIUzI1NiIsInR5cCI6IkpXVCJ9.eyJrZXkiOiJ1cGxvYWRzL2I3MTgwNDFlLWUwNjItNDRlMy1iNTljLTlkYzliNjNjODczMi81MTI5ZWUxNS03ZTYxLTQ5ZTEtOGZmNi0wNWVmMThmNDUwYTEvaW1hZ2UucG5nIiwidHlwZSI6ImF0dGFjaG1lbnQiLCJpYXQiOjE3ODA0NTQ5NTUsImV4cCI6MTc4MDQ1ODU1NX0.WbjEF67-0ngZZjiKiTMb4juL-Rie3wIEXq0T8a-mxBs " =861x433")

#### 

**效果展示视频**

[https://www.bilibili.com/video/BV1Q4MkzVEpU/?vd%5Fsource=44035ad5b3c23e782b73e09ffbd13b7d](https://www.bilibili.com/video/BV1Q4MkzVEpU/?vd%5Fsource=44035ad5b3c23e782b73e09ffbd13b7d)

## 5. Codex 配置教程

> **🚀 全新功能：** 现在可以使用兔子API的 `Codex` 分组，在 OpenAI Codex 原版客户端中按量使用强大的AI编程工具！

### 5.1 系统要求与兼容性

> #### 💻 系统要求
>
> * **操作系统：** macOS 12+ / Ubuntu 20.04+ / Windows 10+ (WSL2)
> * **Git：** 2.23+ (可选)
> * **内存：** 4 GB 最低，8 GB+ 推荐
> * **Node.js：** 18+ (推荐 22+ LTS)
> * **存储空间：** 500 MB 最低，2 GB 推荐
>
> #### ⚡ 性能优化建议
>
> * 使用 SSD 存储提升性能
> * 启用 PR 助手功能
> * 16 GB 内存适合大型项目
> * 使用 nvm 管理 Node.js 版本
> * 预留日志和缓存空间

### 5.2 安装 Codex CLI

#### 方式 1：NPM 包安装（通用推荐）

```bash
# 全局安装
npm i -g @openai/codex

# 验证安装
codex --version
```

#### 方式 2：Homebrew 安装（macOS 推荐）

```bash
# 更新 Homebrew
brew update && brew upgrade

# 安装 Codex
brew install codex

# 验证安装
codex --version
```

### 5.3 兔子API配置

> **⚠️ 重要：** 使用 Codex 时，请在兔子API后台创建 API Key 时选择 `Codex` 分组，确保最佳性能。

#### 步骤 1：创建配置目录

```bash
mkdir -p ~/.codex
nano ~/.codex/config.toml
```

#### 步骤 2：config.toml 配置

```toml
# 核心设置
model = "gpt-5.5"    # 默认AI模型
model_provider = "tuzi"  # 服务提供商
model_reasoning_effort = "high"
disable_response_storage = true

[model_providers.tuzi]
name = "tuzi"
base_url = "https://api.tu-zi.com/v1"
env_key = "CODEX_API_KEY"
wire_api = "responses"
```

#### 步骤 3：auth.json 配置

```bash
nano ~/.codex/auth.json
```

```json
{
  "OPENAI_API_KEY": null
}
```

#### 步骤 4：环境变量设置

```bash
# 配置兔子API Key
echo 'export CODEX_API_KEY=sk-your-tuzi-api-key' >> ~/.bashrc

# 重新加载环境
source ~/.bashrc
```

### 5.4 启动与验证

```bash
# 启动 Codex
codex
```

> **🎯 Codex 使用场景：**
>
> * **开发调试：** 代码分析与修复、代码文档生成、重构优化
> * **项目构建：** 快速原型开发、测试用例生成、CI/CD管道配置
> * **数据处理：** 数据转换、数据可视化、日志分析

### 5.5 安全策略与沙箱管理

#### 🛡️ 安全级别

* `read-only` - 仅读取文件（代码审查）
* `workspace-write` - 写入项目文件（日常开发）
* `danger-full-access` - 完全系统权限（系统管理）

#### ⚙️ 策略配置

```bash
# 临时提升权限
codex --sandbox danger-full-access --approve-all

# 降级权限
codex --sandbox read-only

# 批量操作模式
codex --batch-mode --auto-confirm
```

## 6. Gemini 配置教程

### 6.1 系统要求


* > * **操作系统**：macOS 10.15+ / Ubuntu 20.04+ / Debian 10+ / Windows
  > * **硬件**：≥ 2 GB RAM
  > * **软件**：Node.js 18+、Git 2.23+（可选）、GitHub/GitLab CLI（可选）

  \

### 6.2 安装 Gemini CLI

首先，使用 npm (Node Package Manager) 在您的系统上全局安装 Gemini CLI。请打开终端并运行以下命令：

```javascript
npm install -g @google/gemini-cli
```

### 6.3  配置环境变量

我们需要设置两个变量：一个用于指定 API 的接入点，另一个用于存放您的 API Key。

**mac / linux** 配置

将以下两行命令添加到您的 shell 配置文件中 (例如 `~/.zshrc` 或 `~/.bashrc`)。

```javascript
export GOOGLE_GEMINI_BASE_URL="https://api.tu-zi.com"
export GEMINI_API_KEY="sk-Xvs..."
```

添加完成后，执行 `source ~/.zshrc` (或您对应的配置文件) 或重启终端，以使配置生效。

```javascript
source ~/.zshrc
```

**window 配置**

```javascript
setx GOOGLE_GEMINI_BASE_URL "https://api.tu-zi.com"
setx GEMINI_API_KEY "sk-Xvs..."
```

### 6.4 开始使用

```javascript
gemini
```


> **相关参考资料**
>
> 要了解更多信息或获取帮助，请参考github 官方：
>
> * **[Gemini CLI GitHub 仓库](https://github.com/google-gemini/gemini-cli)**：查看 Gemini CLI 的源代码、报告问题或了解更多高级用法。

## 7. 故障排除与优化

**问题 1：codex 命令不存在**

```bash
npm config get prefix  # 检查全局安装路径是否在 PATH
npx @openai/codex --version  # 临时按需执行
```

**问题 2：Node 版本过旧**

```bash
# 推荐使用 nvm 管理版本
nvm install 22 && nvm use 22
```

**问题 3：权限问题**

```bash
# 仅在必要时使用 sudo
sudo npm i -g @openai/codex
```

**问题 4：网络连通性检查**

```bash
ping -c 4 api.tu-zi.com
nslookup api.tu-zi.com
# 服务器 443 端口
# telnet api.tu-zi.com 443
```

**问题 5：Codex 配置验证**

```bash
codex config validate
codex config debug --verbose
```

## 使用教程

**高级参数：YOLO 模式**

对于批量处理任务，可以使用 `--dangerously-skip-permissions` 参数：

```bash
claude --dangerously-skip-permissions
```

> **安全的 YOLO 模式** | 绕过所有权限检查，让 Claude 不受干扰地工作直到完成，而不是监督 Claude。这对于修复 lint 错误或生成样板代码等工作流程非常有效。

> **⚠️ 使用场景建议：**
>
> * 修复代码风格和 lint 错误
> * 生成重复性样板代码
> * 批量文件处理任务
> * 已知安全的自动化操作

### 视频教程

原版Claude Code的使用教程，我们两个方案的一致使用

[https://www.bilibili.com/video/BV1VkMTzjEhy/?vd%5Fsource=44035ad5b3c23e782b73e09ffbd13b7d](https://www.bilibili.com/video/BV1VkMTzjEhy/?vd%5Fsource=44035ad5b3c23e782b73e09ffbd13b7d)

## 8. 更多资源

* 推荐关注推特的[宝玉老师](https://x.com/dotey)、[海拉鲁编程客](https://x.com/hylarucoder)获得更多Claude Code的实务经验
* 推荐两官文[Claude Code：代理编码的最佳实践](https://www.anthropic.com/engineering/claude-code-best-practices)、[Claude Code进行常见工作流程的分步教程](https://docs.anthropic.com/zh-CN/docs/claude-code/tutorials)
* [社区服务与支持](https://wiki.tu-zi.com/zh/group)：加入兔子AI活跃的用户社区，获取最新资讯、技术支持和使用技巧。


\