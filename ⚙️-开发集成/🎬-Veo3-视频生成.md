# 🎬 Veo3 视频生成

## 1. Veo3 系列模型简介

> `Veo3` 是 Google DeepMind 在 2025 年的「Google I/O 大会」上推出的最新一代**生成式视频模型**，具备领先的多模态理解和影视生成能力。

主要特性包括：

| 特性  | 描述  |
|-----|-----|
| 🎬 **原生视听生成** | 可一次性生成 720p/24fps、最长 8 秒的视频，并同步生成高质量音效和对白。 |
| 🎥 **镜头控制与场景理解** | 支持提示词中直接指定镜头运动（如推拉摇移）、焦距，以及光照风格等，可理解复杂故事逻辑与角色行为。 |
| 🛡️ **安全机制** | 默认启用 `SynthID` 数字水印，限制生成内容时长、画幅比例与语言（仅英语提示有效），防止滥用。 |

#### 首帧输入

以下模型支持**首帧输入**，即**图生视频**。

* `veo3-frames`
* `veo3-fast-frames`
* `veo3-pro-frames`

| 特性  | 描述  |
|-----|-----|
| 🧑‍🤝‍🧑 **参考图一致性** | 可上传参考图或帧，确保人物、物品、光影在不同片段中一致，可进行视频内编辑（如添加道具）。 |


---

## 2. 使用 openai-chat 格式调用示例

> 返回内容会优先返回两个链接地址（`Data Preview`、`Source Data`），用来保障传输意外中断时依然可以获取生成结果。

### python调用文本生图脚本示例

```python
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
   "model": "veo3",
   "stream": True
})
headers = {
   'Accept': 'application/json',
   'Authorization': 'Bearer sk-yourkey',
   'Content-Type': 'application/json'
}
conn.request("POST", "/v1/chat/completions", payload, headers)
res = conn.getresponse()
data = res.read()
print(data.decode("utf-8"))
```

### 根据图片生成示例

```python
payload = json.dumps({
   "temperature": 0.7,
   "messages": [
      {
         "content": [
             {
                 "type": "text",
                 "text": "Generate a detailed scene of the character in the wind and rain based on the picture"
             },
             {
                 "type": "image_url",
                 "image_url": {
                     "url": "https://filesystem.site/cdn/20250814/qI5cU2VBPvtnL1tj12d5wcp8tC6sbZ.png"
                 }
             }
         ]
      }
   ],
   "model": "veo3",
   "stream": True
})
```

### 状态值列表和错误信息字段

```typescript
export enum TaskStatus {
  // 初始状态
  PENDING = 'pending',

  // AI 提示词优化阶段
  PROMPT_ENHANCEMENT_CHECKING = 'prompt_enhancement_checking', // 判断是否需要优化提示词
  PROMPT_ENHANCING = 'prompt_enhancing', // 优化提示词中

  // 图片处理阶段（如果有图片）
  IMAGE_DOWNLOADING = 'image_downloading',
  IMAGE_CROPPING = 'image_cropping',
  IMAGE_UPLOADING = 'image_uploading',
  IMAGE_PROCESSING_COMPLETED = 'image_processing_completed',

  // 视频生成阶段
  VIDEO_GENERATING = 'video_generating',
  VIDEO_GENERATION_COMPLETED = 'video_generation_completed',
  VIDEO_GENERATION_FAILED = 'video_generation_failed',

  // 视频增强阶段（可选）
  VIDEO_UPSAMPLING = 'video_upsampling',
  VIDEO_UPSAMPLING_COMPLETED = 'video_upsampling_completed',
  VIDEO_UPSAMPLING_FAILED = 'video_upsampling_failed',

  // 最终状态
  COMPLETED = 'completed',
  FAILED = 'failed',
}
```

```typescript
export interface Task {
  id: string;
  req: CreateVideoTaskRequest;
  enhanced_prompt?: string; // 当 req.enable_prompt_enhance 为 true 时，增强后的 prompt
  needs_safe_enhancement?: boolean; // 需要规避敏感内容的提示词优化
  status: TaskStatus;
  status_update_time: number; // unix timestamp
  running: boolean; // 任务是否已经正在运行，从任务池中拉取下来并执行，置为 true 防止重复执行

  // 图片处理相关
  images?: Array<{
    url: string;
    mediaId?: string;
    status:
      | 'pending'
      | 'downloading'
      | 'cropping'
      | 'uploading'
      | 'completed'
      | 'failed';
    error?: string;
  }>;
  startImageMediaId?: string;
  endImageMediaId?: string;
  referenceImageMediaIds?: string[];
  veo3StartImageMediaId?: string;

  // 视频生成相关
  video_generation_id?: string;
  video_generation_status?: string;
  video_generation_error?: string;
  video_url?: string;
  video_media_id?: string;

  // 视频增强相关
  upsample_generation_id?: string;
  upsample_status?: string;
  upsample_error?: string;
  upsample_video_url?: string;

  // 其他
  created_at: number; // unix timestamp
  completed_at?: number; // unix timestamp
  error_message?: string;
  error_sleep?: number;
  retry_count: number;
  max_retries: number;
}
```

