# 🔧gpt充值服务指南

# 一、购买服务

进入兔小店购买gpt充值服务-以下为兔小店链接:

<https://store.tu-zi.com/>

 ![](https://wiki.tu-zi.com/api/files.get?sig=eyJhbGciOiJIUzI1NiIsInR5cCI6IkpXVCJ9.eyJrZXkiOiJ1cGxvYWRzL2I3MTgwNDFlLWUwNjItNDRlMy1iNTljLTlkYzliNjNjODczMi9jMDcxNzdjOS1kNWE3LTQ4MDAtYWIzYi00MmI4OGYxMDg1YTgvaW1hZ2UucG5nIiwidHlwZSI6ImF0dGFjaG1lbnQiLCJpYXQiOjE3ODA0NTQ5ODEsImV4cCI6MTc4MDQ1ODU4MX0.7z5y-vfNkdxFMvfm5ExJzZFcbrEP54ZteBu00cs-DIw " =1310x438")

# 二、3种方式充值（任选其一，优先推荐「方案二」方式，获取session，简单方便）

## 方式 1：登录gpt官网获取充值链接

### 2.1.1 左上角点击升级

 ![](https://wiki.tu-zi.com/api/files.get?sig=eyJhbGciOiJIUzI1NiIsInR5cCI6IkpXVCJ9.eyJrZXkiOiJ1cGxvYWRzL2I3MTgwNDFlLWUwNjItNDRlMy1iNTljLTlkYzliNjNjODczMi9kYTY0Nzk2YS04Y2FmLTQxOGMtODZmMy03NjYwYWQ1ZDViNGUvd2Vjb20tdGVtcC0xNjQ3MjctMzhmNmQ4YTk4ZGFhZjQ2MDk2MWRjODJiZjg4MWRlMGUucG5nIiwidHlwZSI6ImF0dGFjaG1lbnQiLCJpYXQiOjE3ODA0NTQ5ODEsImV4cCI6MTc4MDQ1ODU4MX0.cJLNHygUhXn_n3L2xnKKm6bwvPkRAbqiI4QI-q_LnCg " =2962x1024")


### 2.1.2 点击获取plus

 ![](https://wiki.tu-zi.com/api/files.get?sig=eyJhbGciOiJIUzI1NiIsInR5cCI6IkpXVCJ9.eyJrZXkiOiJ1cGxvYWRzL2I3MTgwNDFlLWUwNjItNDRlMy1iNTljLTlkYzliNjNjODczMi82NjAzYzBhNC0wNzkxLTRlYTgtOTU4NS1jY2UyZTQ1ODdhMTUvd2Vjb20tdGVtcC0yNDk4NDEtYjc0ZWZiYTc0NzQxODIxNWFkYmY1Zjc4ZjJjY2I1ZDAucG5nIiwidHlwZSI6ImF0dGFjaG1lbnQiLCJpYXQiOjE3ODA0NTQ5ODEsImV4cCI6MTc4MDQ1ODU4MX0.fjfBliXRpjQEk3z8yIBOg6Q7XpZZQrfnxZMvCe8DQlw " =1731x1526")


### 2.1.3 打开浏览器开发者工具

 ![](https://wiki.tu-zi.com/api/files.get?sig=eyJhbGciOiJIUzI1NiIsInR5cCI6IkpXVCJ9.eyJrZXkiOiJ1cGxvYWRzL2I3MTgwNDFlLWUwNjItNDRlMy1iNTljLTlkYzliNjNjODczMi84ZGYzNzhjOS00NzllLTQzZGUtOGY3Ny04ZDA2MDIyMjAzM2Ivd2Vjb20tdGVtcC0yMjE0MjYtYzQwOTMxZjEyMjYxZjA2YTE2YWYzNjcyYzMyNzNlY2IucG5nIiwidHlwZSI6ImF0dGFjaG1lbnQiLCJpYXQiOjE3ODA0NTQ5ODEsImV4cCI6MTc4MDQ1ODU4MX0.AjLdtv46IRRflPUivzQTlDY_XbV7urHclKY0ebq78g0 " =1149x1767")


### 2.1.4  清空控制台数据

 ![](https://wiki.tu-zi.com/api/files.get?sig=eyJhbGciOiJIUzI1NiIsInR5cCI6IkpXVCJ9.eyJrZXkiOiJ1cGxvYWRzL2I3MTgwNDFlLWUwNjItNDRlMy1iNTljLTlkYzliNjNjODczMi82NTZlYzgzOC03Zjg2LTQ3OTgtODllZC04NWZlZmIzYzEwYWUvd2Vjb20tdGVtcC0yODQ4NDItMDU5ZWUwNmIxODkzZmI5ZTcwMzBjMmQ1NjY3NDI1MGEucG5nIiwidHlwZSI6ImF0dGFjaG1lbnQiLCJpYXQiOjE3ODA0NTQ5ODEsImV4cCI6MTc4MDQ1ODU4MX0.lsjBTBh_WqsgS07-bnuuWwmhKSvr7scot-LqTEeRE0Y " =1275x1489")


### 2.1.5 控制台中输入代码

复制以下代码 在控制台中 按 enter 确定

```javascript
fetch("/api/auth/session").then(r => r.json()).then(({ accessToken }) => {
  fetch("/backend-api/payments/checkout", {
    "method": "POST",
    "headers": { "authorization": `Bearer ${accessToken}`, },
    
  }).then(r => r.json()).then(d => window.open(d.url))
})
```

**⚠️注意:**  在复制以上代码到控制台时,可能会弹出 以下 警告:   请在 控制台中 输入  "允许粘贴"   然后按enter 确认 

>  ![](https://wiki.tu-zi.com/api/files.get?sig=eyJhbGciOiJIUzI1NiIsInR5cCI6IkpXVCJ9.eyJrZXkiOiJ1cGxvYWRzL2I3MTgwNDFlLWUwNjItNDRlMy1iNTljLTlkYzliNjNjODczMi9mM2NjN2U2Yi1mOTMzLTQyZjAtOTJiNy03MDJiNTM3ZjhlNmUvd2Vjb20tdGVtcC0xMjc2Mi02OGZlZWQxZDI4ZGJlYWY5NTk1MDFjZjQ4OWRmZGJmZC5wbmciLCJ0eXBlIjoiYXR0YWNobWVudCIsImlhdCI6MTc4MDQ1NDk4MSwiZXhwIjoxNzgwNDU4NTgxfQ.-xsx3tKJIPj7cDzofv4VPbxhBowEuhVvE9HJljzlW-M " =438x155")\n ![有的情况下是中文"允许粘贴"](https://wiki.tu-zi.com/api/files.get?sig=eyJhbGciOiJIUzI1NiIsInR5cCI6IkpXVCJ9.eyJrZXkiOiJ1cGxvYWRzLzA0MTA4NzY3LTk1YjgtNDYzMi05YWFmLTgwNzgwZjIwMmFkMi9jY2ViNWU1NC1jNjI0LTRjYzQtYjhiNi05NDM3OTFmZGJhMWQv5LyB5Lia5b6u5L-h5oiq5Zu-XzI4YzVhN2M0LTY0YWMtNGMyMS05YzJmLTM1ZjdiYWJlMmUxMi5wbmciLCJ0eXBlIjoiYXR0YWNobWVudCIsImlhdCI6MTc4MDQ1NDk4MSwiZXhwIjoxNzgwNDU4NTgxfQ._ZjuIeys2dFRvlrp75RJifaPAIFh9yiZUCb_dvbemUo " =514x416")


**然后再张贴代码:**


 ![](https://wiki.tu-zi.com/api/files.get?sig=eyJhbGciOiJIUzI1NiIsInR5cCI6IkpXVCJ9.eyJrZXkiOiJ1cGxvYWRzL2I3MTgwNDFlLWUwNjItNDRlMy1iNTljLTlkYzliNjNjODczMi9mMTgxMmI1My0xMDFmLTRlZDktYWVjNC1mYzIzYjY1N2YxZDgvd2Vjb20tdGVtcC0xMTkwNjktYzVhYjQ0ZDJiMzNlMGM4ZDMyNzFhNjc3NGZlMWIwNjgucG5nIiwidHlwZSI6ImF0dGFjaG1lbnQiLCJpYXQiOjE3ODA0NTQ5ODEsImV4cCI6MTc4MDQ1ODU4MX0.hDq7PLpcYni9wni-FlHKv6aKFYLbeHY222DEQaLXVIk " =1146x970")

### 2.1.6  获取新弹出窗口的充值链接

**⚠️注意:** 第五步按下回车键后,可能会弹出阻挡窗口—- 按照下图操作

>  ![](https://wiki.tu-zi.com/api/files.get?sig=eyJhbGciOiJIUzI1NiIsInR5cCI6IkpXVCJ9.eyJrZXkiOiJ1cGxvYWRzL2I3MTgwNDFlLWUwNjItNDRlMy1iNTljLTlkYzliNjNjODczMi83ZDcyYzk0YS0wMmJhLTQ4MGMtOGVlOC0zYzQ3MWQ2NjRlNGUvd2Vjb20tdGVtcC0xNjYxMjItOTFkMTk4NWI1NTQ3MzU3NjEwMDY3YTk0OGNlOWEyYTUucG5nIiwidHlwZSI6ImF0dGFjaG1lbnQiLCJpYXQiOjE3ODA0NTQ5ODEsImV4cCI6MTc4MDQ1ODU4MX0.Si0T18VmZcFnga5D6D0h5LOc9KdIaGZ8YGjNTNgr0TQ " =1053x1314")


**最后: 复制该充值链接咨询企微客服**


 ![](https://wiki.tu-zi.com/api/files.get?sig=eyJhbGciOiJIUzI1NiIsInR5cCI6IkpXVCJ9.eyJrZXkiOiJ1cGxvYWRzL2I3MTgwNDFlLWUwNjItNDRlMy1iNTljLTlkYzliNjNjODczMi85Yjk1MzVhMy02YWI2LTQ0MDItYmI1YS04MDUzMjQ1ZjgxOGQvaW1hZ2UucG5nIiwidHlwZSI6ImF0dGFjaG1lbnQiLCJpYXQiOjE3ODA0NTQ5ODEsImV4cCI6MTc4MDQ1ODU4MX0.Gd_YavyBfz027RIC1NLN1te3HATFeSx4CTogZhKU3VQ " =1417x618")

## 方式 2：提供账户 token 全部信息

在 chatgpt.com 上线完成登入，在打开 下面网址复制其中全部信息给我们即可

```bash
https://chatgpt.com/api/auth/session
```

 ![](https://wiki.tu-zi.com/api/files.get?sig=eyJhbGciOiJIUzI1NiIsInR5cCI6IkpXVCJ9.eyJrZXkiOiJ1cGxvYWRzLzA0MTA4NzY3LTk1YjgtNDYzMi05YWFmLTgwNzgwZjIwMmFkMi8yM2FiMmVhOC00YjRhLTQ3ZTUtOGViOC00MjY3NDcyMzBkNzAvaW1hZ2UucG5nIiwidHlwZSI6ImF0dGFjaG1lbnQiLCJpYXQiOjE3ODA0NTQ5ODEsImV4cCI6MTc4MDQ1ODU4MX0.oRVYT22-2eH6XkMrCpCu2p94jCwse--nA07WXr1seI8 " =1080x447")

## 方式 3：提供账户密码+配合验证码接受

```bash
账户：
密码：
验证码接收方式：
```