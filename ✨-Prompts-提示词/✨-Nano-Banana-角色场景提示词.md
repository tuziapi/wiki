# ✨ Nano Banana 角色场景提示词

## Nano Banana主体参考与场景参考提示词

这篇文章面向第一次尝试通过"角色参考 A1/A2/A3 + 场景参考 B1/B2/B3"方法来稳定产出图像的同学。目标是：快速建立"可复用的角色与场景锚点"，并用最少变量的小步迭代，持续得到风格一致、故事连贯的结果。

提示：讲解使用中文；真正给模型的图像提示词建议使用英文（更稳定），并尽量量化细节（长度、百分比、角度、镜头参数等）。

### 基本原理：把可变与不可变拆开

* **A 类（角色参考）**：先锁定人物的"身份锚点"（脸型、发型、肤色、年龄、服装要素），确保角色在不同图像中保持一致。
  * A1 侧重"形体与三视图"（front/side/back）。
  * A2 侧重"面部与表情一致性"。
  * A3 侧重"服装与配色卡"。
* **B 类（场景参考）**：再锁定场景的"镜头与布局锚点"（机位、镜头、光线、构图、可插入空间）。
  * B1 是"建立镜头"（establishing shot），明确场景构成与尺度。
  * B2 是"干净底板"（clean plate），去人去物，保留插入空间。
  * B3 是"俯视布局"（top‑down blockout），用简图把物体位置、动线与比例固定。

把"人物是谁"（A 类）与"相机怎么拍"（B 类）解耦，可以在后续图像里复用同一套锚点，显著提高一致性与可控性。

### 工作流概览（极简版）


1. 准备世界观与角色信息（可整理为 `world.md`），明确风格锚点与价值观。
2. 先做 A1（必要时做 A2/A3），直到"脸/发/服装"稳定。
3. 再做 B1/B2/B3，固定机位、光线、构图、比例与可插入空间。
4. 在具体场景里合成：引用 A 锚点（人物）与 B 锚点（镜头/环境）。
5. 小步迭代：一次只改 1–2 个变量，用"除 X 外保持一切不变"。
6. 导出：角色用透明 PNG（便于合成），场景用高分 JPG/PNG，保持统一纵横比。

### 提示词骨架

**共性规则**

* 用英文书写图像提示词；短句、结构化表达；尽量量化（百分比、毫米、像素）。
* 强调语义正向描述（semantic positives），必要时补充语义负向（no people / uncluttered path / empty background）。
* 显式相机语言（镜头、机位、角度、构图）与光线（方向、强度、色温）。
* 统一纵横比（推荐 2:3 竖幅）；移动端优先的构图；避免叠加多风格。

**角色（Portrait/Sheet）**

* 关键词：身份锚点（年龄/脸型/肤色/发型/眼睛）、发/刘海保持一致、服装/配色锚点、光位固定、纯净背景。

**场景（Establishing/Clean plate/Top‑down）**

* 关键词：镜头焦距、机位高度、构图法则、关键地标、尺度参照、开阔插入区、干净背景与清晰的路径。

### A 类模板与示例

#### A1) Turnaround（三视图）必须！

```plaintext
Create a character turnaround sheet for "[UNIQUE_NAME]" (identity anchor).
Views: front, side, back; orthographic; consistent scale/alignment; full body.
Background: white seamless; neutral 5600K studio; thin gray ground shadow.
Keep facial features and hairstyle identical; no props/background elements.
Canvas: vertical 2:3 (e.g., 2048×3072).
```

 ![角色三视图](https://tuziai.oss-cn-shenzhen.aliyuncs.com/wiki/prompt/character_a1_turnaround_photorealistic.webp " =456x456")

#### A2) Face & expressions（3×3 表情）可选！

```plaintext
Create a 3×3 expression grid for "[UNIQUE_NAME]".
Close-up, neutral front camera; soft key + fill; white seamless; identical framing.
Row1: neutral, happy (closed-mouth), surprised.
Row2: thinking, determined, embarrassed.
Row3: sleepy, curious, laughing.
Keep hair/bangs identical; no accessory changes.
Output: single sheet or 1024×1024 tiles; transparent optional.
```

 ![角色表情参考](https://tuziai.oss-cn-shenzhen.aliyuncs.com/wiki/prompt/character_a2_expressions.webp " =494x494")

#### A3) Outfit & palette（服装与配色卡）可选！

```plaintext
Create an outfit and palette card for "[UNIQUE_NAME]":
one mid-shot (front), one fabric/zipper close-up,
one emblem/accessory close-up, plus a 5-swatch color strip with short labels.
Layout: white board with clean labels (transparent canvas optional).
If a ref photo is attached, use materials/colors from the photo; keep identity locked.
```

 ![服装与配色卡](https://tuziai.oss-cn-shenzhen.aliyuncs.com/wiki/prompt/character_a3_outfit_palette.webp " =418x418")

### B 类模板与示例

#### B1) Establishing shot（建立镜头）可选！

```plaintext
Generate an establishing shot of "[LOCATION_NAME]" at [time]: [key layout elements].
Camera: 35 mm, eye-level, rule-of-thirds; soft warm light, long shadows.
Optional: subtle A–B scale bar (1 m) or a faint 1 m ground grid overlay.
Aspect: 16:9 landscape.
```

#### B2) Clean plate（干净底板，无人物）必须！

```plaintext
Render a clean plate of the same scene with no people or animals;
keep identical camera and lighting to match B1.
Emphasize uncluttered paths and open insertion space.
Background-only; layer-friendly elements optional (separate transparent cut-outs).
```

 ![场景视图1](https://tuziai.oss-cn-shenzhen.aliyuncs.com/wiki/prompt/view1_from_layout.webp " =456x456")

 ![场景视图2](https://tuziai.oss-cn-shenzhen.aliyuncs.com/wiki/prompt/view2_from_layout.webp " =456x456")

这里还是不够完美，还是有穿帮的地方！

#### B3) Top‑down blockout（俯视布局图）可选！

```plaintext
Draw a top-down schematic: [pond/bridge/paths/props] with thin labels and a 1 m grid.
Monochrome on white or transparent background; anti-aliased edges; no textures.
```

 ![俯视布局图](https://tuziai.oss-cn-shenzhen.aliyuncs.com/wiki/prompt/scene_b3_layout.webp " =456x456")

### 使用tuzi-mcp的元提示词方法跑通

把上面的提示词存成文件prompt.md，这个文件中也可加上gemini官方生图的最佳实践提示词。然后在任意MCP客户端（Cherry Studio， Claude Code, Cursor, Windsurf）中添加tuzi-mcp后提示：


1. 根据 @原始参考.png，用gemini工具生成角色参考，（放在XXX目录下）。
2. 生成有两个房子的家庭场景参考。
3. 生成人物在沙发看书以及在看餐厅吃饭的图片。

实测步骤1很稳，步骤2需要看下效果，迭代优化。

大模型会根据prompt.md中的元提示词来扩写以上提示，从而保证较好的效果。

 ![角色在吧台](https://tuziai.oss-cn-shenzhen.aliyuncs.com/wiki/prompt/character_counter_back_view.webp " =456x456")

 ![角色在沙发阅读](https://tuziai.oss-cn-shenzhen.aliyuncs.com/wiki/prompt/character_sofa_reading_final.webp " =456x456")