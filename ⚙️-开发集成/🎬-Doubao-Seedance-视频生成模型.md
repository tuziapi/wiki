# 🎬 Doubao Seedance 视频生成模型

Seedance 1.5 Pro 是字节跳动豆包大模型团队最新推出的视频生成基础模型。Seedance 1.5 Pro作为该模型系列的大参数量版本，具备独特的多镜头叙事能力，在各维度表现出色。它在语义理解与指令遵循能力上取得突破，能生成运动流畅、细节丰富、风格多样且具备影视级美感的 1080P 高清视频。


# 接口调用

## 1. 配置 api key


1.  登录   <https://api.tu-zi.com/token>
2. 点击控制台添加令牌

 ![](https://wiki.tu-zi.com/api/files.get?sig=eyJhbGciOiJIUzI1NiIsInR5cCI6IkpXVCJ9.eyJrZXkiOiJ1cGxvYWRzL2I3MTgwNDFlLWUwNjItNDRlMy1iNTljLTlkYzliNjNjODczMi8wNzI2ZTlhMS1iMTkzLTRkMjktODQ4Mi01Y2MxNjY3NGJjMjgvMi5wbmciLCJ0eXBlIjoiYXR0YWNobWVudCIsImlhdCI6MTc4MDQ1NDkwNiwiZXhwIjoxNzgwNDU4NTA2fQ.Li4CUID3EYXnit8J3SshX0McTN5fXvjaqPGLlwG_4qw " =1254x709")


\
3\. 添加一个无限制令牌/ 可以自由设置


 ![](https://wiki.tu-zi.com/api/files.get?sig=eyJhbGciOiJIUzI1NiIsInR5cCI6IkpXVCJ9.eyJrZXkiOiJ1cGxvYWRzL2I3MTgwNDFlLWUwNjItNDRlMy1iNTljLTlkYzliNjNjODczMi8wZjBmNWJhMC01YjI4LTRlYTQtYjI3Yy1iZGRjZTcwNDExMmIvJUU0JUJCJUE0JUU3JTg5JThDMi5wbmciLCJ0eXBlIjoiYXR0YWNobWVudCIsImlhdCI6MTc4MDQ1NDkwNiwiZXhwIjoxNzgwNDU4NTA2fQ.eUaWjQMV5r2mfmagH0fWlFJ9D-FjDpPJPwgKmMw6B4g " =1149x951")


\
 ![](https://wiki.tu-zi.com/api/files.get?sig=eyJhbGciOiJIUzI1NiIsInR5cCI6IkpXVCJ9.eyJrZXkiOiJ1cGxvYWRzL2I3MTgwNDFlLWUwNjItNDRlMy1iNTljLTlkYzliNjNjODczMi9iNjliMmU4ZS03YTI5LTQ5ODctOGUxYy1iZTgzMmFiNjEwNmMvMy5wbmciLCJ0eXBlIjoiYXR0YWNobWVudCIsImlhdCI6MTc4MDQ1NDkwNiwiZXhwIjoxNzgwNDU4NTA2fQ.oD1U2z3eOKJATufJSQwQLKehbcs_tloURLlB7ooYkFQ " =1177x826")


\
# 接口类型

* > 接口文档 地址: <https://tuzi-api.apifox.cn/408441203e0>

### 异步调用接口  |     /v1/videos

```javascript
curl --location --request POST 'https://api.tu-zi.com/v1/videos' \
--header 'Authorization: Bearer <token>' \
--form 'model="doubao-seedance-1-5-pro_1080p"' \
--form 'prompt="图像中形象赛跑起来然后相互碰面"' \
--form 'seconds="8"' \
--form 'size="1:1"'
```

**视频查询接口**  

```javascript
# https://api.tu-zi.com/v1/videos/{task_id}
# 例如
curl --location --request GET 'https://api.tu-zi.com/v1/videos/cgt-20260121104952-jjntv' \
--header 'Authorization: Bearer <token>'
```

### 同步调用接口  |     /v1/chat/completions

**Python调用演示**

```json
import http.client
import json

conn = http.client.HTTPSConnection("api.tu-zi.com")
payload = json.dumps({
   "temperature": 0.7,
   "messages": [
      {
         "content": "A candid 4K street interview scene set in a lively urban environment, captured with a slightly shaky handheld camera. A charismatic interviewer holds a microphone and stops a passerby on the sidewalk. The microphone has a small logo: 'CCTV'. The interviewer asks in English: 'Are you happy?' The person responds naturally—with surprise, curiosity, or excitement—and gives an improvised answer. The background shows the bustle of city life: people walking, light traffic, shop windows, and possibly some graffiti or murals. Natural daylight, with ambient city sounds. The entire interaction is in English, with English subtitles, and a watermark appears in the bottom-right corner.\"@tuziapi\".",
         "role": "user"
      }
   ],
   "model": "doubao-seedance-1-0-pro-250528",
   "stream": True
})
headers = {
   'Accept': 'application/json',
   'Authorization': 'Bearer sk-*******', // 这里填写兔子api key
   'Content-Type': 'application/json'
}
conn.request("POST", "/v1/chat/completions", payload, headers)
res = conn.getresponse()
data = res.read()
print(data.decode("utf-8"))
```

# 视频效果

[https://www.bilibili.com/video/BV1pibnznEJb?share%5Fsource=copy%5Fweb](https://www.bilibili.com/video/BV1pibnznEJb?share%5Fsource=copy%5Fweb)

## 效果演示-"mj-chat"

* 输入 ![](https://wiki.tu-zi.com/api/files.get?sig=eyJhbGciOiJIUzI1NiIsInR5cCI6IkpXVCJ9.eyJrZXkiOiJ1cGxvYWRzL2UxMjc0Y2E3LWNmZTEtNDdlOC04MjA0LTNhMDkzMTNlNzM4ZC8zNTM4MDc3NC01ODA5LTQzN2ItOTA4Yy02YTZmYzBlOGZhOTkvaW1hZ2UucG5nIiwidHlwZSI6ImF0dGFjaG1lbnQiLCJpYXQiOjE3ODA0NTQ5MDYsImV4cCI6MTc4MDQ1ODUwNn0.h-ndoph3lDsRWTQJta85arbqCq18V8ulK-E7mcH1vEw " =1920x904")
* 输出

```json
> VideoTask(id=cgt-20250616110726-lfk9x)
[🤫 任务进度](🚀🚀🚀🚀🚀🚀🚀🚀🚀🚀🚀🚀🚀🚀)🎉🎉🎉

{
    "id": "cgt-20250616110726-lfk9x",
    "model": "doubao-seedance-1-0-pro-250528",
    "status": "succeeded",
    "content": {
        "video_url": "https://ark-content-generation-cn-beijing.tos-cn-beijing.volces.com/doubao-seedance-1-0-pro/<video-id>.mp4?X-Tos-Credential=<YOUR_ACCESS_KEY>..."
    },
    "usage": {
        "completion_tokens": 245025,
        "total_tokens": 245025
    },
    "created_at": 1750043247,
    "updated_at": 1750043295
}


[下载链接1](https://ark-content-generation-cn-beijing.tos-cn-beijing.volces.com/doubao-seedance-1-0-pro/<video-id>.mp4?X-Tos-Credential=<YOUR_ACCESS_KEY>...)
```

[https://www.bilibili.com/video/BV193MizFEYm?share%5Fsource=copy%5Fweb](https://www.bilibili.com/video/BV193MizFEYm?share%5Fsource=copy%5Fweb)

# 参数说明

## 异步调用接口 

### `model`（模型名称）

* **类型**：`string`
* **可选值**：
  * `doubao-seedance-1-5-pro_1080p`
  * `doubao-seedance-1-5-pro_720p`
  * `doubao-seedance-1-5-pro_480p`
  * `doubao-seedance-1-0-pro_1080p`
  * `doubao-seedance-1-0-pro_720p`
  * `doubao-seedance-1-0-pro_480p`
  * `doubao-seedance-1-0-pro-fast_1080p`
  * `doubao-seedance-1-0-pro-fast_720p`
  * `doubao-seedance-1-0-pro-fast_480p`
  * `doubao-seedance-1-0-lite_1080p`
  * `doubao-seedance-1-0-lite_720p`
  * `doubao-seedance-1-0-lite_480p`


---

### `size`（宽高比）

* **类型**：`string`
* **说明**：不同模型默认值不同，常见默认值如下：
  * `wan2.1-14b-i2v`：默认 `keep_ratio`
  * `doubao-seedance-1-0-pro`、`doubao-seedance-1-0-lite-i2v`、`doubao-seaweed`：默认 `adaptive`
* **可选值**：
  * `21:9`
  * `16:9`
  * `4:3`
  * `1:1`
  * `3:4`
  * `9:16`
  * `9:21`
  * `keep_ratio`：生成视频的宽高比与所上传图片保持一致。
  * `adaptive`：根据上传图片的比例自动选择最合适的宽高比。


---

### `seconds`（视频时长）

* **类型**：`Integer`
* **可选值**：
* 范围 `4 >=`    `< 12`


---

### `input_reference`（参考图）

* **类型**：`string` 或者 `file`
* **文件**: url 可选择  string 类型, 本地图片文件可选择 file 类型
* **注意 :** 参考图 和 首尾帧 只能选择一个


---

### `first_frame_image`（首帧图）

* **类型**：`string` 或者 `file`


* **文件**: url 可选择  string 类型, 本地图片文件可选择 file 类型


---

### `last_frame_image`（尾帧图）

* **类型**：`Integer`


* **文件**: url 可选择  string 类型, 本地图片文件可选择 file 类型


## 同步调用接口 

在文本提示词后追加 `--[parameters]`，可控制视频输出的规格，包括宽高比、帧率、分辨率等。

```json
   "messages": [
      {
         "content": "提示词.  --resolution 720p --ratio 9:16 --duration 8 --watermark true"
          ,
         "role": "user"
      }
   ],
```

### `resolution`（分辨率）

* **类型**：`string`
* **默认值**：`720p`
* **简写**：`rs`
* **可选值**：
  * `480p`
  * `720p`
  * `1080p`


---

### `ratio`（宽高比）

* **类型**：`string`
* **简写**：`rt`
* **说明**：不同模型默认值不同，常见默认值如下：
  * `wan2.1-14b-i2v`：默认 `keep_ratio`
  * `doubao-seedance-1-0-pro`、`doubao-seedance-1-0-lite-i2v`、`doubao-seaweed`：默认 `adaptive`
* **可选值**：
  * `21:9`
  * `16:9`
  * `4:3`
  * `1:1`
  * `3:4`
  * `9:16`
  * `9:21`
  * `keep_ratio`：生成视频的宽高比与所上传图片保持一致。
  * `adaptive`：根据上传图片的比例自动选择最合适的宽高比。


---

### `duration`（视频时长）

* **类型**：`Integer`
* **默认值**：`5`（秒）
* **简写**：`dur`
* **可选值**：
  * `5`
  * `10`


---

### `framepersecond`（帧率）

* **类型**：`Integer`
* **简写**：`fps`
* **默认值**：
  * `wan2.1-14b`：默认 `16`
  * `doubao-seaweed`：默认 `24`
* **可选值**：
  * `16`
  * `24`


---

### `watermark`（水印）

* **类型**：`Boolean`
* **默认值**：`false`
* **简写**：`wm`
* **可选值**：
  * `false`：不含水印。
  * `true`：含有水印。


---

### `seed`（随机种子）

* **类型**：`Integer`
* **默认值**：`-1`
* **简写**：`seed`
* **取值范围**：`[-1, 2^32 - 1]`

#### 注意事项：

* 不指定 `seed` 或设置为 `-1` 时，会使用随机数。
* 改变 `seed` 是获取不同生成结果的一种方式。
* 相同请求使用相同 `seed` 值可能生成相似结果，但不保证完全一致。


---

### `camerafixed`（是否固定摄像头）

* **类型**：`Boolean`
* **默认值**：`false`
* **简写**：`cf`
* **可选值**：
  * `true`：平台会在用户提示词中追加固定摄像头（实际效果不保证）。
  * `false`：不固定摄像头。


---

## 响应参数

### `id`（视频任务 ID）

* 类型：`string`
* 说明：创建视频生成任务后返回的任务 ID。该接口为异步调用，需要通过**查询视频生成任务 API**获取任务状态。任务完成后会输出生成视频的 `video_url`。