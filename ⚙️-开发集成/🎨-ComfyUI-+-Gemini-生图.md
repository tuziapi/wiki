# 🎨 ComfyUI + Gemini 生图

# 在comfyui中调用tuzi的gemini-2.5-flash-image

### 背景

基本上我是为了使用tuzi的gemini-2.5-flash-image写了一套comfyui的节点，因为一般生图不会只用一个节点，还会涉及到其他的llm服务，如果各种节点混搭太费劲了，也不能发挥tuzi这里集成模型的优势，所以就vibe了一个，迭代了几个版本，用了一个周末，分享出来给大家。

基础目前是全部基于openai的协议，特调了对gemini-2.5-flash-image的兼容。

插件地址： https://github.com/Semonxue/Comfyui-flexai

### 安装


1. 克隆到 ComfyUI 自定义节点目录：

   ```bash
   cd ComfyUI/custom_nodes
   git clone https://github.com/your-repo/Comfyui-flexai.git
   ```
2. 安装依赖：

   ```bash
   cd Comfyui-flexai
   pip install -r requirements.txt
   ```
3. 配置提供商（见配置章节）
4. 重启 ComfyUI

## 配置

在插件根目录创建 `.env` 文件,或复制 `.env.example` 文件并重命名。

### 单一提供商

```bash
OPENAI_API_KEY=your_openai_api_key_here
OPENAI_API_BASE=https://api.openai.com/v1  # 可选
```

### 多提供商（推荐）

```bash
# 定义提供商列表
OPENAI_PROVIDERS=openai,tuzi,custome

# OpenAI
OPENAI_API_KEY_openai=sk-your-openai-key
OPENAI_API_BASE_openai=https://api.openai.com/v1

# Tuzi（通过 OpenAI 兼容端点）
OPENAI_API_KEY_tuzi=sk-your-tuzi-key  
OPENAI_API_BASE_tuzi=https://api.tu-zi.com/v1

# 自定义端点
OPENAI_API_KEY_custom=your-custom-key
OPENAI_API_BASE_custom=https://your-api.example.com/v1
```

### 使用

重启comfyui后，搜索节点 flexai 可以看到有2个节点，拖到画布里，选择对应的api分组、填写目标模型和提示词，生成即可，如下：

 ![flexai-comfyui-image.jpg](https://tuziai.oss-cn-shenzhen.aliyuncs.com/wiki/code/flexai-comfyui-image.jpg)

 ![flexai-comfyui-text.jpg](https://tuziai.oss-cn-shenzhen.aliyuncs.com/wiki/code/flexai-comfyui-text.jpg)

打开debug可以在console里看到与接口的交互过程。

### 工作流实例

#### 换装+手办化 [flexai-手办换装.json](/code/flexai-%E6%89%8B%E5%8A%9E%E6%8D%A2%E8%A3%85.json)

 ![flexai-手办换装.jpg](https://tuziai.oss-cn-shenzhen.aliyuncs.com/wiki/code/flexai-%E6%89%8B%E5%8A%9E%E6%8D%A2%E8%A3%85.jpg)

#### 产品放置 [flexai-产品放置.json](/code/flexai-%E4%BA%A7%E5%93%81%E6%94%BE%E7%BD%AE.json)

 ![flexai-产品放置.jpg](https://tuziai.oss-cn-shenzhen.aliyuncs.com/wiki/code/flexai-%E4%BA%A7%E5%93%81%E6%94%BE%E7%BD%AE.jpg) 成本感人：   ![](https://wiki.tu-zi.com/api/files.get?sig=eyJhbGciOiJIUzI1NiIsInR5cCI6IkpXVCJ9.eyJrZXkiOiJ1cGxvYWRzL2UxMjc0Y2E3LWNmZTEtNDdlOC04MjA0LTNhMDkzMTNlNzM4ZC84MThhM2E5Zi02NmIzLTQzODYtYjQxZi0wMWQyY2U3ODUyOGYvaW1hZ2UucG5nIiwidHlwZSI6ImF0dGFjaG1lbnQiLCJpYXQiOjE3ODA0NTQ5MDIsImV4cCI6MTc4MDQ1ODUwMn0.S_Zr5pbxaFXVPzac4iYonSrKaU4cGdZLGKL5AOV-XcM " =2286x258")