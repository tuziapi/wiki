# gaccode 订阅接入 OpenClaw 完整教程：Claude Code 与 Codex 都能用

# gaccode 订阅接入 OpenClaw 完整教程：Claude Code 与 Codex 都能用

## 简介

这篇教程讲的是，已经购买了 **gaccode 订阅** 之后，怎么在 **OpenClaw** 里把它真正用起来。

很多人会把这几个概念混在一起：

* `gaccode`：我们这边的原生工具接入平台 / 月卡订阅平台
* `OpenClaw`：本地或服务器上运行的智能助手 / 多工具 Agent 框架
* `Claude Code`：Anthropic 体系的原生编程工具接入
* `Codex`：OpenAI 体系的原生编程工具接入

简单理解：

**gaccode 负责提供可用的接入能力，OpenClaw 负责把这些能力接到你的工作流里。**

如果你希望在 OpenClaw 里长期稳定使用 gaccode 订阅中的 **Claude Code** 和 **Codex**，这篇可以直接照着做。


---

## gaccode 是什么

gaccode 可以理解成一套 **原生工具接入平台 / 月卡订阅平台**。

它不是单纯卖一个官方账号，而是通过平台接入的方式，提供 Claude Code、Codex、Gemini 等原生工具能力。

和官方直连订阅相比，它更偏向：

* 免翻墙
* 接入方便
* 支持开票
* 一套订阅里可以覆盖多种原生工具能力
* 按月卡 + 积分消耗方式使用

所以在 OpenClaw 里配置 gaccode，通常不是去"登录一个单独账号"，而是把 **gateway / base url** 和 **API key** 配进去。


---

## 适用场景

这篇教程适合下面几类用户：

* 已经买了 gaccode 月卡，想在 OpenClaw 里接 Claude Code
* 已经买了 gaccode 月卡，想在 OpenClaw 里接 Codex
* 想把 OpenClaw 作为统一入口，在同一套系统里切换 Claude Code / Codex
* 不想折腾复杂网络，希望直接把订阅接进现有 OpenClaw 环境


---

## 前置条件

开始前，建议你先确认这几项：


1. 已经有可正常使用的 **OpenClaw** 环境
2. 已经购买并激活了 **gaccode 订阅**
3. 可以登录 `https://gaccode.com`
4. 能在 gaccode 后台拿到自己的 API Key
5. 知道自己是在本机部署 OpenClaw，还是部署在云服务器上

如果你还没安装 OpenClaw，可以先看这些文档：

* OpenClaw 配置总说明： <https://wiki.tu-zi.com/s/8c61a536-7a59-4410-a5e2-8dab3d041958/doc/openclaw-gVTr4tVhjI?q=openclaw>
* OpenClawInstaller（更适合新手）： <https://wiki.tu-zi.com/s/8c61a536-7a59-4410-a5e2-8dab3d041958/doc/openclawinstaller-openclaw-yXqo6dRAPz?q=openclaw>
* OpenClaw 独立主机安装成功步骤： <https://wiki.tu-zi.com/s/8c61a536-7a59-4410-a5e2-8dab3d041958/doc/openclaw-QxzIagj6yu>


---

## 核心配置思路

先说结论：

**gaccode / Claude Code / Codex 这类接入，在 OpenClaw 里通常统一走这个 gateway：**

```bash
https://gaccode.com/claudecode
```

获取 key 的位置通常在：

<https://gaccode.com/api-keys>

也就是说，你在 OpenClaw 里最常见的配置核心就是：

```bash
ANTHROPIC_BASE_URL=https://gaccode.com/claudecode
ANTHROPIC_API_KEY=你的_gaccode_key
```

对很多用户来说，只要先把这一组配置接通，Claude Code 就已经能跑起来了。

而 Codex 的思路则是：

* 先确认你的 gaccode 套餐包含 Codex 能力
* 再在 OpenClaw 或对应 agent 的模型配置里，把 Codex 模型加入进去
* 然后切换到 Codex 对应模型使用


---

## 第一步：登录 gaccode 后台并获取 Key

打开：

<https://gaccode.com/api-keys>

获取你的 gaccode key。

建议你确认两件事：


1. key 是当前可用状态
2. 订阅已经激活，且对应能力正常

如果你后面在 OpenClaw 里遇到 401、key not found、认证失败之类的问题，第一优先级就是回来检查这里。


---

## 第二步：先把 Claude Code 接进 OpenClaw

### 方式一：环境变量方式（最容易理解）

如果你是自己在服务器或本机终端里启动 OpenClaw，可以先用环境变量方式测试：

```bash
export ANTHROPIC_BASE_URL=https://gaccode.com/claudecode
export ANTHROPIC_API_KEY=你的_gaccode_key
```

然后再启动或重启 OpenClaw。

这样做的好处是：

* 简单直接
* 好排查
* 适合先验证连通性

### 方式二：写入 OpenClaw 配置

如果你希望长期稳定使用，建议把配置写入 OpenClaw 的正式配置或 agent 配置里，而不是每次手动 export。

不同 OpenClaw 版本 / 安装方式，配置落点可能会有区别，但核心字段含义不变：

