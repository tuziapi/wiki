# Codex 官方版本配置教程

### 官方 Codex 客户端 +  API

适合希望使用官方 Codex 客户端的同学，通过配置自定义模型提供商对接 gaccode/兔子 API。

```bash
#官方客户端安装
# 全局安装
npm i -g @openai/codex

# 验证安装
codex --version
```

#### B.1 配置 `~/.codex/config.toml`

新增 `gac/兔子` 配置并将默认 `profile` 指向它：

```toml

profile = "gac"
#profile = "tuzi"
#profile = "codex"


[model_providers.gac]
#[model_providers.tuzi]
#[model_providers.codex]
name = "gac"
#name = "tuzi"
#name = "codex"
base_url = "https://gaccode.com/codex/v1"
#base_url = "https://api.tu-zi.com"
#base_url = "https://api.tu-zi.com/coding"
wire_api = "responses"
env_key = "CODEX_API_KEY"

[profiles.gac]
#[profiles.tuzi]
#[profiles.codex]
model_provider = "gac"
#name = "tuzi"
#name = "codex"
model = "gpt-5.5"
model_reasoning_effort = "medium"
approval_policy = "on-request"
```

#### B.2 设置环境变量

在 Shell （命令窗口）中导入从 订单中 获取的 API Key，Mac/Windows 可能不同，可以问下 AI 如何配置（我的操作系统是\*\*\*，我需要配置永久环境变量CODEX_API_KEY="你的Key字符串"，请协助我）：

```bash
# 到此页面获取 API Key
# https://gaccode.com/api-keys
# https://api.tu-zi.com/token
# https://store.tu-zi.com

export CODEX_API_KEY="你的Key字符串"
```

#### B.3 启动官方 Codex

直接运行官方客户端，使用 `gac` 配置档：

```bash
codex
```

> **提示：** 如你在 `config.toml` 中未将 `profile` 设为 `gac`，也可通过命令行切换：`codex --profile gac`。

> **说明：** 采用官方 Codex + API Key 方式通常无需浏览器授权，直接使用即可。


---

**故障排除**

如果安装或启动过程中遇到问题，可以尝试以下方案：

* **权限错误：** 使用 sudo（macOS/Linux）或以管理员身份运行（Windows）
* **找不到命令：** 重启终端或检查 PATH 环境变量
* **连接问题：** 检查防火墙、代理或网络设置

> 💡 **使用说明：** 无论使用方案A或方案B，Codex 都会使用你的 gaccode 账户积分，且与 Claude Code 共享扣费额度。