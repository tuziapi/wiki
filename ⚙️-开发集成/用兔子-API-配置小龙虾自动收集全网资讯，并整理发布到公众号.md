# 用兔子 API 配置小龙虾自动收集全网资讯，并整理发布到公众号

## 简介

本文基于 X 平台帖子《手把手教会你用小龙虾自动收集全网资讯整理发公众号》的思路，整理成一篇更适合复用的教程。目标是让小龙虾（OpenClaw）每天自动完成以下流程：


1. 从指定信息源抓取行业资讯
2. 筛选值得写的主题
3. 生成适合公众号发布的中文文章
4. 调用兔子 API 为文章生成配图
5. 调用微信公众号接口完成发文或进入待发布流程

如果你已经有小龙虾运行环境，这篇教程可以直接作为你的配置参考；如果还没有，也可以先按本文把外部依赖准备好，再回到小龙虾里编排任务。

原文作者从 2 月 20 日到 3 月 10 日开始给 OpenClaw 下达每日收集资讯并发布到微信公众号的任务，已经跑了半个月有余，一共 16 篇文章，一篇约 10w+，一篇 1.8w，剩下的大部分都在三四百个阅读。

 ![](https://wiki.tu-zi.com/api/files.get?sig=eyJhbGciOiJIUzI1NiIsInR5cCI6IkpXVCJ9.eyJrZXkiOiJ1cGxvYWRzLzA0MTA4NzY3LTk1YjgtNDYzMi05YWFmLTgwNzgwZjIwMmFkMi85MDgxNTk2ZS1lMWI0LTRmOTEtYTY3Ni0wNWQyM2YyNmYyOGUvaW1hZ2UucG5nIiwidHlwZSI6ImF0dGFjaG1lbnQiLCJpYXQiOjE3ODA0NTQ4OTYsImV4cCI6MTc4MDQ1ODQ5Nn0.k1f-QU8Dxi9VMiK6sc1W4z8F6_ud6NpmEm7Tz0Twy_w " =679x482")

 ![](https://wiki.tu-zi.com/api/files.get?sig=eyJhbGciOiJIUzI1NiIsInR5cCI6IkpXVCJ9.eyJrZXkiOiJ1cGxvYWRzLzA0MTA4NzY3LTk1YjgtNDYzMi05YWFmLTgwNzgwZjIwMmFkMi85MGI3YzkwYS1hMDAyLTQwZjktODJhYi1lMGE3YjEzMmJlOWYvaW1hZ2UucG5nIiwidHlwZSI6ImF0dGFjaG1lbnQiLCJpYXQiOjE3ODA0NTQ4OTYsImV4cCI6MTc4MDQ1ODQ5Nn0.oPfUlRRNDbCkSCyWiFwcKtvaqgyr5v59JWxAJSCl72Q " =680x585")

## 适用场景

* 想做 AI、跨境、电商、科技、创业等赛道的资讯号
* 想把"找选题 + 写稿 + 配图 + 发文"压缩成半自动或全自动流程
* 希望优先用兔子 API 提供模型与图片能力，而不是分别对接多个平台

## 整体流程

建议把整套工作流拆成 4 个独立环节：


1. 资讯源采集：用 Google News RSS、行业站点 RSS、关键词搜索结果做输入
2. 内容加工：让小龙虾对候选资讯去重、归纳、改写，输出公众号文章
3. 图片生成：通过兔子 API 调用图像模型，生成封面图和正文配图
4. 公众号发布：通过微信公众号开发接口上传素材并创建草稿或发布文章

这样拆分的好处是：出问题时更容易定位，也更容易替换单个模块。

## 前置条件

开始前请准备好以下内容：

* 一个微信公众号
* 微信公众平台开发者权限
* 一个可以稳定运行小龙虾的环境
* 兔子 API 账号与 API Key
* 至少一个稳定的资讯来源

其中，兔子 API 用于两类能力：

* 文本能力：辅助总结资讯、润色标题、扩写导语、整理文章结构
* 图像能力：为文章生成封面图和正文配图

兔子 API 文档入口：<https://tuzi-api.apifox.cn>

## 第一步：准备公众号发文能力

### 1. 获取公众号开发凭证

访问 微信开发者平台 [https://developers.weixin.qq.com/](https://developers.weixin.qq.com/登录微信公众平台后，进入对应公众号的开发设置页面，记录以下参数：)

 ![](https://wiki.tu-zi.com/api/files.get?sig=eyJhbGciOiJIUzI1NiIsInR5cCI6IkpXVCJ9.eyJrZXkiOiJ1cGxvYWRzLzA0MTA4NzY3LTk1YjgtNDYzMi05YWFmLTgwNzgwZjIwMmFkMi8wYmQwYzM5OS05NmY2LTQxOTAtOWY2Yi01YjM1MzYxOGU4ZjUvaW1hZ2UucG5nIiwidHlwZSI6ImF0dGFjaG1lbnQiLCJpYXQiOjE3ODA0NTQ4OTYsImV4cCI6MTc4MDQ1ODQ5Nn0.7MdkeXAyvSIrYUjLY1BKHo1nnwM2q6jpDwwOC73oEcE " =680x355")

登录后找到你的公众号

 ![](https://wiki.tu-zi.com/api/files.get?sig=eyJhbGciOiJIUzI1NiIsInR5cCI6IkpXVCJ9.eyJrZXkiOiJ1cGxvYWRzLzA0MTA4NzY3LTk1YjgtNDYzMi05YWFmLTgwNzgwZjIwMmFkMi82ZjU2ZmE2Zi0yMzRjLTQ0YmUtYWMwMy0wNjFiMTViNWZhMzkvaW1hZ2UucG5nIiwidHlwZSI6ImF0dGFjaG1lbnQiLCJpYXQiOjE3ODA0NTQ4OTYsImV4cCI6MTc4MDQ1ODQ5Nn0.FgYkqjYDCVMdEPAHzjR9bWpW0XCKCD_zY-X6R40IFPM " =680x409")

点击 开发密钥 下面 AppSecret 的重置按钮，找个记事本记录下你的公众号的 AppID 和 AppSecret

* `AppID`
* `AppSecret`

后续小龙虾在调用公众号接口时，会用这两个参数换取 access token。

### 2. 准备固定出口 IP

公众号部分接口通常要求调用来源满足白名单限制，因此更稳妥的做法是：

* 使用云服务器部署小龙虾或发文中转服务
* 确保请求出口 IP 固定
* 把该 IP 加入微信侧白名单

如果你的小龙虾跑在本地家宽、手机或网络环境经常变化的设备上，最容易出问题的不是模型调用，而是公众号接口授权和白名单。

### 3. 明确发布策略

建议先把目标设为"自动生成草稿，由你人工检查后发布"，跑通后再考虑全自动。原因很简单：

* 标题可能还需要人工优化
* 配图偶尔会偏题
* 热点类内容需要你做最终判断

## 第二步：配置资讯采集源

原帖推荐直接给小龙虾一个 Google News RSS 链接，这个思路是对的，因为它免费、稳定、可按关键词聚合。

### 推荐做法

围绕一个固定赛道准备 3 到 10 个资讯源，例如：

* Google News RSS 关键词订阅
* 行业媒体 RSS
* 竞品博客更新页
* 你长期关注的 KOL 公开内容

### 给小龙虾的采集要求

你可以把下面这类规则直接交给小龙虾：

```text
每天抓取过去 24 小时内的 AI 行业资讯，优先选择能引发讨论、对普通读者有实用价值、且不与近 7 天已发布内容重复的话题。

输出时先给我 3 个候选选题，每个选题包含：
1. 一句话摘要
2. 适合公众号传播的角度
3. 可延展成正文的核心信息点
```

这一步的重点不是"抓得越多越好"，而是"先做筛选再写作"。

## 第三步：把兔子 API 接入到配图与内容加工环节

### 1. 获取兔子 API Key

在兔子 API 平台创建自己的 Key，并保存在小龙虾可读取的配置中。至少准备以下字段：

```text
TUZI_API_BASE_URL=https://api.tu-zi.com/v1
TUZI_API_KEY=你的兔子 API Key
```

如果你的小龙虾支持 OpenAI 兼容格式，通常只需要配置：

* `base_url`: `https://api.tu-zi.com/v1`
* `api_key`: 你的兔子 API Key

具体可用模型，以兔子 API 文档中的最新模型列表为准。

### 2. 让小龙虾调用兔子 API 生成封面图

建议每篇文章至少准备：

* 1 张封面图
* 1 张正文配图

给模型的出图提示词，不要只写"生成一张科技图"，而要带上文章主题、画面风格和公众号使用场景。例如：

```text
为一篇关于"AI 自动整理全网资讯并发布公众号"的中文公众号文章生成封面图。
要求：科技感、信息流、蓝白配色、16:9 横图、适合公众号头图、不要英文水印、不要明显文字。
```

如果你的账号已经接入兔子 API 的图像模型能力，小龙虾只需要：


1. 根据文章主题自动生成提示词
2. 调用兔子 API 生成图片
3. 保存图片 URL 或下载结果
4. 在发布前把图片上传到公众号素材接口

### 3. 让小龙虾用兔子 API 辅助整理文章

除了出图，兔子 API 也可以承担内容加工工作，例如：

* 把多条资讯归并成一个主题
* 生成公众号标题候选
* 改写成更口语化的导语
* 提炼文末总结与行动建议

一个实用的写作提示词可以是：

```text
你是中文公众号编辑。请根据我提供的资讯材料，写一篇适合公众号发布的文章。

要求：
1. 标题给出 3 个候选
2. 开头用通俗语言交代"这件事为什么值得关注"
3. 正文按"事件背景、核心变化、对普通人的影响、我的判断"组织
4. 避免机翻感和空话
5. 输出 Markdown
```

## 第四步：教小龙虾自动完成发文

当资讯、正文、配图都准备好后，就进入公众号发文环节。

比较稳的流程是：


1. 小龙虾生成文章 Markdown
2. 小龙虾调用兔子 API 生成图片
3. 小龙虾把图片上传到公众号素材接口
4. 小龙虾把正文转成公众号需要的内容格式
5. 小龙虾创建草稿，或直接提交发布

如果你不是开发者，也可以把下面这些材料一次性交给小龙虾：

* 微信公众号接口文档
* 你的 `AppID`
* 你的 `AppSecret`
* 兔子 API 的 `base_url`
* 兔子 API 的 `api_key`
* 你希望的写作风格说明
* 你要跟踪的资讯源

## 一套可直接复用的任务模板

下面是一段适合交给小龙虾的高层任务描述：

```text
你每天执行一次资讯整理任务。

目标：
围绕"AI 行业动态"自动生成一篇适合微信公众号发布的中文文章，并生成配图。

执行步骤：
1. 从我提供的 RSS 和资讯源中抓取近 24 小时内容
2. 去重后选出 3 个最值得写的主题
3. 选择其中最适合公众号传播的 1 个主题
4. 生成一篇 1200 到 1800 字的中文文章，输出 Markdown
5. 调用兔子 API 生成 1 张封面图和 1 张正文配图
6. 上传图片到公众号素材库
7. 生成公众号草稿，并返回标题、摘要、封面图、正文和草稿链接

写作要求：
1. 语言口语化，但不要夸张标题党
2. 优先解释"这条资讯和普通人有什么关系"
3. 如果信息不充分，不要硬编
4. 与最近 7 天已经生成的内容尽量避免重复
```

## 运行建议

### 发布频率

建议从每天 1 次开始，跑稳后再增加到每天 2 次。原理很简单：

* 频率太高，容易重复选题
* 频率太低，又不利于测试流程稳定性

### 成本控制

如果你把兔子 API 主要用于配图和润色，而不是全文多轮反复生成，整套流程的成本通常可控。比较常见的优化方式有：

* 先筛选资讯，再决定是否生成正文
* 先生成标题和摘要，通过后再配图
* 图片生成失败时降级为默认封面模板

### 质量控制

建议在自动化里增加 3 个兜底判断：


1. 没有高质量候选主题时，不发文
2. 配图失败时，进入人工审核队列
3. 文章存在明显事实不确定性时，只生成草稿不直接发布

## 常见问题

### 为什么明明文章写出来了，但公众号发不出去？

优先检查以下几点：

* `AppID` 和 `AppSecret` 是否正确
* access token 是否过期
* 请求来源 IP 是否已加入白名单
* 图片是否先上传成公众号可用素材

### 为什么建议把兔子 API 放在中间能力层？

因为这样更容易替换上层工作流。你以后无论是继续用小龙虾、切换到 Dify、Coze，还是自己写脚本，兔子 API 都可以继续承担模型和图像能力。

### 一定要全自动发布吗？

不一定。大多数人更适合"自动生成草稿 + 人工确认发布"的模式，这样稳定性和可控性更好。

## 注意事项

* 不要把 API Key 明文发到公开群聊或知识库
* 不要一开始就接入太多资讯源，否则噪音会明显增加
* 不要让模型自由发挥生成未经核实的事实结论
* 如果你的号还在早期阶段，先追求流程稳定，再追求规模

## 相关链接

* 原始帖子：<https://x.com/ezshine/status/2031224897004052789>
* 兔子 API 文档：<https://tuzi-api.apifox.cn>
* 兔子 API 站：<https://api.tu-zi.com>
* 小龙虾 / OpenClaw：请使用你当前部署版本对应的文档