# 🎨 ComfyUI + Flux-Kontext Pro

# ComfyUI中使用Flux-Kontext-Pro

本文介绍两个优秀的ComfyUI自定义节点方案，用于在ComfyUI中使用Flux-Kontext模型进行图像生成。


---

## 🚀 方案一：ComfyUI-TuZi-Flux-Kontext

🐰 **强大的 Flux-Kontext 图像生成** ComfyUI 自定义节点，使用兔子AI官方API，支持文生图、图生图和多图生图。Pro模型0.14元/次，Max模型0.28元/次。

**GitHub地址**: <https://github.com/LKbaba/ComfyUI-TuZi-Flux-Kontext>

### ✨ 核心特性

* 🎨 **三种生成模式** - 文生图、单图编辑、多图编辑，满足所有创作需求
* 🔥 **双模型支持** - Flux-Kontext-Pro 和 Flux-Kontext-Max，质量与速度自由选择
* ⚡ **并发批量生成** - 支持同时生成 1、2、4 张图像，智能并发提升效率
* 🛡️ **零技术门槛** - 只需一个API密钥，自动处理所有技术细节
* 🎯 **专业参数控制** - 完整支持种子、指导强度、推理步数、宽高比等参数
* 🌟 **优雅的用户界面** - 简洁的状态反馈，清晰的生成进度提示

### 🔥 项目优势

* **🔑 超简化配置** - 仅需配置兔子AI密钥，无需额外的第三方服务配置
* **📱 友好的反馈** - 中文界面，emoji状态提示，清晰的成功/失败统计
* **🚀 高性能** - 智能并发生成，多图同时处理，大幅提升生成速度
* **🛡️ 稳定可靠** - 完善的错误处理，自动重试机制，确保生成成功率

### 📦 安装方法

#### 方法一：通过 ComfyUI Manager 安装（推荐）


1. 在 ComfyUI 界面中打开 **ComfyUI Manager**
2. 点击 **"Install via Git URL"**
3. 输入：`https://github.com/LKbaba/ComfyUI-TuZi-Flux-Kontext.git`
4. 安装完成后重启 ComfyUI

#### 方法二：手动安装

**方式A：通过 Git 克隆（推荐）**

```bash
# 进入 ComfyUI 的 custom_nodes 目录
cd ComfyUI/custom_nodes/

# 克隆项目
git clone https://github.com/LKbaba/ComfyUI-TuZi-Flux-Kontext.git
cd ComfyUI-TuZi-Flux-Kontext

# 安装依赖
pip install -r requirements.txt
```

**方式B：下载 ZIP 文件**


