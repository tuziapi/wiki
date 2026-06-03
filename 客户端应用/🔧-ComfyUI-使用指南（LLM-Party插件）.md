# 🔧 ComfyUI 使用指南（LLM Party插件）

> 适用插件：`comfyui_LLM_party`\n目标：在 ComfyUI 里通过 LLM Party 插件调用 `https://api.tu-zi.com` 的模型


---

## 1. 准备工作

你需要先准备好：


1. 有效的 API Key
2. 已安装并可运行的 **ComfyUI**


---

## 2. 安装 LLM Party 插件

> 插件项目地址：<https://github.com/heshengtao/comfyui_LLM_party>

### 方式 A：通过 ComfyUI-Manager 安装（推荐）

> **ComfyUI-Manager** 是 ComfyUI 的插件管理器，相当于是 ComfyUI 的"应用商店/插件中心"。
>
> 如果你的 ComfyUI 里已经装了 Manager，安装 `comfyui_LLM_party` 会非常便捷。


1. 打开 ComfyUI 页面
2. 进入 ComfyUI-Manager
3. 搜索：`comfyui_LLM_party`
4. 点击安装
5. 重启 ComfyUI

### 方式 B：手动安装


1. 进入 `ComfyUI/custom_nodes/` 目录下
2. 执行：

```bash
git clone https://github.com/heshengtao/comfyui_LLM_party.git
```


3. 进入插件目录并安装依赖：

```bash
cd comfyui_LLM_party
pip install -r requirements.txt
```


4. 重启 ComfyUI


⚠️ 显示


---

## 4. `pip` 没安装怎么办？

很多用户会卡在这一步，按你的系统处理即可。

### Windows（常见）

#### 情况 A：你是 ComfyUI 便携版用户（推荐这样做）

直接使用 ComfyUI 自带 Python 安装依赖：

```bat
..\python_embeded\python.exe -m pip install -r requirements.txt
```

> 说明：在 `comfyui_LLM_party` 目录下执行这条命令。

#### 情况 B：系统提示 `pip` 不是内部或外部命令


1. 先检查 Python 是否安装：

```bat
python --version
```


2. 用 Python 模块方式调用 pip（比直接 `pip` 更稳）：

```bat
python -m pip install -r requirements.txt
```


3. 如果还不行，先安装/修复 pip：

```bat
python -m ensurepip --upgrade
python -m pip install --upgrade pip
```

### macOS / Linux

如果提示 `pip: command not found`，优先使用：

```bash
python3 -m pip install -r requirements.txt
```

若系统未安装 Python3，请先安装 Python 3.10+ 再执行上面命令。


---

## 5. 按官方 README「配置」部分进行快速配置

### 方案一（推荐给普通用户）：在节点里直接填参数


1. 打开 ComfyUI，新建一个 LLM Party 工作流（或导入示例）
2. 添加/找到 **LLM API 加载器（API LLM）** 节点
3. 在节点中填写：

* `base_url`：`https://api.tu-zi.com/v1/`
* `api_key`：你的 API Key
* `model_name`：要调用的模型名（按平台显示名称填写）


4. 保存并运行

### 方案二（进阶）：写到 `config.ini`


1. 打开 `comfyui_LLM_party/config.ini`
2. 填写全局配置（例如 `openai_api_key`、`base_url`、`model_name`）
3. 保存后重启 ComfyUI

> 推荐实践：先用"节点内配置"跑通，再考虑 `config.ini` 统一管理。

### 配置注意事项

* `base_url` 建议以 `/v1/` 结尾：`https://api.tu-zi.com/v1/`
* `api_key` 需从兔子平台获取，复制时避免前后空格
* `model_name` 必须与平台可用模型一致，否则可能报 `model not found`


---

## 6. 快速验证是否配置成功


1. 输入测试提示词（例如：`请用三句话介绍你自己`）
2. 点击运行
3. 若正常返回文本，即接入成功


---

## 7. 常见问题排查

### Q1：401 / 鉴权失败

* 检查 API Key 是否正确、是否过期
* 检查账号是否有该模型权限

### Q2：404 / model not found

* 检查 `model_name` 是否拼写正确
* 确认该模型在你的账号中可用

### Q3：连接超时

* 检查 `base_url` 是否正确：`https://api.tu-zi.com/v1/`
* 检查本地网络、代理、防火墙

### Q4：节点缺失 / 依赖报错

* 用 ComfyUI-Manager 补齐缺失节点
* 重新安装依赖并重启 ComfyUI


---

## 8. 官方视频教程入口

* B 站：<https://space.bilibili.com/26978344>
* YouTube：<https://www.youtube.com/@LLM-party>

（对应 README_ZH 的"视频教程"部分）


---

## 9. 给最终用户的最短配置说明（可直接复制）

在 LLM API 节点填三项：

* `base_url`: `https://api.tu-zi.com/v1/`
* `api_key`: 在兔子平台获取
* `model_name`: 平台支持的模型名

然后运行工作流即可。