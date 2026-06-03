# 🔧 n8n 配置

{ "model": "nano-banana", "messages": \[ { "role": "user", "content": "@sama 在厕所里面大声高歌怒放的生命" } \], "stream": true }

# 准备阶段

## 在 api.tu-zi.com 申请准备好 api key

 ![wechat_2025-07-22_202603_521.png](https://tuziai.oss-cn-shenzhen.aliyuncs.com/wiki/wechat_2025-07-22_202603_521.png)

 ![951f1f62-9c54-4603-902a-a556d7b4c4dd.png](https://tuziai.oss-cn-shenzhen.aliyuncs.com/wiki/951f1f62-9c54-4603-902a-a556d7b4c4dd.png)

创建好之后，在 API 令牌列表页复制新建好的令牌 api key 备用

## n8n 的安装

n8n 官网： https://n8n.io/ n8n 中文知识站： https://docs.n8ncn.io/choose-n8n/ n8n workflow 下载站： https://n8n.io/workflows/

### n8n 在线版

#### 请直接在官网注册在线版。

 ![wechat_2025-07-22_203713_913.png](https://tuziai.oss-cn-shenzhen.aliyuncs.com/wiki/wechat_2025-07-22_203713_913.png)

#### 登录

登录之后如图，后面的部分就跟本地版区别不大了

 ![wechat_2025-07-22_203952_853.png](https://tuziai.oss-cn-shenzhen.aliyuncs.com/wiki/wechat_2025-07-22_203952_853.png)

### docker 一键安装

#### 安装

```bash
docker run -d --name n8n --restart=always -p 5678:5678 -e DB_TYPE=sqlite -e N8N_HOST=n8n.localhost -e N8N_PORT=5678 -e NODE_ENV=production -e N8N_PROTOCOL=http -e N8N_LOG_LEVEL=debug -v .n8n-data:/home/node/.n8n n8nio/n8n:latest
```

#### 注册

第一次打开登录的时候会提示注册管理员账号，请酌情填写 密码需要至少 字符数字还有一个特殊符号

 ![wechat_2025-07-22_204127_791.png](https://tuziai.oss-cn-shenzhen.aliyuncs.com/wiki/wechat_2025-07-22_204127_791.png)

#### 登录

登录之后会提示你填写问卷，随便填一填就好

 ![wechat_2025-07-22_204205_786.png](https://tuziai.oss-cn-shenzhen.aliyuncs.com/wiki/wechat_2025-07-22_204205_786.png)

### 其他安装方式

请参考 https://n8n.io/ 官网进行安装

# N8N 配置

## 连接 tu-zi 的 openai

 ![wechat_2025-07-22_204342_388.png](https://tuziai.oss-cn-shenzhen.aliyuncs.com/wiki/wechat_2025-07-22_204342_388.png)

 ![wechat_2025-07-22_204520_591.png](https://tuziai.oss-cn-shenzhen.aliyuncs.com/wiki/wechat_2025-07-22_204520_591.png)

 ![wechat_2025-07-22_205118_686.png](https://tuziai.oss-cn-shenzhen.aliyuncs.com/wiki/wechat_2025-07-22_205118_686.png)

## 方式一（对话生成）

 ![wechat_2025-07-22_205149_412.png](https://tuziai.oss-cn-shenzhen.aliyuncs.com/wiki/wechat_2025-07-22_205149_412.png)

 ![wechat_2025-07-22_205309_076.png](https://tuziai.oss-cn-shenzhen.aliyuncs.com/wiki/wechat_2025-07-22_205309_076.png)

 ![wechat_2025-07-22_205413_463.png](https://tuziai.oss-cn-shenzhen.aliyuncs.com/wiki/wechat_2025-07-22_205413_463.png)

 ![wechat_2025-07-22_205552_210.png](https://tuziai.oss-cn-shenzhen.aliyuncs.com/wiki/wechat_2025-07-22_205552_210.png)

 ![wechat_2025-07-22_205711_439.png](https://tuziai.oss-cn-shenzhen.aliyuncs.com/wiki/wechat_2025-07-22_205711_439.png)

 ![wechat_2025-07-22_205814_558.png](https://tuziai.oss-cn-shenzhen.aliyuncs.com/wiki/wechat_2025-07-22_205814_558.png)

 ![wechat_2025-07-22_205950_792.png](https://tuziai.oss-cn-shenzhen.aliyuncs.com/wiki/wechat_2025-07-22_205950_792.png)

## 测试

 ![9c653933-3128-42d7-9efe-14c2170f52c5.png](https://tuziai.oss-cn-shenzhen.aliyuncs.com/wiki/9c653933-3128-42d7-9efe-14c2170f52c5.png)

# 总结和拓展

至此，n8n 上面添加 api.tu-zi.com 的 key 并进行简单测试的教程就结束了。 建议新手阅读下面的文章来创建复杂的 ai 应用。

以下是精选的 n8n 学习资源网站，涵盖官方平台、中文社区、技术**博客与开源项目，均**提供中文内容或适配中文用户需求：

## 📊 n8n 学习资源网站一览表

n8n 官方文档 最权威的英文技术文档，涵盖安装、节点配置、API 调用及 AI 集成指南，推荐搭配浏览器翻译插件使用 https://docs.n8n.io

n8n 工作流模板库 官方提供的 1700+ 自动化模板，含电商、客服、AI 代理等场景，可直接导入使用 https://n8n.io/workflows

n8n 中文社区 (n8nclub) 国内活跃论坛，提供汉化教程、部署指南及企业案例解析，支持问题实时交流 https://www.n8nclub.com.cn

微信公众号「AI打工笔记」 连载《零编程学 n8n》系列，从安装到高阶案例（如 Gmail→Sheets→Telegram 通知流） http://mp.weixin.qq.com/s?__biz=MzU1NzY0ODI0MQ==&mid=2247483728&idx=1

GitHub 社区节点 Top 100 热门第三方节点列表（如 WhatsApp 集成、网页爬虫、文档生成），含下载量与更新状态 https://github.com/HalyardConsulting/top-100-n8n-community-nodes

微信公众号「心橙AI智能体」 零基础保姆级教程，含图文详解：官网注册→本地部署→首个工作流搭建（如Gmail自动化） http://mp.weixin.qq.com/s?__biz=MjM5ODAxMTQ1NA==&mid=2247484806&idx=1

CSDN「疯哥AI」专栏 通俗对比n8n/Zapier/Make，解析AI自动化价值，附小白避坑指南和免费模板 https://blog.csdn.net/CM20202222/article/details/149250948

CSDN「小破站」实战指南 10分钟Docker部署教程 + Gmail→表格→通知全流程演示，解决90%权限问题 https://blog.csdn.net/Mrxiao_bo/article/details/147218120

当然你也可以直接在 https://n8n.io/workflows/ 上搜索并导入

## 从 workflow 搜索并导入

 ![wechat_2025-07-22_211907_548.png](https://tuziai.oss-cn-shenzhen.aliyuncs.com/wiki/wechat_2025-07-22_211907_548.png)

 ![wechat_2025-07-22_212059_669.png](https://tuziai.oss-cn-shenzhen.aliyuncs.com/wiki/wechat_2025-07-22_212059_669.png)

 ![wechat_2025-07-22_212120_914.png](https://tuziai.oss-cn-shenzhen.aliyuncs.com/wiki/wechat_2025-07-22_212120_914.png)

 ![wechat_2025-07-22_212249_364.png](https://tuziai.oss-cn-shenzhen.aliyuncs.com/wiki/wechat_2025-07-22_212249_364.png)

 ![wechat_2025-07-22_212337_908.png](https://tuziai.oss-cn-shenzhen.aliyuncs.com/wiki/wechat_2025-07-22_212337_908.png)

 ![wechat_2025-07-22_212547_665.png](https://tuziai.oss-cn-shenzhen.aliyuncs.com/wiki/wechat_2025-07-22_212547_665.png)


## 方式二（图像生成）：HTTP Request 调用 nano-banana

**全文JSON模板**

```json
{
  "nodes": [
    {
      "parameters": {
        "method": "POST",
        "url": "https://api.tu-zi.com/v1/chat/completions",
        "authentication": "genericCredentialType",
        "genericAuthType": "httpHeaderAuth",
        "sendBody": true,
        "specifyBody": "json",
        "jsonBody": "{\n    \"model\": \"nano-banana\",\n    \"messages\": [\n        {\n            \"role\": \"user\",\n            \"content\": \"@sama 在厕所里面大声高歌怒放的生命\"\n        }\n    ],\n    \"stream\": true\n}",
        "options": {
          "redirect": {
            "redirect": {}
          }
        }
      },
      "type": "n8n-nodes-base.httpRequest",
      "typeVersion": 4.3,
      "position": [
        304,
        656
      ],
      "id": "0979364a-72a8-40b3-ba98-f690f6cc7319",
      "name": "HTTP Request",
      "credentials": {
        "httpHeaderAuth": {
          "id": "Ti37ZWgY3WKRmNYi",
          "name": "default"
        }
      }
    },
    {
      "parameters": {
        "operation": "html",
        "options": {}
      },
      "type": "n8n-nodes-base.convertToFile",
      "typeVersion": 1.1,
      "position": [
        528,
        656
      ],
      "id": "ef38a4a8-18c7-45ac-8d8b-444a10cbb888",
      "name": "Convert to File"
    },
    {
      "parameters": {},
      "name": "手动触发",
      "type": "n8n-nodes-base.manualTrigger",
      "typeVersion": 1,
      "position": [
        80,
        656
      ],
      "id": "0ecf770e-3335-43ff-b3d2-60d2c2eecf1a"
    }
  ],
  "connections": {
    "HTTP Request": {
      "main": [
        [
          {
            "node": "Convert to File",
            "type": "main",
            "index": 0
          }
        ]
      ]
    },
    "手动触发": {
      "main": [
        [
          {
            "node": "HTTP Request",
            "type": "main",
            "index": 0
          }
        ]
      ]
    }
  },
  "pinData": {},
  "meta": {
    "instanceId": "ef097262c0dd328289c8bc2e01d37ee7957c2ec38ed7249ad759c221db05657c"
  }
}
```

**HTTP Request 配置**

 ![](https://wiki.tu-zi.com/api/files.get?sig=eyJhbGciOiJIUzI1NiIsInR5cCI6IkpXVCJ9.eyJrZXkiOiJ1cGxvYWRzLzM4NTg0YjhiLTliMmYtNDQ1ZS1iOTA3LTkwNGNlOTRkOGJlZC9lMDk5NzQ2MC00NmNkLTQ5M2YtOGY4ZS1kMzg5ZTI4OTViMDIvaW1hZ2UucG5nIiwidHlwZSI6ImF0dGFjaG1lbnQiLCJpYXQiOjE3ODA0NTQ4NjMsImV4cCI6MTc4MDQ1ODQ2M30.u7ulGFlgJvDRM7Ya9gJaMIxvYv2SgdBnvr7V26moHTs " =1623x846")

 ![](https://wiki.tu-zi.com/api/files.get?sig=eyJhbGciOiJIUzI1NiIsInR5cCI6IkpXVCJ9.eyJrZXkiOiJ1cGxvYWRzLzM4NTg0YjhiLTliMmYtNDQ1ZS1iOTA3LTkwNGNlOTRkOGJlZC81MTBmMjVlNS02NWU2LTQ3MDMtOTFmZS0wYTE1OTI1NmM4ZmEvaW1hZ2UucG5nIiwidHlwZSI6ImF0dGFjaG1lbnQiLCJpYXQiOjE3ODA0NTQ4NjMsImV4cCI6MTc4MDQ1ODQ2M30.X738IOL-xKiCDnYo5ByKM2iOmC-qR3lKjkMo2rkFUcI " =1542x789")

**Body JSON**

```json
{
    "model": "nano-banana",
    "messages": [
        {
            "role": "user",
            "content": "@sama 在厕所里面大声高歌怒放的生命"
        }
    ],
    "stream": true
}
```

**效果图**

 ![](https://wiki.tu-zi.com/api/files.get?sig=eyJhbGciOiJIUzI1NiIsInR5cCI6IkpXVCJ9.eyJrZXkiOiJ1cGxvYWRzLzM4NTg0YjhiLTliMmYtNDQ1ZS1iOTA3LTkwNGNlOTRkOGJlZC84YTJhM2UxMy1iOTE1LTQyNjEtODRmZC05MDgzMWYwMWViMGQvaW1hZ2UucG5nIiwidHlwZSI6ImF0dGFjaG1lbnQiLCJpYXQiOjE3ODA0NTQ4NjMsImV4cCI6MTc4MDQ1ODQ2M30.YERsz1jd3erMGETRoEEfD5Qm3HZOukC_0u3hCO-85TY " =958x276")

 ![](https://wiki.tu-zi.com/api/files.get?sig=eyJhbGciOiJIUzI1NiIsInR5cCI6IkpXVCJ9.eyJrZXkiOiJ1cGxvYWRzLzM4NTg0YjhiLTliMmYtNDQ1ZS1iOTA3LTkwNGNlOTRkOGJlZC8zODBkYjJmMS1hMGVlLTQxNWItOTRiNy0wMzI0NDM4YzFjYjAvaW1hZ2UucG5nIiwidHlwZSI6ImF0dGFjaG1lbnQiLCJpYXQiOjE3ODA0NTQ4NjMsImV4cCI6MTc4MDQ1ODQ2M30.fC2tfJkmu3DGafZVQQg2D7e09UHuvF1D6IdqaK44JLg " =1090x471")

 ![](https://wiki.tu-zi.com/api/files.get?sig=eyJhbGciOiJIUzI1NiIsInR5cCI6IkpXVCJ9.eyJrZXkiOiJ1cGxvYWRzLzM4NTg0YjhiLTliMmYtNDQ1ZS1iOTA3LTkwNGNlOTRkOGJlZC8yZTFjMzhlMS1kZDNmLTQ2MjgtOWYwZS04NmRjNDI2YzI3NjkvaW1hZ2UucG5nIiwidHlwZSI6ImF0dGFjaG1lbnQiLCJpYXQiOjE3ODA0NTQ4NjMsImV4cCI6MTc4MDQ1ODQ2M30.XBuu8I1rVpPHw8NRKe8gW_kMZJE353ikxKuEr5o9m_0 " =1491x785")

 ![](https://wiki.tu-zi.com/api/files.get?sig=eyJhbGciOiJIUzI1NiIsInR5cCI6IkpXVCJ9.eyJrZXkiOiJ1cGxvYWRzLzM4NTg0YjhiLTliMmYtNDQ1ZS1iOTA3LTkwNGNlOTRkOGJlZC85ZGVjZmQyYy00OWQ5LTQyMWItOTg2OC0wMjFlMDE2NDY3YmEvaW1hZ2UucG5nIiwidHlwZSI6ImF0dGFjaG1lbnQiLCJpYXQiOjE3ODA0NTQ4NjMsImV4cCI6MTc4MDQ1ODQ2M30.gi5jnzzdBTu_euQffow6BCKMbqaCIAA0V1caU5Toc-E " =1192x906")


## 方式三（视频生成）：HTTP Request 调用 sora-2


**default分组用<https://api.tu-zi.com/v1/videos/{video_id}>查询视频**

**原价分组用<https://api.tu-zi.com/v1/videos/{task_id}/content>下载视频**


**全文JSON模板**

```json
{
  "nodes": [
    {
      "parameters": {},
      "name": "手动触发",
      "type": "n8n-nodes-base.manualTrigger",
      "typeVersion": 1,
      "position": [
        -2704,
        1440
      ],
      "id": "51dd41b7-9960-43cf-b4ff-f53ec616cead"
    },
    {
      "parameters": {
        "jsCode": "// 定义异步延迟函数\nasync function delay(ms) {\n  return new Promise(resolve => setTimeout(resolve, ms));\n}\n\nconsole.log('开始延迟，当前时间：', new Date().toLocaleString());\n// 延迟6秒（6000毫秒）\nawait delay(6 * 1000);\nconsole.log('延迟结束，当前时间：', new Date().toLocaleString());\n\n// 【关键】n8n的Code节点v2版本，直接返回普通对象也可，但确保至少有一个有效项\nconst outputData = {\n  message: '6秒异步延迟完成',\n  triggerTime: new Date().toISOString()\n};\n\n// 两种合法格式都可以（选一种即可）\nreturn [outputData]; // 简化格式（推荐）\n// return [{ json: outputData }]; // 完整格式"
      },
      "id": "f9abec76-1027-43ee-b098-a8bd7646416c",
      "name": "Code - 1分钟异步延迟",
      "type": "n8n-nodes-base.code",
      "typeVersion": 2,
      "position": [
        -2304,
        1440
      ]
    },
    {
      "parameters": {
        "method": "POST",
        "url": "https://api.tu-zi.com/v1/videos",
        "sendHeaders": true,
        "headerParameters": {
          "parameters": [
            {
              "name": "Authorization",
              "value": "Bearer sk-Uh7cKOtamFGnfjekQb7MqtHxCqfiSW0IdUQoV80hx2anZNiD"
            }
          ]
        },
        "sendBody": true,
        "bodyParameters": {
          "parameters": [
            {
              "name": "model",
              "value": "sora-2"
            },
            {
              "name": "prompt",
              "value": "请生成兔子笑"
            },
            {
              "name": "seconds",
              "value": "4"
            },
            {
              "name": "size",
              "value": "1280x720"
            }
          ]
        },
        "options": {}
      },
      "type": "n8n-nodes-base.httpRequest",
      "typeVersion": 4.3,
      "position": [
        -2480,
        1440
      ],
      "id": "f41edc86-b3f5-4563-b3ca-c36e4132dc20",
      "name": "generate"
    },
    {
      "parameters": {
        "url": "https://api.tu-zi.com/v1/videos/{{ $('generate').item.json.id }}/content",
        "sendHeaders": true,
        "headerParameters": {
          "parameters": [
            {
              "name": "Authorization",
              "value": "Bearer sk-Uh7cKOtamFGnfjekQb7MqtHxCqfiSW0IdUQoV80hx2anZNiD"
            }
          ]
        },
        "options": {}
      },
      "type": "n8n-nodes-base.httpRequest",
      "typeVersion": 4.3,
      "position": [
        -2128,
        1440
      ],
      "id": "a51a53d1-b489-4762-9b88-d648e48c18c0",
      "name": "download"
    }
  ],
  "connections": {
    "手动触发": {
      "main": [
        [
          {
            "node": "generate",
            "type": "main",
            "index": 0
          }
        ]
      ]
    },
    "Code - 1分钟异步延迟": {
      "main": [
        [
          {
            "node": "download",
            "type": "main",
            "index": 0
          }
        ]
      ]
    },
    "generate": {
      "main": [
        [
          {
            "node": "Code - 1分钟异步延迟",
            "type": "main",
            "index": 0
          }
        ]
      ]
    },
    "download": {
      "main": [
        []
      ]
    }
  },
  "pinData": {},
  "meta": {
    "templateCredsSetupCompleted": true,
    "instanceId": "ef097262c0dd328289c8bc2e01d37ee7957c2ec38ed7249ad759c221db05657c"
  }
}
```

**HTTP Request 配置**


<https://api.tu-zi.com/v1/videos/{task_id}/content>

generator request : <https://api.tu-zi.com/v1/videos>

download request : <https://api.tu-zi.com/v1/videos/{{ $('generate').item.json.id }}/content>


**generator Body Parameters**

```json
Body Parameters
Name
model
Value
sora-2
Name
prompt
Value
请生成兔子笑
Name
seconds
Value
4
Name
size
Value
1280x720
```

**效果图**

 ![](https://wiki.tu-zi.com/api/files.get?sig=eyJhbGciOiJIUzI1NiIsInR5cCI6IkpXVCJ9.eyJrZXkiOiJ1cGxvYWRzLzM4NTg0YjhiLTliMmYtNDQ1ZS1iOTA3LTkwNGNlOTRkOGJlZC81MTRiNzljMS1mZTAwLTQ0NzYtYWE2Ny00YTE5ODBjNzJhNWYvaW1hZ2UucG5nIiwidHlwZSI6ImF0dGFjaG1lbnQiLCJpYXQiOjE3ODA0NTQ4NjMsImV4cCI6MTc4MDQ1ODQ2M30.U3juszyqT6ZzZG-kWIDqwtFQ-prOmrwf9uN15bFxiJY " =1159x557")

 ![](https://wiki.tu-zi.com/api/files.get?sig=eyJhbGciOiJIUzI1NiIsInR5cCI6IkpXVCJ9.eyJrZXkiOiJ1cGxvYWRzLzM4NTg0YjhiLTliMmYtNDQ1ZS1iOTA3LTkwNGNlOTRkOGJlZC8zMTk2ZmViMi1lMmMwLTQ1MTUtOGE2Yi1lZTlkMzEzYjg1MTAvaW1hZ2UucG5nIiwidHlwZSI6ImF0dGFjaG1lbnQiLCJpYXQiOjE3ODA0NTQ4NjMsImV4cCI6MTc4MDQ1ODQ2M30.4hdmNw4KHC_4f_RqlWUOqT1u3lPdK6O2M-xRcRHVpqA " =1227x597")

下载即可

 ![](https://wiki.tu-zi.com/api/files.get?sig=eyJhbGciOiJIUzI1NiIsInR5cCI6IkpXVCJ9.eyJrZXkiOiJ1cGxvYWRzLzM4NTg0YjhiLTliMmYtNDQ1ZS1iOTA3LTkwNGNlOTRkOGJlZC8xYzljMzYzMi1jZDJlLTQ2YjctYTVkNC0xMmZkMmE2NWZmMzAvaW1hZ2UucG5nIiwidHlwZSI6ImF0dGFjaG1lbnQiLCJpYXQiOjE3ODA0NTQ4NjMsImV4cCI6MTc4MDQ1ODQ2M30.Z8kqe85BGLGQsaSDgprklg4mqzZh8kRaG4KnY-Wea6E " =1520x826")

 ![](https://wiki.tu-zi.com/api/files.get?sig=eyJhbGciOiJIUzI1NiIsInR5cCI6IkpXVCJ9.eyJrZXkiOiJ1cGxvYWRzLzM4NTg0YjhiLTliMmYtNDQ1ZS1iOTA3LTkwNGNlOTRkOGJlZC9iMzMyZDBiOC05Njc2LTQwMmMtOWUwZi00ZDc1MjhiNjZkYTcvaW1hZ2UucG5nIiwidHlwZSI6ImF0dGFjaG1lbnQiLCJpYXQiOjE3ODA0NTQ4NjMsImV4cCI6MTc4MDQ1ODQ2M30.V0m7LvSF0HCqwGWobY-YE0DWY29eLDeqYeIWO4yZjNE " =1280x720")


## **组件下载**

 ![](https://wiki.tu-zi.com/api/files.get?sig=eyJhbGciOiJIUzI1NiIsInR5cCI6IkpXVCJ9.eyJrZXkiOiJ1cGxvYWRzLzM4NTg0YjhiLTliMmYtNDQ1ZS1iOTA3LTkwNGNlOTRkOGJlZC8yOTc2YWU3OS05MjJmLTRiMmItYjZhNy04MDk2OGY2MmFmYTkvaW1hZ2UucG5nIiwidHlwZSI6ImF0dGFjaG1lbnQiLCJpYXQiOjE3ODA0NTQ4NjMsImV4cCI6MTc4MDQ1ODQ2M30.1mc8ix0G5uoq67bYDGM5glaplfsXkn1KgPeIkWv3Rfo " =434x561")

 ![](https://wiki.tu-zi.com/api/files.get?sig=eyJhbGciOiJIUzI1NiIsInR5cCI6IkpXVCJ9.eyJrZXkiOiJ1cGxvYWRzLzM4NTg0YjhiLTliMmYtNDQ1ZS1iOTA3LTkwNGNlOTRkOGJlZC80Mzc0YzdmZC01MTQyLTRlODYtYWJkMi00MmE2MjIzYWFkM2MvaW1hZ2UucG5nIiwidHlwZSI6ImF0dGFjaG1lbnQiLCJpYXQiOjE3ODA0NTQ4NjMsImV4cCI6MTc4MDQ1ODQ2M30.MmDtnQAl1FcrKD9PxW2BUiSyCV17goAviN-pYj-6UH8 " =1585x850")

下载成功

 ![](https://wiki.tu-zi.com/api/files.get?sig=eyJhbGciOiJIUzI1NiIsInR5cCI6IkpXVCJ9.eyJrZXkiOiJ1cGxvYWRzLzM4NTg0YjhiLTliMmYtNDQ1ZS1iOTA3LTkwNGNlOTRkOGJlZC80YmNiZDhkYy1iOTNhLTQzOTQtODNkNS1lMThjZDc2YTY5YTkvaW1hZ2UucG5nIiwidHlwZSI6ImF0dGFjaG1lbnQiLCJpYXQiOjE3ODA0NTQ4NjMsImV4cCI6MTc4MDQ1ODQ2M30.p7930uelAJ-IU_rlazJA05iXvwMLBjkWLUsN0iTCOgQ " =1551x758")


\

\