# 👥 销售代理申请（API 站分销）

# 兔子 API 代理商招募 & 使用教程

> 文档版本：2025-06\n适用对象：淘宝、闲鱼卖家等其他对C端用户


---

## 1. 关于 **api.tu-zi.com**

* **核心定位**：一站式 AI 模型中转平台
  * 覆盖 OpenAI GPT-4o / GPT-4-Turbo、Anthropic Claude 4（Opus, Sonnet, Haiku）、Gemini 2.5 等主流模型
* **极致价格**：
  * Claude 4 API 仅 7 元 / 10 USD 额度（淘宝同类店铺约 19.8 元）\n![](https://wiki.tu-zi.com/api/files.get?sig=eyJhbGciOiJIUzI1NiIsInR5cCI6IkpXVCJ9.eyJrZXkiOiJ1cGxvYWRzL2UxMjc0Y2E3LWNmZTEtNDdlOC04MjA0LTNhMDkzMTNlNzM4ZC82NzgwMjVjZC1iMjc4LTQ5NTYtYjk0ZS05ZDg0NGUwYmI4ZWYvaW1hZ2UucG5nIiwidHlwZSI6ImF0dGFjaG1lbnQiLCJpYXQiOjE3ODA0NTQ5OTEsImV4cCI6MTc4MDQ1ODU5MX0.bkTeNEWO086hO5YEqfmRnzjy0M9puCYJ9Adgw5bVbKM " =940x691")
  * **GPT-4o**、**GPT-O3** 等模型同档价格低至官方 1 折 不到


---

## 2. 成为代理商的三步

| 步骤  | 操作  | 说明  |
|-----|-----|-----|
| ① 注册账户 | 访问 **https://api.tu-zi.com**， | 支持邮箱/github/google |
| ② 充值额度 | 进入「余额」->「充值」，选择支付宝 / 微信 / Stripe | 支持人民币与美元 |
| ③ 生成令牌 | 参考官方教程 @[https://wiki.tu-zi.com/s/8c61a536-7a59-4410-a5e2-8dab3d041958/doc/api-Q76TllZEfR](mention://60e5ac67-7d35-41a3-a504-236df86b3b46/url/0b27573b-03cc-4153-9c87-0a1e7c229092)  | 每个令牌可单独限流、设置白名单、额度等 |

* **说明**：令牌的生成不消耗任何现金，用户使用时才会对应从钱包中扣款；也就是说如果卖出一个100美金的令牌，客户实际永远没用过，那你的成本就为0.


---

## 3. 令牌使用与查询

* **令牌查询网站**：<https://check.sydney-ai.com> ![](https://wiki.tu-zi.com/api/files.get?sig=eyJhbGciOiJIUzI1NiIsInR5cCI6IkpXVCJ9.eyJrZXkiOiJ1cGxvYWRzL2UxMjc0Y2E3LWNmZTEtNDdlOC04MjA0LTNhMDkzMTNlNzM4ZC9kZjdlNzYwZC1iOGE5LTRmN2YtOWY3Mi1mODcwMGNhNDdmODgvaW1hZ2UucG5nIiwidHlwZSI6ImF0dGFjaG1lbnQiLCJpYXQiOjE3ODA0NTQ5OTEsImV4cCI6MTc4MDQ1ODU5MX0.2ktn_xLyOmtCaeTp2cpkgv6eFgh5gijQzSSPXpXHDH0 " =2488x1317")
* API Base URL：https://api.sydney-ai.com（该地址直接访问将返回 404，保障您的用户和兔子站点隔离）\n![](https://wiki.tu-zi.com/api/files.get?sig=eyJhbGciOiJIUzI1NiIsInR5cCI6IkpXVCJ9.eyJrZXkiOiJ1cGxvYWRzL2UxMjc0Y2E3LWNmZTEtNDdlOC04MjA0LTNhMDkzMTNlNzM4ZC82OTdkMzM4Yy04MGQ0LTQzMjktOTJjYi04MzZkNDg1NjcxNjcvMzg5NWUyZTNhYWUwNWUyYTIwNGJiYWQ3M2Q2OGVkYjAuanBnIiwidHlwZSI6ImF0dGFjaG1lbnQiLCJpYXQiOjE3ODA0NTQ5OTEsImV4cCI6MTc4MDQ1ODU5MX0.NavYL3sRH3bCNYyHOlzYYZ-JRVm5gHWj21LY_IlZpOc " =1460x1080")


---

## 4. 模型状态查询

这是状态查询地址（@[https://apistatus.sydney-ai.com/](mention://ee630e84-cadb-4192-94b1-ffbafc254281/url/c2c7d976-3cd7-4944-839e-32dceabbec0b) ），没有我们的信息，方便提供给客户

[https://apistatus.sydney-ai.com/](https://apistatus.sydney-ai.com/)

## 5. 接口说明

### 5.1 支持带key的自动查询

如下格式访问，会自动填充 key并点击查询按钮

```bash
https://check.sydney-ai.com/?key=sk-**
```

 ![](https://wiki.tu-zi.com/api/files.get?sig=eyJhbGciOiJIUzI1NiIsInR5cCI6IkpXVCJ9.eyJrZXkiOiJ1cGxvYWRzLzA0MTA4NzY3LTk1YjgtNDYzMi05YWFmLTgwNzgwZjIwMmFkMi9jYjllNDk5Mi02ZWNkLTQxOTYtYmMzYy04YTgzYmY0ZDNhNzAvaW1hZ2UucG5nIiwidHlwZSI6ImF0dGFjaG1lbnQiLCJpYXQiOjE3ODA0NTQ5OTEsImV4cCI6MTc4MDQ1ODU5MX0.wyldAf7wMhbt74ME8tDsBOvnYD_tWSXYyYQAxg_Q-x8 " =1886x744")

## 6. 法律合规与数据安全

* 接口日志默认保留 30 日，仅用于异常排查
* 对于违规用途（色情、暴力、政治敏感内容）将依据平台协议立即封禁


---

## 7. 联系我们

 ![微信群二维码](https://wiki.tu-zi.com/api/files.get?sig=eyJhbGciOiJIUzI1NiIsInR5cCI6IkpXVCJ9.eyJrZXkiOiJ1cGxvYWRzL2UxMjc0Y2E3LWNmZTEtNDdlOC04MjA0LTNhMDkzMTNlNzM4ZC9mY2EwNjliYS01ZGI1LTRhYTctOGIxZi05ZmNlNWRlZWU2NDMvaW1hZ2UucG5nIiwidHlwZSI6ImF0dGFjaG1lbnQiLCJpYXQiOjE3ODA0NTQ5OTEsImV4cCI6MTc4MDQ1ODU5MX0.BxIbkpc5LFzsioD8rorsQcgjx8RgdquVn6z_4MhDLsc "left-50 =152x152")

> 立即注册，开启你的 AI 代理之旅！\n<https://api.tu-zi.com>