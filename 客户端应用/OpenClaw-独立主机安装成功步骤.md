# OpenClaw 独立主机安装成功步骤

# OpenClaw 独立主机安装成功步骤

作者：LQ   联系方式：[106562267@qq.com](mailto:106562267@qq.com)

## 1. 目标

本文档基于本次会话中的真实安装与排障过程，总结一套在独立主机上成功安装并验证 `OpenClaw` 可运行的最短路径。

适用场景：

* 一台独立主机本地安装 `OpenClaw`
* 通过另外一台 MacBook `SSH` 远程连接主机进行安装与使用
* 主机无图形界面，需要通过端口转发访问 `dashboard`

## 2. 成功判定标准

本次会话中，以下状态可视为安装主体成功：

* 可以和`OpenClaw`聊天互动
  * 在本地连接远程主机的`Tui`

 ![TUI 已正常回复截图](https://wiki.tu-zi.com/api/files.get?sig=eyJhbGciOiJIUzI1NiIsInR5cCI6IkpXVCJ9.eyJrZXkiOiJ1cGxvYWRzLzA0MTA4NzY3LTk1YjgtNDYzMi05YWFmLTgwNzgwZjIwMmFkMi85ZTE5YjI3MS1jNWZkLTQ1MmMtOGRjMC02MjJiY2U0ZmVlN2UvdHVpLWNoYXQtc3VjY2Vzcy5wbmciLCJ0eXBlIjoiYXR0YWNobWVudCIsImlhdCI6MTc4MDQ1NDg0OSwiZXhwIjoxNzgwNDU4NDQ5fQ.us-ta4AHWXBKg24tegVKrDvUksazuzBHif8vK1uZ6Y8)

* `openclaw dashboard` 能输出本地控制台

 ![Dashboard 概览正常截图](https://wiki.tu-zi.com/api/files.get?sig=eyJhbGciOiJIUzI1NiIsInR5cCI6IkpXVCJ9.eyJrZXkiOiJ1cGxvYWRzLzA0MTA4NzY3LTk1YjgtNDYzMi05YWFmLTgwNzgwZjIwMmFkMi8xNDVjZGE5NS00ZGQzLTQ5NzItYjY3YS1jODExZjViZTE4MjQvZGFzaGJvYXJkLW92ZXJ2aWV3LXN1Y2Nlc3MucG5nIiwidHlwZSI6ImF0dGFjaG1lbnQiLCJpYXQiOjE3ODA0NTQ4NDksImV4cCI6MTc4MDQ1ODQ0OX0.n_JamAQxxP2HluDeHG11hHL58XJUuBIY7v40T8rhehY)

## 3. 前置条件

建议先确认：

* 远程主机可正常联网
* 可以访问模型服务或相关 API
* 具备 `Node.js 22+`
* 远程主机可通过 `SSH` 登录

如果是 `macOS`，建议额外确认 `Xcode Command Line Tools` 已安装。

## 4. macOS 必要依赖

如果在 `npm install` 时出现如下报错：

```text
xcrun: error: invalid active developer path /Library/Developer/CommandLineTools
```

说明当前主机缺少或损坏了 `Xcode Command Line Tools`。

纯终端修复方式：


1. 先查看可安装版本：

```bash
softwareupdate --list
```


2. 安装较新的 `Command Line Tools` 版本，例如：

```bash
sudo softwareupdate --install "Command Line Tools for Xcode-14.3"
```


3. 安装完成后确认路径：

```bash
xcode-select -p
```


4. 如有需要，再执行：

```bash
sudo xcode-select --switch /Library/Developer/CommandLineTools
```

## 5. 安装 OpenClaw

在国内网络环境下，本次会话中验证过的可执行命令为：

```bash
npm install -g openclaw@latest --registry=https://registry.npmmirror.com
```

安装完成后执行：

```bash
openclaw onboard --install-daemon
```

## 6. 初始化向导建议

在初始化向导中，建议按以下方式选择：


1. 选择 `local` 模式
2. 使用默认工作区或指定稳定目录
3. 网关端口使用默认 `18789`
4. 网关绑定保持 `loopback`
5. 网关认证保持 `token`
6. 选择模型提供方并填写正确密钥（在`tuzi`后台配置以及获取）

> 核心就是按照提示一步步操作即可，一些skill或者channel可以延后配置，先让主流程跑起来

初始化向导示例截图：

 ![Onboarding 配置示例](https://wiki.tu-zi.com/api/files.get?sig=eyJhbGciOiJIUzI1NiIsInR5cCI6IkpXVCJ9.eyJrZXkiOiJ1cGxvYWRzLzA0MTA4NzY3LTk1YjgtNDYzMi05YWFmLTgwNzgwZjIwMmFkMi82YTRjNzI4MS05ZWQxLTQ2YWQtOWMxNy0wOGQ1NjlhYjBiNzUvb25ib2FyZGluZy1leGFtcGxlLnBuZyIsInR5cGUiOiJhdHRhY2htZW50IiwiaWF0IjoxNzgwNDU0ODQ5LCJleHAiOjE3ODA0NTg0NDl9.lvMLGRLDW-RR7c6QSVArLD5QdA5lOyKdqgcowPmHJwg)

## 7. 独立主机上的验证步骤

安装完成后，依次执行：

```bash
openclaw doctor
openclaw status
openclaw tui
```

成功特征：

* `doctor` 无关键阻塞错误
* `status` 显示网关正常
* `tui` 成功进入交互界面

在本次会话中，安装成功时看到的关键特征为：

* 顶部显示 `openclaw tui`
* 网关地址为 `ws://127.0.0.1:18789`
* 状态栏显示 `connected | idle`

## 8. 远程主机访问 dashboard

如果 `OpenClaw` 部署在远程独立主机上，执行：

```bash
openclaw dashboard
```

看到如下提示时，不是报错：

* `Dashboard URL: http://127.0.0.1:18789/...`
* `No GUI detected. Open from your computer:`

这表示：

* 远程主机上的控制台已经启动
* 需要通过本机端口转发来访问

本机执行：

```bash
ssh -N -L 18789:127.0.0.1:18789 用户名@远程主机IP
```

然后在本机浏览器打开：

```text
http://localhost:18789/
```

或带 token 的完整地址。

## 9. 本次会话中真正踩到的坑

### 9.1 `npm install` 很慢

解决方式：

```bash
npm install -g openclaw@latest --registry=https://registry.npmmirror.com
```

### 9.2 `xcrun: invalid active developer path`

根因：

* `macOS` 缺少 `Xcode Command Line Tools`

解决方式：

* 先通过 `softwareupdate` 安装 `Command Line Tools`

### 9.3 TUI 已连接但没有模型回复

结论：

* 安装主体大概率成功
* 更可能卡在自定义 provider 配置

本次会话中高风险项包括：

* `baseUrl: https://api.tu-zi.com`
* `api: openai-completions`这个api一定要个大模型提供的api名称匹配，一般在tui的初始化阶段可以自动选择，我之前就是这里搞错了，卡了很久
* `model id: codex`

**配置截图**

初始配置截图：

 ![初始配置截图](https://wiki.tu-zi.com/api/files.get?sig=eyJhbGciOiJIUzI1NiIsInR5cCI6IkpXVCJ9.eyJrZXkiOiJ1cGxvYWRzLzA0MTA4NzY3LTk1YjgtNDYzMi05YWFmLTgwNzgwZjIwMmFkMi80OWMzNjNhNS0xNDgzLTRkZDEtYmVkNS1mMjg3ZmQzOWM4NTIvcHJvdmlkZXItY29uZmlnLW9sZC5wbmciLCJ0eXBlIjoiYXR0YWNobWVudCIsImlhdCI6MTc4MDQ1NDg0OSwiZXhwIjoxNzgwNDU4NDQ5fQ.BGdLVXOmFZgOiJUKJFufkbi0sl5n5tj97H2edS_qUhs)

默认大模型的key也不能设置错误，斜杠前的是 provider 名称，后面的是大模型id，可通过`tuzi`官网的模型价格页面获取。

 ![修正后的配置截图](https://wiki.tu-zi.com/api/files.get?sig=eyJhbGciOiJIUzI1NiIsInR5cCI6IkpXVCJ9.eyJrZXkiOiJ1cGxvYWRzLzA0MTA4NzY3LTk1YjgtNDYzMi05YWFmLTgwNzgwZjIwMmFkMi9kMzQ0MDJiMi03NzYxLTQ1MDYtOTBjYS05Y2VlY2NhODMwY2IvcHJvdmlkZXItY29uZmlnLXVwZGF0ZWQucG5nIiwidHlwZSI6ImF0dGFjaG1lbnQiLCJpYXQiOjE3ODA0NTQ4NDksImV4cCI6MTc4MDQ1ODQ0OX0.Uk3B4K7Pjk6tiOIXyO3Cz99Hd8z6Ch1utdSTsBEMwkE)

## 10. 最小成功路径

如果只保留最关键步骤，可按以下顺序执行：


1. 安装 `Command Line Tools`
2. 执行：

```bash
npm install -g openclaw@latest --registry=https://registry.npmmirror.com
```


3. 执行：

```bash
openclaw onboard --install-daemon
```


4. 执行：

```bash
openclaw tui
```


5. 确认状态为：

* `connected | idle`


6. 如需网页控制台，执行：

```bash
openclaw dashboard
```


7. 若在远程主机上运行，则通过：

```bash
ssh -N -L 18789:127.0.0.1:18789 用户名@远程主机IP
```

在本机浏览器打开控制台。