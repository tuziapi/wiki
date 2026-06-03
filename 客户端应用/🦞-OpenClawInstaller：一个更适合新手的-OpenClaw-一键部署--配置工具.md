# 🦞 OpenClawInstaller：一个更适合新手的 OpenClaw 一键部署 / 配置工具

![](https://wiki.tu-zi.com/api/files.get?sig=eyJhbGciOiJIUzI1NiIsInR5cCI6IkpXVCJ9.eyJrZXkiOiJ1cGxvYWRzL2FjNjBlNmRhLTdjYTQtNDdjMS04ZTQxLTAxMDUyMDAwNzM3NS81YWFhOWNkMC02MTdjLTQ5OTItYTk4Yi0xMmRiYzJiN2U5MWYvaW1hZ2UucG5nIiwidHlwZSI6ImF0dGFjaG1lbnQiLCJpYXQiOjE3ODA0NTQ4NDcsImV4cCI6MTc4MDQ1ODQ0N30.OMOZlsimuAl-mrNCIM_MYQHiafo9pW7yJ4UKZ77JKuU " =526x356")

如果你想体验 OpenClaw，但不想自己从环境、模型、服务和消息渠道开始一点点配置，可以试试这个项目：

> 项目地址： <https://github.com/cwj526/OpenClawInstaller>

它基于开源 OpenClaw 做了一层更适合新手的一键安装和配置流程，重点是：

* 支持一键安装 OpenClaw
* 默认引导接入 **[兔子 API](https://api.tu-zi.com/)**
* 可通过菜单继续配置模型和消息渠道
* 支持飞书、Telegram、Discord、WhatsApp 等渠道

  ![](https://wiki.tu-zi.com/api/files.get?sig=eyJhbGciOiJIUzI1NiIsInR5cCI6IkpXVCJ9.eyJrZXkiOiJ1cGxvYWRzL2FjNjBlNmRhLTdjYTQtNDdjMS04ZTQxLTAxMDUyMDAwNzM3NS8yYmQ3NWJkOC1kZjM2LTQ0ZGEtOTFiZC1mNTk3ODk4MWFkMDIvaW1hZ2UucG5nIiwidHlwZSI6ImF0dGFjaG1lbnQiLCJpYXQiOjE3ODA0NTQ4NDcsImV4cCI6MTc4MDQ1ODQ0N30.Q4pCFFtpneh4O6sBvIHiK2wCYW_OS3kURICUlhSNa8E " =522x299")

它更适合这几类人：

* 第一次接触 OpenClaw 的新用户
* 想尽快跑通 OpenClaw 的个人用户
* 已经跑通 OpenClaw，想直接接入兔子 API 的用户
* 想把 OpenClaw 接到飞书或聊天软件里使用的人

## 一、安装前准备

根据 README，推荐环境如下：

| 项目  | 要求  |
|-----|-----|
| 操作系统 | macOS 12+ / Ubuntu 20.04+ / Debian 11+ / CentOS 8+ |
| Node.js | v22 或更高版本（如果 Node 版本太低，建议先升级） |
| 内存  | 最低 2GB，推荐 4GB+ |
| 磁盘空间 | 最低 1GB |

## 二、最快安装 / 配置方式

直接运行一键安装脚本：

```bash
curl -fsSL https://raw.githubusercontent.com/cwj526/OpenClawInstaller/main/install.sh | bash
```

 ![](https://wiki.tu-zi.com/api/files.get?sig=eyJhbGciOiJIUzI1NiIsInR5cCI6IkpXVCJ9.eyJrZXkiOiJ1cGxvYWRzL2FjNjBlNmRhLTdjYTQtNDdjMS04ZTQxLTAxMDUyMDAwNzM3NS8wZDYxN2FmOC01MTY2LTRjN2EtOTFkZi02YjkwOTFhY2EzOWYvaW1hZ2UucG5nIiwidHlwZSI6ImF0dGFjaG1lbnQiLCJpYXQiOjE3ODA0NTQ4NDcsImV4cCI6MTc4MDQ1ODQ0N30.bqCavH6KgpudNDLUsYqrhTFn90bXdo4mp1vfuDSRV74 " =704x283")

安装脚本会自动完成：


1. 检测环境并安装依赖
2. 安装 OpenClaw
3. 引导完成基础配置
4. 测试 API 连接
5. 选择安装 [tuzi-skills](https://github.com/tuziapi/tuzi-skills) AI 内容生成技能集
6. 启动 OpenClaw 服务

如果你不想折腾太多细节，这就是最推荐的方式。

* 若检测到本机已经安装完成，可以选择：1. 安装最新版本 2. 只修改配置，接入tuzi api

 ![](https://wiki.tu-zi.com/api/files.get?sig=eyJhbGciOiJIUzI1NiIsInR5cCI6IkpXVCJ9.eyJrZXkiOiJ1cGxvYWRzL2FjNjBlNmRhLTdjYTQtNDdjMS04ZTQxLTAxMDUyMDAwNzM3NS9hM2E1NzZkNy04MjIyLTRiMDItOWM4Ni02Nzk5YTBhMzg4NjUvaW1hZ2UucG5nIiwidHlwZSI6ImF0dGFjaG1lbnQiLCJpYXQiOjE3ODA0NTQ4NDcsImV4cCI6MTc4MDQ1ODQ0N30.02VrGgkPJCAc8DTJJe_ko3ijcS7pATTjM7T3wKgxGVs " =685x378")

## 三、如何获取兔子 API

安装过程中或安装完成后，可以进入模型配置流程。

> 获取 api-key 视频教程：<https://www.bilibili.com/video/BV1k4PqzPEKz/ >

核心步骤是：


1. 进入兔子 API Token 地址： <https://api.tu-zi.com/token，创建令牌>

   ![](https://wiki.tu-zi.com/api/files.get?sig=eyJhbGciOiJIUzI1NiIsInR5cCI6IkpXVCJ9.eyJrZXkiOiJ1cGxvYWRzL2FjNjBlNmRhLTdjYTQtNDdjMS04ZTQxLTAxMDUyMDAwNzM3NS9hMjg3Nzc4NS04ZTRiLTRkOTgtYWFjNS1iODhjMjM1ODEwZGYvaW1hZ2UucG5nIiwidHlwZSI6ImF0dGFjaG1lbnQiLCJpYXQiOjE3ODA0NTQ4NDcsImV4cCI6MTc4MDQ1ODQ0N30.K_usNIXm-loNA8bkPGVgEGs2Tt17LqNdn2fIYeGV2WI " =642x199")
2. 选择分组：`Claude-Code` 或 `Codex`

   ![](https://wiki.tu-zi.com/api/files.get?sig=eyJhbGciOiJIUzI1NiIsInR5cCI6IkpXVCJ9.eyJrZXkiOiJ1cGxvYWRzL2FjNjBlNmRhLTdjYTQtNDdjMS04ZTQxLTAxMDUyMDAwNzM3NS8zMzg5Yjg1Yi01YmZkLTQ3MjEtYjlhZS00OThiMGEwN2QyNTUvaW1hZ2UucG5nIiwidHlwZSI6ImF0dGFjaG1lbnQiLCJpYXQiOjE3ODA0NTQ4NDcsImV4cCI6MTc4MDQ1ODQ0N30.QH6nzIq4zwwu3yb2Q5-ylWRFn_eMAGrnAfrEQ4eJcu0 " =385x538")
3. 输入对应分组的 API Key
4. 从预置列表里选择模型
5. 配置自动写入 `~/.openclaw/openclaw.json`


需要注意：

> `Claude-Code` 和 `Codex` 的 Key 不能混用。

## 四、选择安装 tuzi-skills

tuzi-skills 是一组实用扩展技能，主要用于增强内容生成与处理能力。 适合在 OpenClaw 中**扩展生图**、**视频生成**、**封面制作**和文案处理等场景，也可用于文案润色、Markdown 处理等常见内容创作场景。

> 仓库地址：<https://github.com/tuziapi/tuzi-skills>

 ![](https://wiki.tu-zi.com/api/files.get?sig=eyJhbGciOiJIUzI1NiIsInR5cCI6IkpXVCJ9.eyJrZXkiOiJ1cGxvYWRzL2FjNjBlNmRhLTdjYTQtNDdjMS04ZTQxLTAxMDUyMDAwNzM3NS80MDc2MTA4Yy1lMTk4LTRjMzEtOTMzMS1iYmZkYTcxZTdjMjYvaW1hZ2UucG5nIiwidHlwZSI6ImF0dGFjaG1lbnQiLCJpYXQiOjE3ODA0NTQ4NDcsImV4cCI6MTc4MDQ1ODQ0N30.grriaN5FXvZWDgkndxyePEDE6HZVJYJYSnJWubTutsM " =556x446")

## 五、安装完成后怎么运行

安装完成后，建议先检查服务状态：

```bash
openclaw gateway status
```

如果没有启动，可以手动执行：

```bash
openclaw gateway start
```

查看日志：

```bash
openclaw logs --follow
```

如果你想继续调整配置，可以打开配置菜单：

```bash
bash ~/.openclaw/config-menu.sh
```

## 六、接入消息渠道

这个项目支持多种消息渠道，包括：

* 飞书
* Telegram
* Discord
* WhatsApp
* Slack
* 微信
* iMessage（仅 macOS）

如果你是新手，建议先只接一个渠道，优先选自己最常用的，比如飞书。

 ![](https://wiki.tu-zi.com/api/files.get?sig=eyJhbGciOiJIUzI1NiIsInR5cCI6IkpXVCJ9.eyJrZXkiOiJ1cGxvYWRzL2FjNjBlNmRhLTdjYTQtNDdjMS04ZTQxLTAxMDUyMDAwNzM3NS80YjA4Y2E2NS0zMDA3LTQxMzctODIzZC1lMTFlYTIyZmYyNDgvaW1hZ2UucG5nIiwidHlwZSI6ImF0dGFjaG1lbnQiLCJpYXQiOjE3ODA0NTQ4NDcsImV4cCI6MTc4MDQ1ODQ0N30.AVjDbAtU1GWl0D5zrDNp68ZhnnSDuEMOqGjmY0wEvws " =522x391")

## 七、飞书怎么配

README 里也给了飞书配置说明，核心步骤是：


1. 去[飞书开放平](https://open.feishu.cn/app)台创建企业自建应用
2. 添加机器人能力
3. 获取 App ID 和 App Secret

   ![](https://wiki.tu-zi.com/api/files.get?sig=eyJhbGciOiJIUzI1NiIsInR5cCI6IkpXVCJ9.eyJrZXkiOiJ1cGxvYWRzL2FjNjBlNmRhLTdjYTQtNDdjMS04ZTQxLTAxMDUyMDAwNzM3NS80NzdkNjgzYy1kMDcyLTQ2YjEtODE0Yy0wODVkNjg4YTcxNWEvaW1hZ2UucG5nIiwidHlwZSI6ImF0dGFjaG1lbnQiLCJpYXQiOjE3ODA0NTQ4NDcsImV4cCI6MTc4MDQ1ODQ0N30.XcAnMRlfAhw-PE-svY6jsq_29yo9jYPTjTZ6bFuECFw " =728x265")
4. 添加必要权限
5. 发布应用
6. 在配置菜单里选择飞书并填入凭据
7. 开启长连接事件订阅
8. 把机器人加到群里测试

飞书这条线的优点是：

* 不需要公网服务器
* 支持长连接
* 个人账号也可以配置

## 八、常用命令

```bash
openclaw gateway start
openclaw gateway stop
openclaw gateway restart
openclaw gateway status
openclaw logs
openclaw logs --follow
openclaw doctor
```

这些命令基本够你完成启动、排查和日常维护。

## 九、总结

OpenClawInstaller 不是替代 OpenClaw，而是把 OpenClaw 的安装和初始配置过程做得更简单。

如果你想更快完成这件事：

* 装 OpenClaw
* 接兔子 API
* 配置 tuzi-skills
* 启动服务
* 接入飞书或其他消息渠道

那这个项目很适合作为入口。

> 项目地址： <https://github.com/cwj526/OpenClawInstaller>