# 🎨 Midjourney API

# Midjourney API调用说明

## 快速开始

### API秘钥配置

> 在使用前，请确保您有有效的API密钥。 调用（mj原生分组） {.is-info}

### 流程图概要

 ![](https://wiki.tu-zi.com/api/files.get?sig=eyJhbGciOiJIUzI1NiIsInR5cCI6IkpXVCJ9.eyJrZXkiOiJ1cGxvYWRzL2UxMjc0Y2E3LWNmZTEtNDdlOC04MjA0LTNhMDkzMTNlNzM4ZC9kMWYwNzQ4Ni01YmY2LTQyNWItYWNmMC01MDY0NDVkYmE0ZjUvaW1hZ2UucG5nIiwidHlwZSI6ImF0dGFjaG1lbnQiLCJpYXQiOjE3ODA0NTQ5MDQsImV4cCI6MTc4MDQ1ODUwNH0.LKvKCJkXuSaoLV6H2Spjc3Kb4qfjKj5Csyp9cwr2ynI " =934x1672")

## 1.任务提交

### 1.1 提交Imagine任务（文生图）

> `**POST**`    **/mj/submit/imagine**

**请求参数**

* Header 参数

| 参数  | 类型  | 是否必需 | 描述  | 示例值 |
|-----|-----|------|-----|-----|
| Authorization | string | 是    | API key | {{YOUR_API_KEY}} |

* Body 参数 application/json

| 参数  | 类型  | 是否必需 | 描述  | 示例值 |
|-----|-----|------|-----|-----|
| prompt | string | 是    | 提示词 | Cat |
| base64Array | array | 否    | 垫图 base64 数组 |     |
| notifyHook | string | 否    | 回调地址，为空时使用全局 notifyHook |     |
| noStorage | boolean | 否    | true：返回官方链接，默认值: false | false |
| botType | enum | 否    | bot 类型，mj(默认)或 niji | MID_JOURNEY、NIJI_JOURNEY |
| accountFilter | object | 否    | 账号筛选，modes array\[string\] 速度筛选 | {"accountFilter": {"modes": \["FAST", "RELAX"\]}} |
| state | string | 否    | 自定义参数 |     |

**请求示例**

```python
import http.client
import json

conn = http.client.HTTPSConnection("api.tu-zi.com")
payload = json.dumps({
   "botType": "MID_JOURNEY",
   "prompt": "Cat" #提示词
})
headers = {
   'Authorization': 'sk-****',
   'Content-Type': 'application/json'
}
conn.request("POST", "/mj/submit/imagine", payload, headers)
res = conn.getresponse()
data = res.read()
print(data.decode("utf-8"))
```

**返回结果** `{"code":1,"description":"Submit Success","properties":null,"result":"1756193671880652"}`

> 根据result中的任务id 到 获取任务代码中拿到图片链接 {.is-success}

**MJ绘图效果**    ![](https://tuziai.oss-cn-shenzhen.aliyuncs.com/wiki/code/mdjourney/cat_1.png)

 ![](https://tuziai.oss-cn-shenzhen.aliyuncs.com/wiki/code/mdjourney/cat_2.png)

 ![](https://tuziai.oss-cn-shenzhen.aliyuncs.com/wiki/code/mdjourney/cat_3.png)   ![](https://tuziai.oss-cn-shenzhen.aliyuncs.com/wiki/code/mdjourney/cat_4.png)

### 1.2 提交Blend任务（图像混合）

> `**POST**` **/mj/submit/blend**

**请求参数**

* Header 参数

| 参数  | 类型  | 是否必需 | 描述  | 示例值 |
|-----|-----|------|-----|-----|
| Authorization | string | 是    | API key | {{YOUR_API_KEY}} |

* Body 参数 application/json

| 参数  | 类型  | 是否必需 | 描述  | 示例值 |
|-----|-----|------|-----|-----|
| base64Array | array | 是    | 垫图 base64 数组 | \["data:image/png;base64,xxx1","data:image/png;base64,xxx2"\] |
| botType | enum | 否    | bot 类型，mj(默认)或 niji | MID_JOURNEY、NIJI_JOURNEY |
| dimensions | enum | 否    | 比例：PORTRAIT(2:3); SQUARE(1:1); LANDSCAPE(3:2) | SQUARE |
| notifyHook | string | 否    | 回调地址，为空时使用全局 notifyHook |     |
| state | string | 否    | 自定义参数 |     |

**请求示例**

```python
import http.client
import json
import base64
import mimetypes

# ====== 把本地图片文件转为 data URL ======
def file_to_data_url(path):
    # 根据扩展名猜 MIME，缺省按 png
    mime, _ = mimetypes.guess_type(path)
    if mime is None:
        mime = "image/png"
    with open(path, "rb") as f:
        b64 = base64.b64encode(f.read()).decode("utf-8")
    return f"data:{mime};base64,{b64}"

# 需要混合的本地图片文件（按需修改路径）
files = [
    "C:/Users/north/Pictures/Saved Pictures/assets_task_01k2gxmdfhff6rjdj61dpqj4ex_1755062162_src_0.png",
    "C:/Users/north/Pictures/Saved Pictures/assets_task_01k32t0w0hf649k4tz9xznrjf8_1755662369_src_0.png"
]

# 生成 base64Array
base64Array = [file_to_data_url(p) for p in files]

conn = http.client.HTTPSConnection("api.tu-zi.com")
payload = json.dumps({
   "botType": "MID_JOURNEY",
   "base64Array": base64Array,
   "dimensions": "LANDSCAPE"
})
headers = {
   "Authorization": "sk-****",   
   "Content-Type": "application/json"
}
conn.request("POST", "/mj/submit/blend", payload, headers)
res = conn.getresponse()
data = res.read()
print(data.decode("utf-8"))
```

**返回结果** `{"code":1,"description":"Submit Success","properties":null,"result":"1756193671880652"}`

> 根据result中的任务id 到 获取任务代码中拿到图片链接 {.is-success}

**MJ图混合效果** 原图   

 ![](https://wiki.tu-zi.com/api/files.get?sig=eyJhbGciOiJIUzI1NiIsInR5cCI6IkpXVCJ9.eyJrZXkiOiJ1cGxvYWRzL2UxMjc0Y2E3LWNmZTEtNDdlOC04MjA0LTNhMDkzMTNlNzM4ZC9kMWM0MzYxZi1hY2VhLTRlMmQtOGUyYy1lMTQ4ZDNkZGNiMDUvYTdjY2I3Njc0NzY3MjNmOWZiNTAwNGU2ZjM1YmMxZGMuanBnIiwidHlwZSI6ImF0dGFjaG1lbnQiLCJpYXQiOjE3ODA0NTQ5MDQsImV4cCI6MTc4MDQ1ODUwNH0.PnSS4qJ2uOkFYoEFW96bLlNNV6QNsD7jtbRJ85X0pic "left-50 =190x190") ![](https://tuziai.oss-cn-shenzhen.aliyuncs.com/wiki/code/mdjourney/fish.png "left-50 =190x190")


\

\

\
效果图    ![](https://tuziai.oss-cn-shenzhen.aliyuncs.com/wiki/code/mdjourney/zoo_all2.png)

### 1.3 提交Video任务 (图生视频）

> `**POST**` **/mj/submit/video**

**请求参数**

* Header 参数

| 参数  | 类型  | 是否必需 | 描述  | 示例值 |
|-----|-----|------|-----|-----|
| Authorization | string | 是    | API key | {{YOUR_API_KEY}} |

* Body 参数 application/json

| 参数  | 类型  | 是否必需 | 描述  | 示例值 |
|-----|-----|------|-----|-----|
| prompt | string | 是    | 提示词 | Cat |
| videoType | enum | 是    | 枚举值: vid_1.1_i2v_480、vid_1.1_i2v_720 | vid_1.1_i2v_720 |
| motion | enum | 是    | 枚举值: low、high | low |
| image | enum | 是    | 首帧图片，扩展时可为空，枚举值: url、base64 | url |
| endImage | string | 否    | 尾帧图片 |     |
| loop | boolean | 否    | 是否循环播放 |     |
| batchSize | enum | 否    | 枚举值: 1、2、4，默认值: 4 |     |
| action | string | 否    | 对视频任务进行操作。不为空时，index、taskId 必填，枚举值: extend |     |
| index | integer | 否    | 执行的视频索引号，>= 0 且 ≤ 3 |     |
| taskId | string | 否    | 需要操作的视频父任务 ID |     |
| state | string | 否    | 自定义参数 |     |
| notifyHook | string | 否    | 回调地址 |     |
| noStorage | boolean | 否    | True 时返回官方链接，默认值: false |     |

**请求示例**

```python
import http.client
import json
#
conn = http.client.HTTPSConnection("api.tu-zi.com")
payload = json.dumps({
   "prompt": "The rabbit in the picture is running",
   "motion": "low",
   "videoType": "vid_1.1_i2v_480",
   "image": "https://image.2025178.xyz/logo-tuzi.png"
})
headers = {
   'Authorization': 'sk-****',
   'Content-Type': 'application/json'
}
conn.request("POST", "/mj/submit/video", payload, headers)
res = conn.getresponse()
data = res.read()
print(data.decode("utf-8"))
```

### 1.4 提交Action任务

> `**POST**` **/mj/submit/action**

**请求参数**

* Header 参数

| 参数  | 类型  | 是否必需 | 描述  | 示例值 |
|-----|-----|------|-----|-----|
| Authorization | string | 是    | API key | {{YOUR_API_KEY}} |

* Body 参数 application/json

| 参数  | 类型  | 是否必需 | 描述  | 示例值 |
|-----|-----|------|-----|-----|
| chooseSameChannel | boolean | 可选   | 是否选择同一频道下的账号，默认只使用任务关联的账号 |     |
| customId | string | 必需   | 动作标识 | MJ::JOB::upsample::2::3dbbd469-36af-4a0f-8f02-df6c579e7011 |
| taskId | string | 必需   | 任务ID | 14001934816969359 |
| notifyHook | string | 可选   | 回调地址，为空时使用全局 notifyHook |     |
| state | string | 可选   | 自定义参数 |     |
| noStorage | boolean | 可选   | True 时返回原始图片链接 |     |
| enableRemix | boolean | 可选   | 是否使用 remix 模式，可强制绕过账号指定的 Remix 自动提交，默认值: false |     |

### 1.5 提交Describe任务

> `**POST**` **/mj/submit/describe**

**请求参数**

* Header 参数

| 参数  | 类型  | 是否必需 | 描述  | 示例值 |
|-----|-----|------|-----|-----|
| Authorization | string | 是    | API key | {{YOUR_API_KEY}} |

* Body 参数 application/json

| 参数  | 类型  | 是否必需 | 描述  | 枚举值 / 示例值 |
|-----|-----|------|-----|-----------|
| botType | enum | 可选   | bot 类型，mj(默认)或 niji | 枚举值: MID_JOURNEY, NIJI_JOURNEY |
| 示例值: MID_JOURNEY |     |      |     |           |
| base64 | string | 必需   | 图片 base64，和 link 二选一 | data:image/png;base64,xxx |
| link | string | 必需   | 图片 Link，和 base64 二选一 |           |
| notifyHook | string | 可选   | 回调地址，为空时使用全局 notifyHook |           |
| state | string | 可选   | 自定义参数 |           |

### 1.6 提交Modal任务

> `**POST**` **/mj/submit/modal**

**请求参数**

* Header 参数

| 参数  | 类型  | 是否必需 | 描述  | 示例值 |
|-----|-----|------|-----|-----|
| Authorization | string | 是    | API key | {{YOUR_API_KEY}} |

* Body 参数 application/json

| 参数  | 类型  | 是否必需 | 描述  | 示例值 |
|-----|-----|------|-----|-----|
| maskBase64 | string | 可选   | 局部重绘的蒙版 base64 |     |
| prompt | string | 可选   | 提示词 |     |
| taskId | string | 必需   | 任务 ID | 14001934816969359 |
| noStorage | boolean | 可选   | True 时返回原始图片链接 |     |

### 1.7 提交Edit任务

> `**POST**` **/mj/submit/edits**

**请求参数**

* Header 参数

| 参数  | 类型  | 是否必需 | 描述  | 示例值 |
|-----|-----|------|-----|-----|
| Authorization | string | 是    | API key | {{YOUR_API_KEY}} |

* Body 参数 application/json

| 参数  | 类型  | 是否必需 | 描述  | 枚举值 / 示例值 |
|-----|-----|------|-----|-----------|
| prompt | string | 必需   | 提示词 |           |
| image | enum | 必需   | 图片类型 | 枚举值: url, base64 |
| maskBase64 | string | 已废弃  | 蒙版 base64，编辑区域使用透明，可随意调节尺寸 |           |
| state | string | 可选   | 自定义参数 |           |
| notifyHook | string | 可选   | 回调地址 |           |
| noStorage | boolean | 可选   | True 时返回原始图片链接 |           |

## 2.任务查询

### 2.1 指定ID获取任务

> `**GET**` **/mj/task/{id}/fetch**

**请求参数**

* Header 参数

| 参数  | 类型  | 是否必需 | 描述  | 示例值 |
|-----|-----|------|-----|-----|
| Authorization | string | 是    | 在 Header 添加参数 Authorization，其值为在 Bearer 之后拼接 Token | Bearer \*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\* |

* Path 参数

| 参数  | 类型  | 是否必需 | 描述  | 示例值 |
|-----|-----|------|-----|-----|
| id  | string | 必需   | 任务 ID |     |

**请求示例**

```python
  import http.client

def fetch_task(task_id: str, api_key: str):
    conn = http.client.HTTPSConnection("api.tu-zi.com")
    payload = ''
    headers = {
        'Authorization': api_key
    }
    url = f"/mj/task/{task_id}/fetch"
    conn.request("GET", url, payload, headers)
    res = conn.getresponse()
    data = res.read()
    return data.decode("utf-8")

# 使用示例
if __name__ == "__main__":
    api_key = "sk-***"
    task_id = "1756201324617315"   # 可以换成其他 ID
    result = fetch_task(task_id, api_key)
    print(result)
```