* base url / gateway 指向 `https://gaccode.com/claudecode`
* api key 使用你在 gaccode 后台拿到的 key

如果你不确定自己当前 OpenClaw 配置写在哪个文件，建议优先参考你当前安装文档，或者让 OpenClaw 直接帮你检查现有配置结构。


---

## 第三步：验证 Claude Code 是否已经接通

配置完成后，可以用下面几种方式验证。

### 方法 1：看 OpenClaw 是否正常启动

如果启动阶段没有出现认证错误、模型初始化错误，说明基础配置大概率已经通了。

### 方法 2：发送一个简单请求测试

例如让 OpenClaw 执行一个轻量任务：

* 总结一段文本
* 写一个 hello world
* 改一个简单脚本

如果能正常返回结果，说明 Claude Code 通道已可用。

### 方法 3：遇到 Claude Code 很卡时，调整 gaccode 通道

如果能用，但体验偏卡，可以去 gaccode 后台：

<https://gaccode.com/configuration>

在后台尝试切换 Claude 通道，例如：

* `0.6`
* `高级渠道`
* `default`

当前口径下：

* `0.6` 和 `高级渠道` 都属于 Max 号池
* `default` 是自动路由

如果你更在意性价比，通常可以先试 `0.6`；如果你更在意稳定性和体验，可以试 `高级渠道`。


---

## 第四步：在 OpenClaw 里接入 Codex

Claude Code 接通之后，再做 Codex 会更顺。

更改地址为"https://gaccode.com/codex"即可


---

## Claude Code 与 Codex 的推荐使用方式

如果你希望在 OpenClaw 里把 gaccode 订阅用得更顺，建议按下面理解：

### Claude Code 更适合

* 日常主力编码
* 代码解释与重构
* 多轮上下文连续协作
* Agent 风格的任务编排

### Codex 更适合

* 明确、短路径的代码任务
* OpenAI 体系偏好的场景
* 你已经有 Codex 使用习惯，想迁移到 OpenClaw

很多用户最后的用法并不是二选一，而是：

* 默认主力放在 Claude Code
* 某些场景切去 Codex

而 gaccode 的价值就在这里：

**一套订阅，把多种原生工具能力一起接进 OpenClaw。**


---


---

## 不知道该填哪个 gateway

如果你当前问的是 gaccode / Claude Code / Codex 这类接入，标准答案通常就是：

```text
https://gaccode.com/claudecode
https://gaccode.com/codex
```

如果你问的是兔子 API / OpenAI 兼容 API，那才通常是：

```text
https://api.tu-zi.com
```

这两个不要混用。


---

## 一份最简理解版

如果你只想先跑通，不想看太多原理，可以直接照这个顺序：


1. 去 `https://gaccode.com/api-keys` 拿 key
2. 配置：

```bash
ANTHROPIC_BASE_URL=https://gaccode.com/claudecode
ANTHROPIC_API_KEY=你的_gaccode_key
```


3. 重启 OpenClaw
4. 先测试 Claude Code 是否可用
5. 再把 Codex 模型加入 OpenClaw 模型配置里
6. 切换到 Codex 做第二轮测试

这样最稳。


---

## 推荐实践

如果你是第一次接 gaccode 到 OpenClaw，建议按这个节奏来：

### 新手推荐顺序


1. 先把 OpenClaw 装好
2. 先只接 Claude Code
3. Claude Code 跑通以后，再加 Codex
4. 最后再做模型切换、默认模型调整、通道优化

这样排错最简单。

### 不建议的做法

* 一上来同时改很多配置
* Claude / Codex / API 站配置混着填
* 不确认模型名就乱写
* 改完不重启就直接下结论说"不能用"


---

## 总结

gaccode 订阅接入 OpenClaw，核心并不复杂，真正重要的是先分清两件事：


1. **Claude Code 通常先靠 gateway + key 接通**
2. **Codex 通常还需要补模型配置并切换模型**

只要你先把 Claude Code 跑通，再去补 Codex，整个过程会顺很多。

如果你是从使用角度来理解，也可以把它记成一句话：

**gaccode 提供 Claude Code / Codex 的接入能力，OpenClaw 负责把这些能力变成你日常可直接调用的工作流。**


---

## 相关链接

* gaccode key 获取： <https://gaccode.com/api-keys>
* gaccode 通道设置： <https://gaccode.com/configuration>
* OpenClaw 配置总说明： <https://wiki.tu-zi.com/s/8c61a536-7a59-4410-a5e2-8dab3d041958/doc/openclaw-gVTr4tVhjI?q=openclaw>
* OpenClawInstaller： <https://wiki.tu-zi.com/s/8c61a536-7a59-4410-a5e2-8dab3d041958/doc/openclawinstaller-openclaw-yXqo6dRAPz?q=openclaw>
* OpenClaw 独立主机安装成功步骤： <https://wiki.tu-zi.com/s/8c61a536-7a59-4410-a5e2-8dab3d041958/doc/openclaw-QxzIagj6yu>

如果你需要，我也可以继续再补一篇"按不同 OpenClaw 安装方式分别怎么填配置文件"的进阶版。