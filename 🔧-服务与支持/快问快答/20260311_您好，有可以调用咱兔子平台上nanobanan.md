# 20260311_您好，有可以调用咱兔子平台上nanobanan

## 问题

您好，有可以调用咱兔子平台上nanobanana模型的ComfyUI插件吗

## 回答

有现成方案，但 Wiki 里暂时没看到"nanobanana 专用插件"的单独条目。现在已发布的方案主要有两类：


1. 通用接入：可以用 `comfyui_LLM_party`，在 ComfyUI 里把 `base_url` 填成 `https://api.tu-zi.com/v1/`，再填你的 `api_key` 和平台支持的 `model_name`，如果你的账号下 `nanobanana` 可用，就可以直接试。
2. 专用节点参考：Wiki 里还有一篇针对 `gemini-2.5-flash-image` 的 ComfyUI 节点方案 `Comfyui-flexai`，说明兔子这边已经有实际的 ComfyUI 生图插件接入案例。

如果你要的是"开箱即用、专门为 nanobanana 做好的节点"，目前我在 Wiki 里没检索到明确发布文档；如果你接受通用方式，先用 LLM Party 这套最稳。

可先看这两篇：

* https://wiki.tu-zi.com/s/8c61a536-7a59-4410-a5e2-8dab3d041958/doc/comfyui-llm-party-kwT7uegYK2
* https://wiki.tu-zi.com/s/8c61a536-7a59-4410-a5e2-8dab3d041958/doc/comfyui-gemini-U9DCXs78PQ

**来源：** [🔧 ComfyUI 使用指南（LLM Party插件）](https://wiki.tu-zi.com/s/8c61a536-7a59-4410-a5e2-8dab3d041958/doc/comfyui-llm-party-kwT7uegYK2)

> 完整内容请查阅上方 Wiki 原文。