# 🌐 Open WebUI 配置

# Open WebUI（兔子托管版）

## 1. 获取API Key

[🔐获取Key步骤](/doc/49b23582-9a23-4310-9188-d29448ae813c)

## 2. 访问OpenWebUI 托管版

### 1.直接在API站点访问

**1.1.找到箭头所指位置**

 ![](https://wiki.tu-zi.com/api/files.get?sig=eyJhbGciOiJIUzI1NiIsInR5cCI6IkpXVCJ9.eyJrZXkiOiJ1cGxvYWRzL2UxMjc0Y2E3LWNmZTEtNDdlOC04MjA0LTNhMDkzMTNlNzM4ZC8yYTZiYWNlMC04Njg0LTQ5OTctYWI0MS04YjE3NmQyNjk5NDAvaW1hZ2UucG5nIiwidHlwZSI6ImF0dGFjaG1lbnQiLCJpYXQiOjE3ODA0NTQ4NzYsImV4cCI6MTc4MDQ1ODQ3Nn0.Q5K0p1Uc1PLFsZ1NMlKyHQTwjBZxDujTc4hbyxIhj5M " =1788x836")

**1.2.点击OpenwebUI**

 ![](https://wiki.tu-zi.com/api/files.get?sig=eyJhbGciOiJIUzI1NiIsInR5cCI6IkpXVCJ9.eyJrZXkiOiJ1cGxvYWRzL2UxMjc0Y2E3LWNmZTEtNDdlOC04MjA0LTNhMDkzMTNlNzM4ZC82ZTRiMzU4MS1iZjBkLTRkNDUtYjMzZS1kZWJlY2Y0YTM2NDUvaW1hZ2UucG5nIiwidHlwZSI6ImF0dGFjaG1lbnQiLCJpYXQiOjE3ODA0NTQ4NzYsImV4cCI6MTc4MDQ1ODQ3Nn0.htD9jV4LIY3wpB2-c4orxF7JS8rHKEW-mKTx6SG-zC0 " =1788x832")

**1.3.选择正确的Key，然后点击确定**

 ![](https://wiki.tu-zi.com/api/files.get?sig=eyJhbGciOiJIUzI1NiIsInR5cCI6IkpXVCJ9.eyJrZXkiOiJ1cGxvYWRzL2UxMjc0Y2E3LWNmZTEtNDdlOC04MjA0LTNhMDkzMTNlNzM4ZC8wMDI2NTUwZS0wMmY2LTRiZWMtYmVjYy03MzQ2YzUzODdkYzYvaW1hZ2UucG5nIiwidHlwZSI6ImF0dGFjaG1lbnQiLCJpYXQiOjE3ODA0NTQ4NzYsImV4cCI6MTc4MDQ1ODQ3Nn0.ZX-XXtMFvRrI6Nl-SMJwa7pcuFSsay9s1Vf2WfIzB6M " =1917x851")

### 2.通过链接直接访问

**2.1访问链接**

访问链接直接输入https://openwebui.tu-zi.com/sso/login?apiKey=你的key

例如 https://openwebui.tu-zi.com/sso/login?apiKey=sk-xxxxxxxxxxxxxxxxxxxxxxxxxxx

## 3.成功进入，可以开始使用了

 ![](https://wiki.tu-zi.com/api/files.get?sig=eyJhbGciOiJIUzI1NiIsInR5cCI6IkpXVCJ9.eyJrZXkiOiJ1cGxvYWRzL2UxMjc0Y2E3LWNmZTEtNDdlOC04MjA0LTNhMDkzMTNlNzM4ZC85MDk0YjE5Mi0xY2Q3LTQ5NmItOWJjOS1hYmU2YmJlOTAyN2UvaW1hZ2UucG5nIiwidHlwZSI6ImF0dGFjaG1lbnQiLCJpYXQiOjE3ODA0NTQ4NzYsImV4cCI6MTc4MDQ1ODQ3Nn0.1B0eQ0yzV_53cI9ntjRjsHQrL2SXcoQp02suT_YBiHA " =1792x809")

# Open WebUI 官方配置

> Open WebUI 是一个可扩展的、功能丰富、用户友好的自托管 AI 平台，专为完全离线运行而设计。 它支持多种 LLM 运行环境，包括 Ollama 和 OpenAI 兼容的 API，并内置了用于 RAG 的推理引擎，是一个强大的 AI 部署解决方案。

## 1. 部署 Open WebUI

要将 **兔子API** 接入 **Open WebUI**，您需要先自部署 **Open WebUI**。

### 可选部署位置：

* 本机
* 服务器（推荐）

### 可选部署方式：

* uv
* Docker
* Docker Compose（推荐）

### 部署教程请查阅：

* [官方 GitHub 仓库](https://github.com/open-webui/open-webui/)
* [官方文档](https://docs.openwebui.com/)
* [官方文档 —— 中文版](https://openwebui-doc-zh.pages.dev/)

## 2. 获取 API key

* 进入 [兔子 API 网站的令牌页面](https://api.tu-zi.com/token)
* 点击 `添加令牌` ![openwebui_token.png](https://tuziai.oss-cn-shenzhen.aliyuncs.com/wiki/chat/openwebui_token_mod.png)
* 创建一个新的令牌

  
  1. 填写 令牌 `名称`（可以填入接入平台的名称），我们这个填入 **Open WebUI**
  2. 设置 令牌 `限额`，避免不经意间消耗过多额度
  3. 点击 `提交` <img src="/chat/openwebui_createtoken.png" alt="openwebui_createToken" style="zoom:38%;" />
* 复制 **API key** ![openwebui_copytoken.png](https://tuziai.oss-cn-shenzhen.aliyuncs.com/wiki/chat/openwebui_copytoken.png)

## 3. 接入 Open WebUI

* 进入 **Open WebUI**，注册并登录管理员账号，点击 `头像` -> `管理员面板` -> `设置` -> `外部连接`
* 如果未部署和配置 `Ollama`，建议关闭 `Ollama API`
* 点击 `OpenAI API` 下的 `+` ![openwebui_outsidelink.png](https://tuziai.oss-cn-shenzhen.aliyuncs.com/wiki/chat/openwebui_outsidelink.png)
* `URL` 填入 `https://api.tu-zi.com/v1`
* `密匙` 填入前面复制的 `兔子 API Key`
* 建议：如果您同时使用多个 API 提供商，可以在 `密匙` 这行后面的 `前置 ID` 填写 `tu-zi`，以避免同时使用不同 API 提供商但模型名称相同时，导致的冲突或混淆
* 在 `新增模型 ID` 输入框中，按需填写您所需的 **兔子 API** 模型名称，参见 [兔子模型列表](https://api.tu-zi.com/pricing)，点击加号完成添加
* 点击出现两次的 `保存` ![openwebui_editlink.png](https://tuziai.oss-cn-shenzhen.aliyuncs.com/wiki/chat/openwebui_editlink.png)
* 在 `设置` 的 `模型` 页面中，可以对刚才添加的模型进行编辑，如模型图像，模型名称，系统提示词，模型参数等。
* 可选：可以根据您的需求进行模型排序（排序入口在页面右上角的齿轮⚙️图标）

## 4. 开始使用

* 建议：所有设置完毕后，在使用前，强制刷新一次网页（<kbd>CTRL</kbd> + <kbd>SHIFT</kbd> + <kbd>R</kbd>）
* 点击 `新对话`，选择下拉列表中您添加和设置的 **兔子 API** 的模型名称，即可开始使用 **Open WebUI** 调用 **兔子API** 进行 AI 对话啦！🎉🎉🎉

</br>