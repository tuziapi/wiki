# Happy Coder - 手机远程控制Claude Code/codex

# Happy Coder - 手机远程控制 Claude Code/codex

通过 Happy Coder，可以用手机远程控制电脑上的 Claude Code 或 OpenAI Codex。

## 安装

### 电脑端


1. 安装 AI 编程工具（二选一）：

```bash
# Claude Code
npm install -g @anthropic-ai/claude-code

# OpenAI Codex
npm install -g @openai/codex
```


2. 先运行一次完成授权：

```bash
claude  # 或 codex
```


3. 安装 Happy Coder：

```bash
npm install -g happy-coder
```


4. 启动服务：

```bash
happy        # 使用 Claude
happy codex  # 使用 Codex
```

启动后会显示二维码和配对链接。

### 手机端 (安卓/苹果)

**安卓端**


1. 从 Google Play 下载 Happy Coder
2. 扫描电脑上的二维码，或复制配对链接到 App 中连接

**苹果端**

自备苹果商店外区id


1. 苹果商店下载 Happy: Codex & Claude Code APP
2.  扫描电脑上的二维码，或复制配对链接到 App 中连接

## 防掉线设置

### Windows


1. 设置 -> 系统 -> 电源和睡眠 -> 睡眠改为"从不"
2. 笔记本：控制面板 -> 电源选项 -> 关闭笔记本盖的功能 -> 接通电源时选"不采取任何操作"
3. 可选：安装 PowerToys，开启 Awake 功能

### 出门前


1. 运行 `happy` 或 `happy codex`
2. 按 Win + L 锁屏
3. 保持电源连接

## 功能

* 支持 Plan / Edit / Danger 模式切换
* 原生聊天界面，非远程桌面
* 低延迟，弱网络也能用