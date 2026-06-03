# Codex 官方版本配置教程（兔子线路）

### 官方 Codex 客户端 +  兔子 API

```bash
#官方客户端安装
# 全局安装
npm i -g @openai/codex

# 验证安装
codex --version
```

#### B.1 配置 `~/.codex/config.toml`

新增 `tuzi` 配置并将默认 `model_provider` 指向它：

```toml
disable_response_storage = true
model_provider = "tuzi"
model = "gpt-5.5"
model_reasoning_effort = "high"

[model_providers.codex]
name = "codex"
base_url = "https://api.tu-zi.com/v1"
env_key = "TUZI_CODEX_API_KEY"
wire_api = "responses"
requires_openai_auth = true
```

#### B.2 设置环境变量

在 Shell （命令窗口）中导入从 订单中 获取的 API Key，Mac/Windows 可能不同，可以问下 AI 如何配置（我的操作系统是\*\*\*，我需要配置永久环境变量CODEX_API_KEY="你的Key字符串"，请协助我）：

```bash
# 到此页面获取 API Key
# https://api.tu-zi.com/token

export TUZI_CODEX_API_KEY="你的Key字符串"
```

#### B.3 启动官方 Codex

直接运行官方客户端，使用 `tuzi` 配置档：

```bash
codex
```

> **提示：** 如你在 `config.toml` 中未将 `model_provider` 设为 `tuzi`，也可通过命令行切换：`codex --model_provider tuzi`。




---

**故障排除**

如果安装或启动过程中遇到问题，可以尝试以下方案：

* **权限错误：** 使用 sudo（macOS/Linux）或以管理员身份运行（Windows）
* **找不到命令：** 重启终端或检查 PATH 环境变量
* **连接问题：** 检查防火墙、代理或网络设置
