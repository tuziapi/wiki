# 30 元 / 月，把 OpenClaw + 飞书装成你的效率核武器

如果你想让 AI 真正在飞书里帮你干活，而不是只会聊天，这套组合非常值得试：

* OpenAI Business / Team 级账户
* OpenClaw
* 飞书官方插件

先说结论：

> 30 元 / 月，官方 Business / Team 级账户，日常聊天、写文档、跑 OpenClaw 基本非常够用，个人和小团队拿来跑 OpenClaw + 飞书，完全够打。

更重要的是，这套方案不是只能"聊两句"的玩具。OpenClaw 接上飞书后，可以在授权范围内直接读取和操作你的飞书内容，比如群聊、文档、日历、任务、多维表格和电子表格，也就是说，AI 不再只是"给建议"，而是可以真正进入你的工作流。

## 一、开始前要准备什么

在开始前，你只需要准备 3 样东西。

### 1. 一个 OpenAI Business / Team 级账户

购买地址： <https://store.tu-zi.com/item/57>

它适合拿来做什么：

* 日常聊天
* 写文档
* 跑 OpenClaw
* 给 Codex / OpenAI 登录提供可用账户

对于个人用户和小团队来说，这个价格非常友好，起步成本很低。

### 2. 一台美国服务器

建议把 OpenClaw 部署在美国服务器上。

原因很简单：Codex 的 gpt-5.4 跑得更快，整体体验明显更顺。如果你只是偶尔玩玩，本地也能试；但如果你想把它当成日常工具，部署在美国服务器上通常更舒服。

### 3. 一个飞书账号

后面安装飞书插件时，需要通过飞书扫码创建机器人并完成授权。

## 二、先安装 OpenClaw

这一步一定是最先做的。先有 OpenClaw，后面才能装飞书插件、接 OpenAI 账户。

官网： <https://openclaw.ai/>

安装

```bash
npm install -g openclaw
```

装好之后，建议先确认 OpenClaw 已经能正常运行。

## 三、安装飞书官方插件

OpenClaw 装好后，下一步就是安装飞书插件。

执行命令：

```bash
npx -y @larksuite/openclaw-lark-tools install
```

如果报权限错误，可以在命令前加 sudo 再试一次。

安装过程中，你会看到二维码。用飞书客户端扫码后，系统会自动帮你创建飞书机器人，并处理一部分权限、事件和安全配置，整个流程已经比以前简单很多。

## 四、绑定 OpenAI / Codex 账户

确认 OpenClaw 和飞书插件都装好之后，再做 OpenAI 登录，这个顺序才对。

如果你使用的是 OpenAI / Codex 订阅体系，可以执行：

