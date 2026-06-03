# 💻 Cursor 配置

Cursor


1. 地址：https://www.cursor.com/cn
2. 介绍 Cursor 是一个AI工具，主要用于帮助开发者更高效地编写代码。它可以智能地理解你的编程需求，提供代码建议、自动完成以及实时的错误检测等功能。简单来说，Cursor 就像是一个聪明的编程助手，帮助你更快地写出更好的代码，让编程变得更加轻松！ Cursor集成了 GPT、Claude 等先进的LLM，页面布局跟 VSCode 基本一致。\n注：新版 cursor 已经不支持外接第三方的 Claude 模型，以及不支持外接第三方的模型跑 agent 模型
3. 搭配兔子 API 使用 LLM ● 点击官网地址，进行程序的下载安装 ![](https://pic1.imgdb.cn/item/67bdbd71d0e0a243d40578e1.png) ● 安装成功后，根据提示进行选择即可，登录完成后，进行后续操作 ![](https://pic1.imgdb.cn/item/67bdbd71d0e0a243d40578e2.png) ● 在首页右上角点击齿轮进入设置页面 ![](https://pic1.imgdb.cn/item/67bdbd72d0e0a243d40578e3.png) ● 点击 Models 进行模型的选择 ![](https://pic1.imgdb.cn/item/67bdbd70d0e0a243d40578e0.png) ● 在 Open API key 下方输入兔子 API 的 APIKEY，以及点击 Override OpenAl Base URL，选择 API 地址，最后点击Verify验证通过即可 ![](https://pic1.imgdb.cn/item/67bdbda1d0e0a243d40578f3.png)

* API地址一定拼接加上v1 完成地址: https://api.tu-zi.com/v1

API-KEY获取步骤

* 访问官方API平台：[api.tu-zi.com](https://api.tu-zi.com)
* 登录后进入密钥管理面板创建API-KEY
* 在钱包内完成充值（新用户有0.4美金赠送）

> 📌 详细说明可参考：[兔子自带的nextchat配置说明](https://tuziai.oss-cn-shenzhen.aliyuncs.com/wiki/zh/Chat/nextchat)

● 配置完毕后，想要使用 Claude-Sonnet-4 模型 还需要如下配置


1. 点击 `+ Add model ` 按钮 分别填写名字如下的两个模型 `Cursor-c4` 和 `Cursor-c4-thinking` ![微信截图_20250527125510.png](https://tuziai.oss-cn-shenzhen.aliyuncs.com/wiki/chat/curosr/%E5%BE%AE%E4%BF%A1%E6%88%AA%E5%9B%BE_20250527125510.png)

● 并确保 Cursor Settings > Models 勾选了 这两个模型 `Cursor-c4` 和 `Cursor-c4-thinking` ● 在 ask 和 agent 里选择 `Cursor-c4` 和 `Cursor-c4-thinking`     ![微信截图_20250527125841.png](https://tuziai.oss-cn-shenzhen.aliyuncs.com/wiki/chat/curosr/%E5%BE%AE%E4%BF%A1%E6%88%AA%E5%9B%BE_20250527125841.png)     ![企业微信截图_17483210933552.png](https://tuziai.oss-cn-shenzhen.aliyuncs.com/wiki/chat/curosr/%E4%BC%81%E4%B8%9A%E5%BE%AE%E4%BF%A1%E6%88%AA%E5%9B%BE_17483210933552.png)