# 🎵 Suno API 音乐生成

本 Wiki 提供与 Suno API 交互的文档和代码示例，该 API 允许生成歌词、音乐以及获取任务状态。

## API 端点

### 1. 生成歌词

* **方法:** POST
* **端点:** `https://api.tu-zi.com/suno/submit/lyrics`

**请求参数:**

* **Authorization:** 在 Header 中添加参数 `Authorization`，其值为在 `Bearer `之后拼接 Token。
* **示例:** `Authorization: Bearer ********************`

**代码示例 (**`**sunolyrics.py**`**):**

```python
import http.client
import json

conn = http.client.HTTPSConnection("api.tu-zi.com")
payload = json.dumps({
   "prompt": "歌颂可爱的兔子API服务商"
})
headers = {
   'Content-Type': 'application/json',
   'Authorization': 'sk-**'
}
conn.request("POST", "/suno/submit/lyrics", payload, headers)
res = conn.getresponse()
data = res.read()
print(data.decode("utf-8"))
```

### 2. 生成歌曲 (灵感、自定义、续写)

* **方法:** POST
* **端点:** `https://api.tu-zi.com/suno/submit/music`

**请求参数:**

* **Authorization:** 在 Header 中添加参数 `Authorization`，其值为在 `Bearer `之后拼接 Token。
* **示例:** `Authorization: Bearer ********************`
* **Body 参数 (**`**application/json**`**):**
  * `prompt` (string, 必需): `prompt`为空可填写`gpt_description_prompt`自动生成。
  * `tags` (string, 必需)
  * `mv` (string, 必需)
  * `title` (string, 必需)

  **示例:**

  ```json
  {
    "prompt": "[Verse]\nWalking down the streets\nBeneath the city lights\nNeon signs flickering\nLighting up the night\nHeart beating faster\nLike a drum in my chest\nI'm alive in this moment\nFeeling so blessed\n\nStilettos on the pavement\nStepping with grace\nSurrounded by the people\nMoving at their own pace\nThe rhythm of the city\nIt pulses in my veins\nLost in the energy\nAs my worries drain\n\n[Verse 2]\nConcrete jungle shining\nWith its dazzling glow\nEvery corner hiding secrets that only locals know\nA symphony of chaos\nBut it's music to my ears\nThe hustle and the bustle\nWiping away my fears",
    "tags": "emotional punk",
    "mv": "chirp-v4",
    "title": "City Lights"
  }
  ```

**代码示例 (**`**suno.py**`**):**

```python
import http.client
import json

conn = http.client.HTTPSConnection("api.tu-zi.com")
payload = json.dumps({
   "prompt": "[Verse]\nWalking down the streets\nBeneath the city lights\nNeon signs flickering\nLighting up the night\nHeart beating faster\nLike a drum in my chest\nI'm alive in this moment\nFeeling so blessed\n\nStilettos on the pavement\nStepping with grace\nSurrounded by the people\nMoving at their own pace\nThe rhythm of the city\nIt pulses in my veins\nLost in the energy\nAs my worries drain\n\n[Verse 2]\nConcrete jungle shining\nWith its dazzling glow\nEvery corner hiding secrets that only locals know\nA symphony of chaos\nBut it's music to my ears\nThe hustle and the bustle\nWiping away my fears",
   "tags": "emotional punk",
   "mv": "chirp-v4",
   "title": "City Lights"
})
headers = {
   'Content-Type': 'application/json',
   'Authorization': 'sk-**'  # Replace YOUR_API_TOKEN with your actual token
}
conn.request("POST", "/suno/submit/music", payload, headers)
res = conn.getresponse()
data = res.read()
print("Submission response:")
print(data.decode("utf-8"))
conn.close()
```

### 3. 获取任务

* **方法:** GET
* **端点:** `https://api.tu-zi.com/suno/fetch/{task_id}`

**请求参数:**

* **Authorization:** 在 Header 中添加参数 `Authorization`，其值为在 `Bearer `之后拼接 Token。
* **示例:** `Authorization: Bearer ********************`
* **Path 参数:**
  * `task_id` (string, 必需)

**代码示例 (**`**sunoget.py**`**):**

```python
import http.client
import json

# Replace 'YOUR_TASK_ID' with the actual task ID you received from suno.py
TASK_ID = "eb7feca7-3bec-4503-9bcd-a61d1ea553b1" 

if TASK_ID == "YOUR_TASK_ID" or not TASK_ID:
    print("Please replace 'YOUR_TASK_ID' in the script with the actual task ID.")
    exit()

conn = http.client.HTTPSConnection("api.tu-zi.com")
payload = '' # No payload for GET typically
headers = {
    # Add Authorization header if the GET endpoint requires it
    # Make sure this token is the same or valid for the fetch operation
   'Authorization': 'sk-**',
   'Content-Type': 'application/json' # Often not needed for GET but doesn't hurt
}

conn.request("GET", f"/suno/fetch/{TASK_ID}", payload, headers)
res = conn.getresponse()
data = res.read()

print(f"Fetching results for Task ID: {TASK_ID}")
print(data.decode("utf-8"))

conn.close()
```