```bash
openclaw onboard --auth-choice openai-codex
```

 ![](https://wiki.tu-zi.com/api/files.get?sig=eyJhbGciOiJIUzI1NiIsInR5cCI6IkpXVCJ9.eyJrZXkiOiJ1cGxvYWRzL2RiZTJjMjRhLWQ4M2MtNGUxMy1iYzc2LTZlNDBmZGM3YmZlNS85NzBhMzExYy1hM2M1LTQxMGItYWY3ZC05MThlZDM0NGZlYTMvaW1hZ2UucG5nIiwidHlwZSI6ImF0dGFjaG1lbnQiLCJpYXQiOjE3ODA0NTQ4NDgsImV4cCI6MTc4MDQ1ODQ0OH0._YwKtJUg2mn-5lZ05l3Iqc_vwrPJ0ed3dDAyaouiyHQ " =947x454")

这一步适合：

* 想通过 ChatGPT / Codex 登录来使用能力
* 不想一开始就折腾 API key
* 希望尽快把 OpenClaw 接到可用模型上

做完之后，OpenClaw 才算真正接上 OpenAI 这一侧的能力。

## 五、在飞书里验证插件是否安装成功

插件装完后，去飞书里找到这个机器人，发送：

```text
/feishu start
```

如果返回了版本号信息，说明插件已经安装成功。

这一步很重要，建议不要跳过。先确认插件活着，后面再做登录和授权。

## 六、完成飞书授权

如果你想让 OpenClaw 真正访问你的飞书数据，比如：

* 读取群聊上下文
* 读取或更新文档
* 查看日历
* 操作任务
* 读写表格

那还需要做用户授权。直接在飞书里对机器人发送：

```text
/feishu auth
```

授权完成后，OpenClaw 才能在你允许的范围内真正"伸进飞书里干活"。

## 七、建议顺手做的 3 个增强配置

### 1. 开启流式输出

这样飞书里的回复体验更自然。

```bash
openclaw config set channels.feishu.streaming true
```

如果以后不想用流式输出，可以关闭：

```bash
openclaw config set channels.feishu.streaming false
```

还可以额外打开一些卡片状态信息：

```bash
openclaw config set channels.feishu.footer.elapsed true
openclaw config set channels.feishu.footer.status true
```

### 2. 开启话题独立上下文和多任务并行

如果你在飞书话题群里使用，非常推荐打开：

```bash
openclaw config set channels.feishu.threadSession true
```

关闭命令：

```bash
openclaw config set channels.feishu.threadSession false
```

开启后，每个话题都可以有自己的上下文，不容易串台，也更适合并行处理多个任务。

### 3. 建议保留"必须 @ 才回复"

大多数群里都推荐这个模式，避免刷屏。

```bash
openclaw config set channels.feishu.requireMention true --json
```

这样机器人只有在被 @ 的时候才会回复，比较稳。

## 八、装好之后，它能帮你做什么

这套方案真正的价值，不是"接了个 AI 聊天机器人"，而是让 OpenClaw 真正进入飞书工作现场。

比如你可以让它：

* 读取群聊和话题回复，整理上下文
* 生成会议纪要并写入飞书文档
* 查你的日历和档期冲突
* 创建和更新任务
* 处理多维表格和电子表格内容
* 搜索历史消息、下载文件、整理资料

以前你得把消息、文档、表格一段段复制给 AI。现在是 AI 在授权后，直接去飞书里读上下文，再回来帮你干活。

这就是为什么说：

> OpenClaw + 飞书，不是普通助手，是效率核武器。

## 九、遇到问题怎么办

飞书插件现在还在快速迭代中，所以遇到小问题并不奇怪。不过它也准备了比较完整的诊断命令。

### 飞书里可以直接用

```text
/feishu start
/feishu doctor
/feishu auth
```

### 终端里可以用

```bash
npx @larksuite/openclaw-lark-tools doctor
```

自动修复：

```bash
npx @larksuite/openclaw-lark-tools doctor --fix
```

查看信息：

```bash
npx @larksuite/openclaw-lark-tools info
npx @larksuite/openclaw-lark-tools info --all
```

如果安装不顺、权限异常、插件没反应，这几条命令都很有用。

## 十、安全提醒

飞书插件之所以强，是因为它接入了真实工作数据：消息、文档、日历、联系人和协作记录，所以也一定要注意边界。

建议你这样用：

* 先用个人账号试
* 先熟悉能力，再接入更正式场景
* 涉及发送、修改、写入时先预览再确认
* 不要让 AI 完全脱离人工监督自动执行

一句话：它很好用，但别闭着眼全自动。

## 十一、最终总结

如果你想用一个低成本、但真正能打的方案，把 AI 接入飞书工作流，那么按下面这条顺序做就行：


1. 准备 OpenAI Business / Team 级账户
2. 准备一台美国服务器
3. 安装 OpenClaw
4. 安装飞书官方插件
5. 在飞书里用 `/feishu start` 验证安装成功
6. 用 `openclaw onboard --auth-choice openai-codex` 完成 OpenAI / Codex 登录
7. 用 `/feishu auth` 完成飞书授权
8. 按需开启流式输出、话题独立上下文等增强配置

搭完之后，你得到的就不是一个只能聊天的 AI，而是一个能在飞书里看消息、读文档、查日历、管任务、碰表格的工作助手。

最后一句话总结：

> 30 元 / 月，官方 Business / Team 级账户，日常聊天、写文档、跑 OpenClaw 基本非常够用，个人和小团队拿来跑 OpenClaw + 飞书，完全够打。