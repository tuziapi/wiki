# 🎨 Cherry Studio + GPT-4o 生图

# 兔子API + cherry Studio实现gpt4o绘图教程

> 本教程基于Mac M3平台，但应该是其他Mac和Windows也通用的.

## Step1 注册&下载

注册兔子的api，可以用我的链接： https://api.tu-zi.com/register?aff=sShD

去官网下载最新Cherry Studio: https://cherry-ai.com/download

 ![](https://tuziai.oss-cn-shenzhen.aliyuncs.com/wiki/image-20250402191737724.png)

## Step2 获取你的api-key

https://api.tu-zi.com/token 在此处添加你的令牌，名称可以自定义，比如可以取不同名称来区分不同任务    ![](https://tuziai.oss-cn-shenzhen.aliyuncs.com/wiki/image-20250402192231166.png)

下面这里除了名称以外，按需填写，不懂的话默认就行了    ![](https://wiki.tu-zi.com/api/files.get?sig=eyJhbGciOiJIUzI1NiIsInR5cCI6IkpXVCJ9.eyJrZXkiOiJ1cGxvYWRzL2UxMjc0Y2E3LWNmZTEtNDdlOC04MjA0LTNhMDkzMTNlNzM4ZC83ZTM3OTM2Zi05MTcyLTRiN2QtODU4My1lZGNmMWJlODI3ZjAvaW1hZ2UucG5nIiwidHlwZSI6ImF0dGFjaG1lbnQiLCJpYXQiOjE3ODA0NTQ5MjYsImV4cCI6MTc4MDQ1ODUyNn0.ldg5iujTSKaC9dwMiJRj2uPHqZFFBUDyXfZHM_t_7uU " =380x560")

新建完你在这点个复制（下图红框），就会复制一个api-key，所谓密钥，到你的剪贴板上    ![](https://wiki.tu-zi.com/api/files.get?sig=eyJhbGciOiJIUzI1NiIsInR5cCI6IkpXVCJ9.eyJrZXkiOiJ1cGxvYWRzL2UxMjc0Y2E3LWNmZTEtNDdlOC04MjA0LTNhMDkzMTNlNzM4ZC8yM2MxYWVjZC0zMjYwLTRjMDEtODRhNi0zNThkNDY0ODdhMjIvaW1hZ2UucG5nIiwidHlwZSI6ImF0dGFjaG1lbnQiLCJpYXQiOjE3ODA0NTQ5MjYsImV4cCI6MTc4MDQ1ODUyNn0.f3OL-K38D2hj9TVCSWtO1i78f8rmjLzeoEGYP6g43JM " =3804x496")

## Step 3 配置Cherry Studio

打开设置    ![](https://wiki.tu-zi.com/api/files.get?sig=eyJhbGciOiJIUzI1NiIsInR5cCI6IkpXVCJ9.eyJrZXkiOiJ1cGxvYWRzL2UxMjc0Y2E3LWNmZTEtNDdlOC04MjA0LTNhMDkzMTNlNzM4ZC9kM2EzMDZjNi01NDFiLTQwMTAtYWVjMC0wYTBhNmQ3ODE1MmIvaW1hZ2UucG5nIiwidHlwZSI6ImF0dGFjaG1lbnQiLCJpYXQiOjE3ODA0NTQ5MjYsImV4cCI6MTc4MDQ1ODUyNn0.fRiqKB_eikce8pYWiCz6ne6XTl44XQDhpS1v61H8w4w " =2858x1980")

添加一个提供商    ![](https://tuziai.oss-cn-shenzhen.aliyuncs.com/wiki/image-20250402192644299.png)    ![](https://wiki.tu-zi.com/api/files.get?sig=eyJhbGciOiJIUzI1NiIsInR5cCI6IkpXVCJ9.eyJrZXkiOiJ1cGxvYWRzL2UxMjc0Y2E3LWNmZTEtNDdlOC04MjA0LTNhMDkzMTNlNzM4ZC9iZjA0MGRhYy03ZmIzLTQ0NTUtOTU0NC02ODEyODEyZTI4MTMvaW1hZ2UucG5nIiwidHlwZSI6ImF0dGFjaG1lbnQiLCJpYXQiOjE3ODA0NTQ5MjYsImV4cCI6MTc4MDQ1ODUyNn0.9fuXKrJNrnh7uzhcWJldIQM25MBnkTVgzXirLHlgQxw " =722x480")

填入各个信息    ![](https://tuziai.oss-cn-shenzhen.aliyuncs.com/wiki/image-20250402192924069.png " =532x369")

然后记得填入模型名称，你要gpt4o绘画就可以填如下几个，如有变动请关注tuzi的群。如果你想纯聊天，可以有别的选择!!

点击上面的按钮添加模型，模型id可以在兔子api站控制台找到    ![](https://wiki.tu-zi.com/api/files.get?sig=eyJhbGciOiJIUzI1NiIsInR5cCI6IkpXVCJ9.eyJrZXkiOiJ1cGxvYWRzL2UxMjc0Y2E3LWNmZTEtNDdlOC04MjA0LTNhMDkzMTNlNzM4ZC8zNjk4MTQ5Yy04ODg3LTRjYWItODY4Zi1jZWM4M2IwYWRjZjgvaW1hZ2UucG5nIiwidHlwZSI6ImF0dGFjaG1lbnQiLCJpYXQiOjE3ODA0NTQ5MjYsImV4cCI6MTc4MDQ1ODUyNn0.bOPa782xsblmDbPZ3v3ir4IinGu4spTQdxmG812OsOM " =646x358")

## Step 4开始对话

添加个新助手，里面选择刚刚注册的模型即可    ![](https://tuziai.oss-cn-shenzhen.aliyuncs.com/wiki/image-20250402193339749.png " =532x369")