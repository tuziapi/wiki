# Codex 官方版本配置教程（Codex 订阅版）

# Codex 官方版本配置教程（Codex 订阅版）

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

将 `~/.codex/config.toml` 中的配置改成下面这份：

```toml
profile = "codex"

[model_providers.codex]
name = "codex"
base_url = "https://api.tu-zi.com/coding"
wire_api = "responses"
env_key = "CODEX_API_KEY"

[profiles.codex]
model_provider = "codex"
model = "gpt-5.5"
model_reasoning_effort = "medium"
approval_policy = "on-request"
```

#### B.2 设置环境变量

在 Shell （命令窗口）中导入从订单中获取的 API Key，Mac/Windows 可能不同，可以问下 AI 如何配置（我的操作系统是\*\*\*，我需要配置永久环境变量 `CODEX_API_KEY="你的Key字符串"`，请协助我）：

```bash
# 到此页面获取 API Key
# https://store.tu-zi.com

export CODEX_API_KEY="你的Key字符串"
```

 ![](https://wiki.tu-zi.com/api/files.get?sig=eyJhbGciOiJIUzI1NiIsInR5cCI6IkpXVCJ9.eyJrZXkiOiJ1cGxvYWRzLzA0MTA4NzY3LTk1YjgtNDYzMi05YWFmLTgwNzgwZjIwMmFkMi8xY2FhNTY1Ny1iOTE2LTQyMzQtYjhjMC0zYTAxMzlhNGZiMWQvaW1hZ2UucG5nIiwidHlwZSI6ImF0dGFjaG1lbnQiLCJpYXQiOjE3ODA0NTQ5NTgsImV4cCI6MTc4MDQ1ODU1OH0.N7-JxB5xMOC2nlxbansfuo7WY8FLLDT4yL1R2dRP1CQ " =829x400")

#### B.3 启动官方 Codex

直接运行官方客户端，使用 `codex` 配置档：

```bash
codex
```

> **提示：** 如你在 `config.toml` 中未将 `profile` 设为 `codex`，也可通过命令行切换：`codex --profile codex`。

> **说明：** 采用官方 Codex + API Key 方式通常无需浏览器授权，直接使用即可。


---

**故障排除**

如果安装或启动过程中遇到问题，可以尝试以下方案：

* **权限错误：** 使用 sudo（macOS/Linux）或以管理员身份运行（Windows）
* **找不到命令：** 重启终端或检查 PATH 环境变量
* **连接问题：** 检查防火墙、代理或网络设置

> 💡 **使用说明：** 无论使用方案 A 或方案 B，Codex 都会使用你的 gaccode 账户积分，且与 Claude Code 共享扣费额度。