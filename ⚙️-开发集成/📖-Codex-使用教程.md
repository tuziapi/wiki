# 📖 Codex 使用教程

# Codex CLI 完整操作手册

## 目录


1. [简介](#%E7%AE%80%E4%BB%8B)
2. [快速开始](#%E5%BF%AB%E9%80%9F%E5%BC%80%E5%A7%8B)
3. [基本用法](#%E5%9F%BA%E6%9C%AC%E7%94%A8%E6%B3%95)
4. [沙盒和权限管理](#%E6%B2%99%E7%9B%92%E5%92%8C%E6%9D%83%E9%99%90%E7%AE%A1%E7%90%86)
5. [配置管理](#%E9%85%8D%E7%BD%AE%E7%AE%A1%E7%90%86)
6. [高级功能](#%E9%AB%98%E7%BA%A7%E5%8A%9F%E8%83%BD)
7. [MCP协议集成](#mcp%E5%8D%8F%E8%AE%AE%E9%9B%86%E6%88%90)
8. [故障排除和调试](#%E6%95%85%E9%9A%9C%E6%8E%92%E9%99%A4%E5%92%8C%E8%B0%83%E8%AF%95)

## 简介

Codex CLI 是一个强大的AI辅助编程工具，可以帮助开发者完成各种编程任务，包括代码生成、重构、测试、文档编写等。它支持交互式和非交互式两种工作模式，并具备完善的安全沙盒机制。

## 快速开始

### 基本命令

| 命令  | 功能  | 示例  |
|-----|-----|-----|
| `codex` | 启动交互式TUI界面 | `codex` |
| `codex "提示内容"` | 带初始提示启动交互式界面 | `codex "修复lint错误"` |
| `codex exec "任务"` | 非交互式自动化模式 | `codex exec "解释utils.ts文件"` |

### 主要标志参数

* `--model/-m`: 指定使用的模型
* `--ask-for-approval/-a`: 设置权限批准策略
* `--sandbox`: 设置沙盒模式
* `--full-auto`: 全自动模式（相当于 `--sandbox workspace-write` + `--ask-for-approval on-failure`）

## 基本用法

### 会话管理

#### 恢复会话

```bash
# 显示会话选择器
codex resume

# 恢复最近的会话
codex resume --last

# 按ID恢复特定会话
codex resume 7f9f9a2e-1b3c-4c7a-9b0e-123456789abc
```

#### 带提示运行

```bash
# 基本提示
codex "解释这个代码库"

# 全自动模式
codex --full-auto "创建一个待办事项应用"
```

### 实用示例

| 任务  | 命令  | 结果  |
|-----|-----|-----|
| React组件重构 | `codex "将Dashboard组件重构为React Hooks"` | 重写类组件，运行`npm test`，显示差异 |
| 数据库迁移 | `codex "生成用户表的SQL迁移文件"` | 推断ORM，创建迁移文件并在沙盒数据库中运行 |
| 单元测试 | `codex "为utils/date.ts编写单元测试"` | 生成测试，执行并迭代直到通过 |
| 文件重命名 | `codex "使用git mv批量重命名*.jpeg为*.jpg"` | 安全重命名文件并更新导入/使用 |
| 代码解释 | `codex "解释这个正则表达式: ^(?=.*[A-Z]).{8,}$"` | 输出详细的人类可读解释 |
| 代码审查 | `codex "仔细审查这个仓库，提出3个高影响的PR建议"` | 在当前代码库中建议有影响力的PR |
| 安全审计 | `codex "查找漏洞并创建安全审查报告"` | 发现并解释安全漏洞 |

### 实用技巧

#### 文件搜索

* 输入`@`触发模糊文件名搜索
* 使用上下箭头选择结果
* Tab或Enter确认选择，Esc取消

#### 图像输入

```bash
# 粘贴图像到编辑器
Ctrl+V / Cmd+V

# 命令行附加图像
codex -i screenshot.png "解释这个错误"
codex --image img1.png,img2.jpg "总结这些图表"
```

#### 编辑历史消息

* 当编辑器为空时，按Esc进入"回溯"模式
* 再次按Esc打开历史预览
* 重复按Esc选择更早的消息
* Enter确认编辑

#### Shell补全

```bash
codex completion bash   # Bash补全
codex completion zsh    # Zsh补全  
codex completion fish   # Fish补全
```

#### 工作目录设置

```bash
# 使用--cd指定工作目录
codex --cd /path/to/project "分析代码"
```

## 沙盒和权限管理

### 权限模式概述

Codex提供三种主要的权限预设：


1. **只读模式**: Codex可以读取文件和回答问题；编辑、运行命令和网络访问需要批准
2. **自动模式**: Codex可以在工作区内读取文件、编辑和运行命令而无需批准；工作区外或网络访问需要批准
3. **完全访问**: 完全的磁盘和网络访问权限，无提示；极其危险

### 沙盒模式

#### 三种沙盒级别


1. **read-only**: 只读访问，可以读取任何文件，但写入和网络访问被阻止
2. **workspace-write**: 当前工作目录可写（以及macOS上的`$TMPDIR`）
3. **danger-full-access**: 禁用所有沙盒，完全访问权限

#### 权限策略


1. **untrusted**: 运行不受信任的命令前提示用户
2. **on-failure**: 沙盒中命令失败时请求权限在沙盒外重试
3. **on-request**: 模型决定何时申请权限
4. **never**: 从不提示用户，自动尝试解决方案

### 常用沙盒和权限组合

| 使用场景 | 命令标志 | 效果  |
|------|------|-----|
| 安全的只读浏览 | `--sandbox read-only --ask-for-approval on-request` | 只能读取文件和回答问题，编辑/命令/网络需要批准 |
| 只读非交互(CI) | `--sandbox read-only --ask-for-approval never` | 只读访问，从不升级权限 |
| 允许编辑仓库，风险时询问 | `--sandbox workspace-write --ask-for-approval on-request` | 可在工作区内读/写/运行命令，工作区外或网络需要批准 |
| 自动模式 | `--full-auto` | 等同于`--sandbox workspace-write` + `--ask-for-approval on-failure` |
| YOLO模式(不推荐) | `--dangerously-bypass-approvals-and-sandbox` | 无沙盒，无提示 |

### 配置文件设置

```toml
# 权限模式
approval_policy = "untrusted"
sandbox_mode = "read-only"

# 全自动模式
approval_policy = "on-request"
sandbox_mode = "workspace-write"

# 工作区写入模式的可选设置
[sandbox_workspace_write]
network_access = true  # 允许网络访问
```

### 配置文件预设

```toml
[profiles.full_auto]
approval_policy = "on-request"
sandbox_mode = "workspace-write"

[profiles.readonly_quiet]
approval_policy = "never"
sandbox_mode = "read-only"
```

### 平台特定的沙盒实现

* **macOS 12+**: 使用Apple Seatbelt，通过`sandbox-exec`执行命令
* **Linux**: 使用Landlock/seccomp API组合实现沙盒配置

### 沙盒测试

```bash
# macOS沙盒测试
codex debug seatbelt [--full-auto] [COMMAND]...

# Linux沙盒测试  
codex debug landlock [--full-auto] [COMMAND]...
```

## 配置管理

### 配置层级和优先级

配置值可以在多个层级设置，优先级从高到低：


1. 命令行参数，如`--model o3`
2. 配置文件中的profile设置，通过`--profile`指定
3. `config.toml`中的条目，如`model = "o3"`
4. Codex CLI默认值（默认为`gpt-5`）

### 配置文件位置

配置文件位于`$CODEX_HOME/config.toml`，其中`CODEX_HOME`默认为`~/.codex`。

### 配置方法

#### 命令行配置

```bash
# 特定配置标志
codex --model o3

# 通用配置标志
codex --config model="o3"
codex --config model_providers.openai.wire_api="chat"

# TOML格式值
codex --config shell_environment_policy.include_only='["PATH", "HOME", "USER"]'
```

### 核心配置选项

#### 模型配置

```toml
# 基本模型设置
model = "o3"  # 覆盖默认的"gpt-5"
model_provider = "openai"

# 模型推理配置（支持推理的模型）
model_reasoning_effort = "high"      # minimal/low/medium/high
model_reasoning_summary = "detailed" # auto/concise/detailed/none
model_verbosity = "low"              # low/medium/high (仅GPT-5系列)
```

#### 模型提供商配置

```toml
[model_providers.openai-chat-completions]
name = "OpenAI using Chat Completions"
base_url = "https://api.openai.com/v1"
env_key = "OPENAI_API_KEY"
wire_api = "chat"  # chat 或 responses

# 网络调优设置
request_max_retries = 4            # HTTP请求重试次数
stream_max_retries = 10            # SSE流重试次数
stream_idle_timeout_ms = 300000    # 5分钟空闲超时

# 额外的HTTP头
http_headers = { "X-Example-Header" = "example-value" }
env_http_headers = { "X-Example-Features" = "EXAMPLE_FEATURES" }
```

#### 第三方提供商示例

```toml
# Ollama本地部署
[model_providers.ollama]
name = "Ollama"
base_url = "http://localhost:11434/v1"

# Mistral
[model_providers.mistral]
name = "Mistral"
base_url = "https://api.mistral.ai/v1"
env_key = "MISTRAL_API_KEY"

# Azure OpenAI
[model_providers.azure]
name = "Azure"
base_url = "https://YOUR_PROJECT_NAME.openai.azure.com/openai"
env_key = "AZURE_OPENAI_API_KEY"
query_params = { api-version = "2025-04-01-preview" }
```

#### Profile配置

```toml
# 默认设置
model = "o3"
approval_policy = "untrusted"
profile = "o3"  # 默认profile

# Profile定义
[profiles.o3]
model = "o3"
model_provider = "openai"
approval_policy = "never"
model_reasoning_effort = "high"
model_reasoning_summary = "detailed"

[profiles.gpt3]
model = "gpt-3.5-turbo"
model_provider = "openai-chat-completions"

[profiles.zdr]
model = "o3"
model_provider = "openai"
approval_policy = "on-failure"
```

#### 环境变量策略

```toml
[shell_environment_policy]
inherit = "core"  # all/core/none
ignore_default_excludes = false
exclude = ["AWS_*", "AZURE_*"]
set = { CI = "1" }
include_only = ["PATH", "HOME"]
```

#### 其他重要配置

```toml
# 历史记录
[history]
persistence = "none"  # save-all/none

# 文件编辑器设置
file_opener = "vscode"  # vscode/vscode-insiders/windsurf/cursor/none

# 通知设置
notify = ["python3", "/path/to/notify.py"]

# 推理显示设置
hide_agent_reasoning = true      # 隐藏推理事件
show_raw_agent_reasoning = true  # 显示原始推理内容

# 项目文档设置
project_doc_max_bytes = 32768  # AGENTS.md最大字节数

# Web搜索工具
[tools]
web_search = true  # 启用web搜索工具
```

### 配置参考表

| 配置键 | 类型/值 | 说明  |
|-----|------|-----|
| `model` | string | 使用的模型 (如 `gpt-5`) |
| `model_provider` | string | 提供商ID (默认: `openai`) |
| `approval_policy` | `untrusted`/`on-failure`/`on-request`/`never` | 批准提示时机 |
| `sandbox_mode` | `read-only`/`workspace-write`/`danger-full-access` | 沙盒策略 |
| `model_reasoning_effort` | `minimal`/`low`/`medium`/`high` | 推理强度 |
| `model_reasoning_summary` | `auto`/`concise`/`detailed`/`none` | 推理摘要 |
| `hide_agent_reasoning` | boolean | 隐藏模型推理事件 |
| `file_opener` | string | 文件超链接的URI方案 |

## 高级功能

### 非交互式/CI模式

#### GitHub Actions示例

```yaml
- name: 通过Codex更新变更日志
  run: |
    npm install -g @openai/codex
    codex login --api-key "${{ secrets.OPENAI_KEY }}"
    codex exec --full-auto "为下一个版本更新CHANGELOG"
```

#### 恢复非交互式会话

```bash
# 恢复最近会话并运行新提示
codex exec "发布草稿变更日志" resume --last

# 通过stdin传递提示
echo "发布草稿变更日志" | codex exec resume --last

# 按ID恢复特定会话
codex exec resume 7f9f9a2e-1b3c-4c7a-9b0e-123456789abc "继续任务"
```

### 追踪和详细日志

Codex使用Rust的`RUST_LOG`环境变量配置日志行为：

```bash
# TUI模式默认设置
RUST_LOG=codex_core=info,codex_tui=info

# 监控日志文件
tail -F ~/.codex/log/codex-tui.log

# 非交互式模式默认设置
RUST_LOG=error  # 消息直接打印，无需监控单独文件
```

### AGENTS.md内存系统

Codex会查找以下位置的`AGENTS.md`文件并自上而下合并：


1. `~/.codex/AGENTS.md` - 个人全局指导
2. 仓库根目录的`AGENTS.md` - 共享项目说明
3. 当前工作目录的`AGENTS.md` - 子文件夹/功能特定说明

## MCP协议集成

### 作为MCP客户端

在`~/.codex/config.toml`中定义MCP服务器：

```toml
[mcp_servers.server-name]
command = "npx"
args = ["-y", "mcp-server"]
env = { "API_KEY" = "value" }
startup_timeout_ms = 20_000  # 可选：覆盖默认10秒启动超时
```

### 作为MCP服务器

#### 启动MCP服务器

```bash
# 使用MCP检查器启动
npx @modelcontextprotocol/inspector codex mcp
```

#### 可用工具

`**codex**`**工具** - 运行Codex会话：

| 属性  | 类型  | 描述  |
|-----|-----|-----|
| `prompt` (必需) | string | 启动对话的初始用户提示 |
| `approval-policy` | string | 权限策略: `untrusted`/`on-failure`/`never` |
| `base-instructions` | string | 替代默认指令集 |
| `config` | object | 覆盖`config.toml`的配置设置 |
| `cwd` | string | 会话工作目录 |
| `model` | string | 模型名称覆盖 |
| `sandbox` | string | 沙盒模式 |

`**codex-reply**`**工具** - 继续会话：

| 属性  | 类型  | 描述  |
|-----|-----|-----|
| `prompt` (必需) | string | 继续对话的用户提示 |
| `conversationId` (必需) | string | 要继续的对话ID |

#### 使用示例

使用以下设置构建井字游戏：

* **approval-policy**: never
* **prompt**: 使用HTML、Javascript和CSS实现井字游戏。将游戏写在名为index.html的单个文件中。
* **sandbox**: workspace-write

> **提示**: Codex通常需要几分钟运行。调整MCP检查器的请求和总超时时间为600000ms（10分钟）。

## 故障排除和调试

### 日志配置

```bash
# 设置详细日志级别
export RUST_LOG=debug

# 查看实时日志
tail -f ~/.codex/log/codex-tui.log
```

### 常见问题

#### 沙盒问题

* 在Docker环境中，如果不支持Landlock/seccomp API，使用`--sandbox danger-full-access`
* 在旧Linux内核或Windows上，可能需要禁用沙盒

#### 网络问题

* 检查环境变量中的API密钥设置
* 确认网络访问权限配置

#### 配置问题

* 验证`~/.codex/config.toml`语法
* 检查配置优先级设置

### 调试命令

```bash
# 测试沙盒行为
codex debug seatbelt [COMMAND]   # macOS
codex debug landlock [COMMAND]   # Linux

# 检查配置
codex --help
codex config --help
```


---

这个手册涵盖了Codex CLI的所有主要功能和配置选项，从基本使用到高级功能，帮助用户充分利用这个强大的AI辅助编程工具。