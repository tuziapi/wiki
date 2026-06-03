# sora-2

## 一、简要介绍

Sora-2 已支持以下功能：

* **客串模式**：通过 Sora.com 网站查询公开授权的人物 ID，使用 @id 来进行操作。例如：@sama。
* **横竖屏切换**：通过提示词中要求"横屏"或"竖屏"控制输出视频状态。
* **输出质量**：10s/15s视频，默认无水印
* **编辑功能**：支持编辑（Remix）

**审查流程**

官方审查会涉及至少 3 个阶段/方向：


1. **提交的图片是否涉及真人**：如果图片中的人物非常像真人，也不符合要求。
2. **提示词内容是否违规**：检查是否含有暴力、色情、侵犯版权或涉及活着的名人等内容。
3. **生成结果审查是否合格**：这是导致生成失败的常见原因之一，通常发生在生成了 90% 多时出现问题。

**开发文档**


1. **官方接口（异步）（推荐）**： **__[查看文档](https://tuzi-api.apifox.cn/359269497e0)__**\n建议优先适配官方接口，该接口请求失败不扣费用
2. **同步接口**： **__[查看文档](https://tuzi-api.apifox.cn/343647039e0)__**
3. **老异步接口（不推荐）**： **__[查看文档](https://tuzi-api.apifox.cn/357807698e0)__**

**来自社群的示例**

* 基于 Sora，制作一个简易的小应用：**__[观看教程视频](https://www.youtube.com/watch?v=9Y0GxB2OUD4)__**

## 二、小白 web 端使用方法(aitu画布)

### 2.1 访问令牌（@[https://api.tu-zi.com/token](mention://c4fb7929-315f-4814-84aa-cedde20fcd35/url/36451469-3eff-41d5-81c6-5a9184cf503c) )


获取自己的令牌（`defalut` 分组或`原价`分组）


1. ![](https://wiki.tu-zi.com/api/files.get?sig=eyJhbGciOiJIUzI1NiIsInR5cCI6IkpXVCJ9.eyJrZXkiOiJ1cGxvYWRzLzA0MTA4NzY3LTk1YjgtNDYzMi05YWFmLTgwNzgwZjIwMmFkMi8wZDM1MmYwNi0wN2ZlLTRiNGEtYTQ5Zi1iNGY3NmRmNTRjNWMvaW1hZ2UucG5nIiwidHlwZSI6ImF0dGFjaG1lbnQiLCJpYXQiOjE3ODA0NTQ5NDcsImV4cCI6MTc4MDQ1ODU0N30.U0y1cX1iaDKYqIqz_HBGZ39H09nISpwLDGz1kXfYjsQ " =1116x688")

   \


### 2.2 AITU 画布中 使用 Sora 2 生成视频


 ![](https://wiki.tu-zi.com/api/files.get?sig=eyJhbGciOiJIUzI1NiIsInR5cCI6IkpXVCJ9.eyJrZXkiOiJ1cGxvYWRzL2I3MTgwNDFlLWUwNjItNDRlMy1iNTljLTlkYzliNjNjODczMi85YzVjM2JlOC1hYWI0LTRmY2EtOWUzOC02MmZiMzdjMzAwODEvaW1hZ2UucG5nIiwidHlwZSI6ImF0dGFjaG1lbnQiLCJpYXQiOjE3ODA0NTQ5NDcsImV4cCI6MTc4MDQ1ODU0N30.o0bchhAgDKNDf94M8TbMXwIKouNwsYzX_IDgvMAGprk " =1160x292")


选择 default 分组令牌

 ![](https://wiki.tu-zi.com/api/files.get?sig=eyJhbGciOiJIUzI1NiIsInR5cCI6IkpXVCJ9.eyJrZXkiOiJ1cGxvYWRzL2I3MTgwNDFlLWUwNjItNDRlMy1iNTljLTlkYzliNjNjODczMi85NjRkOWQ5My0xZGJkLTQ1ZmMtYjg1OC0yMzRmNzYxYzBlNjAvaW1hZ2UucG5nIiwidHlwZSI6ImF0dGFjaG1lbnQiLCJpYXQiOjE3ODA0NTQ5NDcsImV4cCI6MTc4MDQ1ODU0N30.TqX-nz2SH9Cfb0s5SbVyJQrsvMbj2zqwRGXWG2L_pzg " =1165x332")


 ![](https://wiki.tu-zi.com/api/files.get?sig=eyJhbGciOiJIUzI1NiIsInR5cCI6IkpXVCJ9.eyJrZXkiOiJ1cGxvYWRzL2I3MTgwNDFlLWUwNjItNDRlMy1iNTljLTlkYzliNjNjODczMi8yZmM0NWZmMC1iYTQwLTRiNWYtYTAzZi05M2ViYWJhN2RlODIvaW1hZ2UucG5nIiwidHlwZSI6ImF0dGFjaG1lbnQiLCJpYXQiOjE3ODA0NTQ5NDcsImV4cCI6MTc4MDQ1ODU0N30.ZMozdBcAF_EPu1aIIBPJode2owcRvyx4IhiLYhqoWxI " =933x838")


\
 ![](https://wiki.tu-zi.com/api/files.get?sig=eyJhbGciOiJIUzI1NiIsInR5cCI6IkpXVCJ9.eyJrZXkiOiJ1cGxvYWRzL2I3MTgwNDFlLWUwNjItNDRlMy1iNTljLTlkYzliNjNjODczMi83NzUxZWMyMi01ZjE1LTRlNTEtOWYwNi1kNGJmYzZiYmE0MmIvaW1hZ2UucG5nIiwidHlwZSI6ImF0dGFjaG1lbnQiLCJpYXQiOjE3ODA0NTQ5NDcsImV4cCI6MTc4MDQ1ODU0N30.AlcUyeDYWPh72mtVo2aPfnVK76OxKV25DQmAKXMaL-8 " =1389x646")


\