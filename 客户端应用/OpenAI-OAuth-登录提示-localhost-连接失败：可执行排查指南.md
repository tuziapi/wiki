# OpenAI OAuth 登录提示 localhost 连接失败：可执行排查指南

> 适用：macOS / Linux
>
> 目标：按顺序执行命令，修复 `localhost` 回调失败问题。


---

## 0. 你要做什么（先看这个）


1. 打开终端
2. 按下面 **步骤 1 → 5** 逐段复制执行
3. 再次尝试 OpenAI OAuth 登录
4. 如果仍失败，把最后的"最终检查输出"发给你的AI助手


---

## 1) 清理代理影响（最常见原因）

```bash
export NO_PROXY=localhost,127.0.0.1,::1
export no_proxy=localhost,127.0.0.1,::1

unset HTTP_PROXY HTTPS_PROXY ALL_PROXY http_proxy https_proxy all_proxy

echo "== proxy env =="
env | grep -Ei 'http_proxy|https_proxy|all_proxy|no_proxy'
```

**说明：**

* 这会让 `localhost` 不走代理。
* 若你开了 Clash/Surge/系统代理，也要确认 localhost 直连。


---

## 2) 检查 1455 端口是否被占用

```bash
echo "== port 1455 listener =="
lsof -nP -iTCP:1455 -sTCP:LISTEN || echo "no listener on 1455"
```

如果看到有进程占用 1455，执行：

```bash
PID=$(lsof -tiTCP:1455 -sTCP:LISTEN | head -n1)
if [ -n "$PID" ]; then
  echo "killing PID=$PID on 1455"
  kill -9 "$PID"
else
  echo "1455 is free"
fi
```


---

## 3) 检查 localhost 是否正常

```bash
echo "== localhost resolve =="
ping -c 1 localhost || true
grep -n "localhost" /etc/hosts || true
```

正常情况下，`/etc/hosts` 里应包含类似：

```text
127.0.0.1 localhost
```


---

## 4) 清理旧 OAuth 缓存（防止脏状态）

```bash
AUTH_FILE="$HOME/.openclaw/agents/main/agent/auth-profiles.json"
mkdir -p "$HOME/.openclaw/agents/main/agent"

if [ -f "$AUTH_FILE" ]; then
  cp "$AUTH_FILE" "$AUTH_FILE.bak.$(date +%Y%m%d-%H%M%S)"
  rm -f "$AUTH_FILE"
  echo "old auth file removed (backup created)"
else
  echo "auth file not found, skip remove"
fi
```


---

## 5) 重启 OpenClaw 网关并重试登录

```bash
openclaw gateway restart
sleep 2
openclaw gateway status
```

然后在**同一台机器**重新发起 OAuth 登录。

> 注意：如果你是 SSH 到远程机器操作，但浏览器在本机，容易失败。请确保回调和登录流程在同一机器，或正确做端口转发。


---

## 6) 仍失败？执行"最终检查"

```bash
echo "=== FINAL CHECK ==="
openclaw gateway status
lsof -nP -iTCP:1455 -sTCP:LISTEN || echo "no listener on 1455"
env | grep -Ei 'proxy|no_proxy'
```

把以上输出完整发给你的AI助手/管理员即可定位问题。


---

## 常见结论（快速判断）

* **1455 被占用** → 杀掉占用进程后重试。
* **localhost 走了代理** → 设置 `NO_PROXY` 并关闭全局代理后重试。
* **旧 token 缓存损坏** → 删除 `auth-profiles.json` 后重登。
* **远程登录场景** → 改为同机登录或配置 SSH 端口转发。


---