1. 访问 [项目页面](https://github.com/LKbaba/ComfyUI-TuZi-Flux-Kontext)
2. 点击绿色 **"Code"** 按钮 → **"Download ZIP"**
3. 解压到 `ComfyUI/custom_nodes/` 目录
4. **重要**: 将解压后的文件夹从 `ComfyUI-TuZi-Flux-Kontext-main` 重命名为 `ComfyUI-TuZi-Flux-Kontext`

```bash
# 安装依赖
cd ComfyUI/custom_nodes/ComfyUI-TuZi-Flux-Kontext
pip install -r requirements.txt
```

#### 便携版用户特别说明

便携版用户需要使用ComfyUI自带的Python环境安装依赖：

**Git 克隆方式：**

```powershell
# 在 ComfyUI 根目录执行 例如：PS E:\ComfyUI_windows_portable_nvidia\ComfyUI_windows_portable>
.\python_embeded\python.exe -m pip install --force-reinstall -r .\ComfyUI\custom_nodes\ComfyUI-TuZi-Flux-Kontext\requirements.txt
```

**ZIP 下载方式：**

```powershell
# ⚠️ 注意：如果是下载ZIP解压，文件夹名称为 ComfyUI-TuZi-Flux-Kontext-main
# 请先重命名文件夹，或使用以下命令：
.\python_embeded\python.exe -m pip install --force-reinstall -r .\ComfyUI\custom_nodes\ComfyUI-TuZi-Flux-Kontext-main\requirements.txt

# 重命名后推荐使用：
.\python_embeded\python.exe -m pip install --force-reinstall -r .\ComfyUI\custom_nodes\ComfyUI-TuZi-Flux-Kontext\requirements.txt
```

### 🔑 API密钥设置

#### 获取 API 密钥

您只需要获取 **一个** API 密钥：

* **兔子AI密钥**: 访问 [兔子AI官网](https://api.tu-zi.com/panel) 登录后在控制台获取

#### 配置方法

插件已经包含了 `.env` 配置模板文件，您只需要：


1. **打开配置文件**: `ComfyUI/custom_nodes/ComfyUI-TuZi-Flux-Kontext/.env`
2. **替换 API 密钥**: 将 `sk-xxxxx` 替换为您的真实密钥

```env
TUZI_API_KEY=your_tuzi_api_key_here
```

**配置位置**: `ComfyUI/custom_nodes/ComfyUI-TuZi-Flux-Kontext/.env`

保存文件后重启 ComfyUI 即可使用！

### 🎯 使用方法

安装完成后，您将在 **"TuZi/Flux.1 Kontext"** 分类下找到三个强大的节点：

#### 1. 🐰Flux.1 Kontext - Text to Image

**纯文本生成图像**   ![text-to-image-demo.png](https://tuziai.oss-cn-shenzhen.aliyuncs.com/wiki/code/flux-kontext/text-to-image-demo.png)

* **输入**: 文本提示词
* **用途**: 基于文字描述创建全新图像
* **支持模型**: Flux-Kontext-Pro、Flux-Kontext-Max
* **输出**: 高质量图像

#### 2. 🐰Flux.1 Kontext - Editing

**单图像编辑生成**   ![single-image-editing-demo.png](https://tuziai.oss-cn-shenzhen.aliyuncs.com/wiki/code/flux-kontext/single-image-editing-demo.png)

* **输入**: 文本提示词 + 单张参考图像
* **用途**: 基于现有图像进行智能编辑和变换
* **支持模型**: Flux-Kontext-Pro、Flux-Kontext-Max
* **特色**: 深度理解图像上下文，精准编辑

#### 3. 🐰Flux.1 Kontext - Editing (Multi Image)

**多图像融合生成**   ![multi-image-editing-demo.png](https://tuziai.oss-cn-shenzhen.aliyuncs.com/wiki/code/flux-kontext/multi-image-editing-demo.png)

* **输入**: 文本提示词 + 多张参考图像（2-4张）
* **用途**: 融合多个图像元素，创造复杂场景
* **支持模型**: Flux-Kontext-Pro、Flux-Kontext-Max
* **特色**: 智能理解多图关系，创造性融合

### ⚙️ 参数说明

#### 核心参数

* **prompt** (文本提示词): 描述您想要生成的图像
* **model**: 选择生成模型
  * `flux-kontext-pro`: 一个统一的模型，提供本地编辑、生成性修改和 FLUX.1 质量的文本到图像生成。处理文本和图像输入，以实现精确的区域编辑或全场景转换，速度突破，开创了在多次编辑中保持角色一致性的迭代工作流程。
  * `flux-kontext-max`: 新高级模型在各个方面都带来了最大性能——显著改善的提示遵循和排版生成实现了高端的一致性，使编辑在速度上没有妥协。
* **num_images**: 生成数量 (1/2/4 张)
* **seed**: 随机种子 (0=随机，其他=固定)

#### 高级参数

* **guidance_scale**: 指导强度 (0.0-10.0) - 值越高，越严格遵循提示词
* **num_inference_steps**: 推理步数 (1-100) - 步数越多，细节越丰富
* **aspect_ratio**: 宽高比选择 - 支持 21:9、16:9、4:3、1:1、3:4、9:16、9:21
* **output_format**: 输出格式 (PNG/JPEG)
* **safety_tolerance**: 安全容忍度 (0-6)
* **prompt_upsampling**: 提示词增强 (开启/关闭)


---

## 🔧 方案二：TuZi API - Flux Kontext Nodes（基础版）

基于fal改进的ComfyUI插件，改自fal_api项目，新增了模型选择功能，可以直接选择切换max和pro模型。目前通过ImgBB负责图像上传和整合。

**GitHub地址**: <https://github.com/yellowstar686/comfyui-tuzi/tree/main>

### ⚠️ 重要说明

* **图像上传**: 目前使用 ImgBB 进行图像上传（临时方案）
* **免费限制**: 非会员账户每小时可免费上传 100 张图片
* **API 密钥**: 需要 TuZi API 密钥和 ImgBB API 密钥
* **未来更新**: 待 TuZi 支持 base64 图像上传后会更新项目

### ✨ 核心特性

* 🎨 **三种生成模式** - 单图像、多图像、纯文本生成
* 🔄 **基于fal_api改进** - 稳定的底层架构
* 📤 **ImgBB集成** - 临时图像上传解决方案
* 🎯 **内部平台友好** - API密钥存储在配置文件中

### 📦 安装方法

#### 方法一：通过 ComfyUI Manager 安装（推荐）


1. 在 ComfyUI 界面中打开 ComfyUI Manager
2. 点击 "Install via Git URL"
3. 输入：`https://github.com/yellowstar686/tuzi-api.git`
4. 安装完成后重启 ComfyUI

#### 方法二：手动安装

```bash
cd ComfyUI/custom_nodes

git clone https://github.com/yellowstar686/tuzi-api.git

cd tuzi-api

pip install -r requirements.txt
```

### 🔑 API 密钥设置

您需要获取两个 API 密钥：

* **TuZi API 密钥**: 从 [兔子API控制台](https://api.tu-zi.com/panel) 获取
* **ImgBB API 密钥**: 从 [ImgBB](https://imgbb.com/) 获取

### 📁 配置文件

在插件目录中打开 `config.ini` 文件，填入您的 API 密钥：

```ini
[API]
API_KEY = 您的兔子API密钥
IMGBB_API_KEY = 您的ImgBB_API密钥
```

### 🎯 使用方法

安装完成后，您将在 **"TuZi/Image"** 分类下找到三个节点：

#### 1. Flux Pro Kontext（单图像）

**基于上下文理解的图像到图像生成**

* **输入**: 文本提示词 + 单张图像
* **用途**: 基于上下文理解的图像到图像生成
* **参数**:
  * 提示词（文本）
  * 输入图像
  * 宽高比（16:9, 1:1 等）
  * 输出格式（PNG/JPEG）
  * 安全等级
  * 提示词增强

#### 2. Flux Pro Kontext Multi（多图像）

**使用多个参考图像生成复杂场景**

* **输入**: 文本提示词 + 多张图像（2-4张）
* **用途**: 使用多个参考图像生成复杂场景
* **参数**:
  * 提示词（文本）
  * 图像 1-4（至少需要2张）
  * 宽高比
  * 输出格式
  * 安全等级
  * 提示词增强

#### 3. Flux Pro Kontext Text-to-Image（文生图）

**纯文本生成图像**

* **输入**: 仅文本提示词
* **用途**: 纯文本生成图像
* **参数**:
  * 提示词（文本）
  * 宽高比
  * 输出格式
  * 安全等级
  * 提示词增强

### 🔧 配置说明

* **内部使用**: API 密钥存储在 `config.ini` 中，方便作为内部平台使用
* **手动配置**: 需要手动在配置文件中填写 API 密钥
* **临时方案**: ImgBB 集成是临时方案，待 TuZi 支持 base64 图像上传后会更新

### 📋 工作流示例

工作流地址：[兔子API.json](https://github.com/yellowstar686/comfyui-tuzi/blob/main/example_workflows/%E5%85%94%E5%AD%90API.json)

 ![comfyui01.jpg](https://wiki.tu-zi.com/api/files.get?sig=eyJhbGciOiJIUzI1NiIsInR5cCI6IkpXVCJ9.eyJrZXkiOiJ1cGxvYWRzLzhkMTlmMmJkLTA5MGQtNGRlZi1iOTg1LWYxOTVhM2NhYTVkYy8xMWNiNTQ4Zi1kODI1LTQ2OTktYjllYy1iZjkxOGE3YWFlMTcvY29tZnl1aTAxLmpwZyIsInR5cGUiOiJhdHRhY2htZW50IiwiaWF0IjoxNzgwNDU0OTEwLCJleHAiOjE3ODA0NTg1MTB9.ZL8H7FPiNBaHwnbQA_fOrFW1UqarCZLPBpNcZDfmrcE)

### 🔮 未来更新

* 待 TuZi API 支持 base64 图像上传后会更新项目
* 未来版本将移除 ImgBB 依赖
* 增强错误处理和用户体验改进


---

## 📊 方案对比

| 特性  | ComfyUI-TuZi-Flux-Kontext | TuZi API - Flux Kontext Nodes |
|-----|---------------------------|-------------------------------|
| **配置复杂度** | ⭐⭐⭐⭐⭐ 仅需1个API密钥           | ⭐⭐⭐ 需要2个API密钥                 |
| **功能完整性** | ⭐⭐⭐⭐⭐ 三种生成模式              | ⭐⭐⭐⭐ 三种生成模式                   |
| **用户界面** | ⭐⭐⭐⭐⭐ 中文界面，友好反馈           | ⭐⭐⭐ 标准界面                      |
| **性能优化** | ⭐⭐⭐⭐⭐ 智能并发生成              | ⭐⭐⭐ 标准性能                      |
| **稳定性** | ⭐⭐⭐⭐⭐ 完善错误处理              | ⭐⭐⭐ 基础稳定                      |
| **维护状态** | ⭐⭐⭐⭐⭐ 积极维护                | ⭐⭐⭐ 基础维护                      |
| **图像上传** | ⭐⭐⭐⭐⭐ 内置处理                | ⭐⭐ 依赖ImgBB（临时）                |
| **内部平台** | ⭐⭐⭐ 标准配置                  | ⭐⭐⭐⭐⭐ 配置文件友好                  |

## 💡 推荐建议

* **新用户推荐**: 选择 **ComfyUI-TuZi-Flux-Kontext**，配置简单，功能完整
* **内部平台用户**: 可考虑 **TuZi API - Flux Kontext Nodes**，配置文件管理更方便
* **高级用户**: 可以根据具体需求选择合适的方案
* **企业用户**: 推荐 **ComfyUI-TuZi-Flux-Kontext**，稳定性和支持更好


---

## 🐛 故障排除

### 节点相关问题

**节点没有出现？**

* 完全重启 ComfyUI
* 检查插件安装路径
* 确认依赖安装成功
* 验证配置文件是否存在且包含正确的 API 密钥

**节点显示红色错误？**

* 检查配置文件是否存在
* 验证 API 密钥格式
* 重启 ComfyUI
* 查看 ComfyUI 控制台的详细错误信息

### API 相关问题

**生成失败？**

* 检查兔子AI账户余额
* 验证 API 密钥有效性
* 查看节点状态信息获取详细错误
* 检查 API 配额限制

**图像上传失败？（方案二）**

* 确保输入图像格式有效（PNG, JPEG）
* 检查 ImgBB 上传限制（免费账户每小时 100 张）
* 验证网络连接
* 验证 ImgBB API 密钥是否正确


---

## 📋 系统要求

* **Python** >= 3.8
* **ComfyUI** (最新版本)
* **依赖包**:
  * requests
  * python-dotenv
  * fal-client
  * httpx
  * httpcore
  * torch
  * Pillow
  * numpy


---

## 🔗 相关链接

* **兔子AI官网**: [tu-zi.com](https://api.tu-zi.com)
* **ComfyUI**: [github.com/comfyanonymous/ComfyUI](https://github.com/comfyanonymous/ComfyUI)
* **Flux模型**: [Black Forest Labs](https://blackforestlabs.ai/)
* **API文档**: [wiki.tu-zi.com](https://wiki.tu-zi.com/zh/Code/Flux-Kontext)
* **ImgBB**: [imgbb.com](https://imgbb.com/)


---

**⭐ 如果这些项目对您有帮助，请给开发者们一个星标！您的支持是持续改进的动力！**