## 3. 使用 chat-mj 格式调用示例

具体操作可以参考《[如何使用兔子 api 站点 速通](https://wiki.tu-zi.com/zh/Chat/howtouse-4o-all)》一文

### 3.1 文生视频 `veo3`, `veo3-fast`, `veo3-pro`

 ![veo3-1.png](https://tuziai.oss-cn-shenzhen.aliyuncs.com/wiki/code/veo3/veo3-1.png)

```json
{
  "prompt": "In a cozy cabin restaurant softly lit by flickering candlelight, warm shadows dance gently around the room. The camera moves smoothly with a handheld selfie perspective, capturing an elegant Korean woman with natural long hair. She wears a black lace-trimmed camisole dress and sits gracefully on a chair, exuding a relaxed and alluring expression. She smiles warmly and leans closer to the camera, softly whispering in Chinese in an ASMR style: '来由兔子API提供veo3模型生成，你要不要试试？来呗，来嘛'. The overall atmosphere is romantic, intimate, and tender."
}
```

```markdown
> 视频生成任务已创建
> 任务ID: `24cbd66b-3163-4f1a-95cf-0b9af4bf606f`
> 为了防止任务中断，可以从以下链接持续获取任务进度:
> [数据预览](https://asyncdata.net/web/24cbd66b-3163-4f1a-95cf-0b9af4bf606f) | [原始数据](https://asyncdata.net/source/24cbd66b-3163-4f1a-95cf-0b9af4bf606f)
> 等待处理中
> 类型: 文本视频生成
> 🎬 开始生成视频................
> 🔄 正在优化视频质量.............
> 🎉 高质量视频已生成

[▶️ 在线观看](https://filesystem.site/cdn/20250617/c5NLjuBPZD3oqzj6xJIx2bYJmDPVja.mp4) | [⏬ 下载视频](https://filesystem.site/cdn/download/20250617/c5NLjuBPZD3oqzj6xJIx2bYJmDPVja.mp4)
```

### 3.2 图生视频 `veo3-frames`, `veo3-fast-frames`, `veo3-pro-frames`

 ![veo3-6.png](https://tuziai.oss-cn-shenzhen.aliyuncs.com/wiki/veo3-6.png)

```json
{
  "prompt": "A short, lighthearted video featuring a girl initially taking self portraits with a camera, appearing a bit self-conscious. As the video progresses, she becomes more comfortable and starts striking various playful and cute poses. The audio includes the authentic sound of camera shutters clicking, intermingled with the girl's genuine giggles and ambient background noise that captures the joyful atmosphere. The visual style is vibrant and focuses on the girl's expressions and movements, with a soft filter to enhance the playful mood."
}
```

```markdown
> Video generation task created
> Task ID: `a40f3847-3a37-47d1-b08f-0c897fa6f9b3`
> To prevent task interruption, you can continuously track progress from the following links:
> [Data Preview](https://asyncdata.net/web/a40f3847-3a37-47d1-b08f-0c897fa6f9b3) | [Source Data](https://asyncdata.net/source/a40f3847-3a37-47d1-b08f-0c897fa6f9b3)
> Waiting for processing

> 🖼️ Processing images (download/crop/upload).

> Type: VEO3 start frame video generation
> 🎬 Starting video generation..................................

> Type: VEO3 start frame video generation
> 🎬 Starting video generation...................

> Type: VEO3 start frame video generation
> 🎬 Starting video generation.......................................

> ✅ Preview video generated
> [📺 Online Preview](https://filesystem.site/cdn/20250617/qXTj2bhDckeIaMRTO9fd9O1wDBcpqk.mp4) | [⏬ Download Video](https://filesystem.site/cdn/download/20250617/qXTj2bhDckeIaMRTO9fd9O1wDBcpqk.mp4)

> 🔄 Optimizing video quality...............

> 🎉 High-quality video generated

[▶️ Watch Online](https://filesystem.site/cdn/20250617/xaZfjBaFNnB7lefCTrzb5CxljlV51K.mp4) | [⏬ Download Video](https://filesystem.site/cdn/download/20250617/xaZfjBaFNnB7lefCTrzb5CxljlV51K.mp4)
```