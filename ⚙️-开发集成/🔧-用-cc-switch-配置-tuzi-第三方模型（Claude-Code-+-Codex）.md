# 🔧 用 cc-switch 配置 tuzi 第三方模型（Claude Code + Codex）

> 尚未安装 CC Switch？先看 [CC Switch 下载与安装](🔧-CC-Switch-下载与安装.md)。

## 前言：cc-switch 是什么？能做什么？

如果你是第一次接触模型配置，可以把 **cc-switch** 理解成一个"模型切换面板" 🧭：

* 它可以帮你管理多个模型供应商（比如 Claude、Codex、Gemini 等）
* 你不用每次手动改一堆配置文件
* 可以在不同供应商之间快速切换

这篇教程会手把手教你，如何把 **tuzi 提供的接口**接入到：


1. **Claude Code**
2. **Codex**


---

## 准备工作（先做这 3 件事）🧰

### 1) 确认你有可用 API（先去 tuzi 官网获取）🔑

先登录 tuzi 官网，确认你已经拿到可用 Key：

* **Claude 分组 Key**
* **Codex 分组 Key**

  ![](https://wiki.tu-zi.com/api/files.get?sig=eyJhbGciOiJIUzI1NiIsInR5cCI6IkpXVCJ9.eyJrZXkiOiJ1cGxvYWRzL2FjNjBlNmRhLTdjYTQtNDdjMS04ZTQxLTAxMDUyMDAwNzM3NS80OGQzMTJiOC0yOTc0LTQ2OGMtYWUwOS0xNWU5Y2M3NzUxMjUvaW1hZ2UucG5nIiwidHlwZSI6ImF0dGFjaG1lbnQiLCJpYXQiOjE3ODA0NTQ4OTcsImV4cCI6MTc4MDQ1ODQ5N30.nq1DFXpSRv15_xAeP_gUPAX7uZedsb96FQBee8w464U " =642x341")


---

### 2) 安装 cc-switch（新手安装步骤）💻

> cc-switch 官方仓库：`https://github.com/farion1231/cc-switch`

如果你还没安装，请按下面做：


**Windows 用户**

从 [Releases](https://github.com/farion1231/cc-switch/releases) 页面下载最新版本的：

* `CC-Switch-v{版本号}-Windows.msi`（安装版）
* 或 `CC-Switch-v{版本号}-Windows-Portable.zip`（绿色版）

  \

**macOS 用户**

**方式一：Homebrew 安装（推荐）**

```bash
brew tap farion1231/ccswitch
brew install --cask cc-switch
```

更新：

```bash
brew upgrade --cask cc-switch
```

**方式二：手动下载**

从 [Releases](https://github.com/farion1231/cc-switch/releases) 下载 `CC-Switch-v{版本号}-macOS.zip`，解压后使用。

> ⚠️ 注意：首次打开若出现"未知开发者"提示，先关闭，再到"系统设置 → 隐私与安全性"点击"仍要打开"。


---

### 3) 打开 cc-switch，先清空旧冲突（如果你以前配过）🧹

如果你之前按照其他方法已经配置过 Claude Code 或是 Codex ，在系统里写过旧环境变量（比如 `.zshrc`），第一次打开 cc-switch 时会显示环境变量冲突，按照提示选中删除即可。

 ![](https://wiki.tu-zi.com/api/files.get?sig=eyJhbGciOiJIUzI1NiIsInR5cCI6IkpXVCJ9.eyJrZXkiOiJ1cGxvYWRzL2FjNjBlNmRhLTdjYTQtNDdjMS04ZTQxLTAxMDUyMDAwNzM3NS83YmYwMjc0ZS1lZWVkLTQ0NWMtODdmZC0wODg2OGI3MWMzNTkv5LyB5Lia5b6u5L-h5oiq5Zu-XzRjZmNkN2U2LWRjYzItNDJmNC04OWFlLWIzNjZjMThmYzAwNy5wbmciLCJ0eXBlIjoiYXR0YWNobWVudCIsImlhdCI6MTc4MDQ1NDg5NywiZXhwIjoxNzgwNDU4NDk3fQ.xE6EOrFTaZNGNLNr8t0gOeJddXrbBH85cr-OUesx2ik " =514x334") ![](https://wiki.tu-zi.com/api/files.get?sig=eyJhbGciOiJIUzI1NiIsInR5cCI6IkpXVCJ9.eyJrZXkiOiJ1cGxvYWRzL2FjNjBlNmRhLTdjYTQtNDdjMS04ZTQxLTAxMDUyMDAwNzM3NS82ODYxYTYyMC00ODYxLTRjNGQtOTAzMy1iZjM5NzVmZWJlN2Ev5LyB5Lia5b6u5L-h5oiq5Zu-XzdmODNjMzY3LTdkMTItNGEyYS04OTdjLTExY2FhYjM0ZWUyOC5wbmciLCJ0eXBlIjoiYXR0YWNobWVudCIsImlhdCI6MTc4MDQ1NDg5NywiZXhwIjoxNzgwNDU4NDk3fQ.hfRK-sWUnxHGlojVwVCJypWmaeKYBGjLKJ_bIkvDJko " =514x334")


---

## Claude 配置步骤🤖

### 第 1 步：新增 Claude 供应商

在 cc-switch 中进入 Claude 的供应商配置页，点击"新增供应商"。

填写：

* **供应商名称**：例如`tuzi-claude`
* **API Key**：填 tuzi 的 **Claude 分组 Key**
* **请求地址 / Base URL**：`https://api.tu-zi.com`
* **API 格式**：`Anthropic Messages`
* **模型选择：**指定默认使用的 Claude 模型，留空则使用系统默认

  ![](https://wiki.tu-zi.com/api/files.get?sig=eyJhbGciOiJIUzI1NiIsInR5cCI6IkpXVCJ9.eyJrZXkiOiJ1cGxvYWRzL2FjNjBlNmRhLTdjYTQtNDdjMS04ZTQxLTAxMDUyMDAwNzM3NS82MmNmYjVjYS00NDkxLTQ5NzAtYmU5MC1iYWNhNjZiNDZkOTQvMi0yNi0wMS5naWYiLCJ0eXBlIjoiYXR0YWNobWVudCIsImlhdCI6MTc4MDQ1NDg5NywiZXhwIjoxNzgwNDU4NDk3fQ.czeYNINMMPxhEYofey-aB4G-bOarbWuy_fPSM0-7OSY " =514x361")

  \


---

### 第 2 步：查看 cc-switch 自动生成的 JSON

保存后，cc-switch 通常会生成类似内容：

```json
{
  "env": {
    "ANTHROPIC_AUTH_TOKEN": "你的Key",
    "ANTHROPIC_BASE_URL": "https://api.tu-zi.com"
  },
  "includeCoAuthoredBy": false
}
```


---

### 第 3 步（重点）：把 `ANTHROPIC_AUTH_TOKEN` 改成 `ANTHROPIC_API_KEY` ✍️

你需要手动改成：

```json
{
  "env": {
    "ANTHROPIC_API_KEY": "你的Key",
    "ANTHROPIC_BASE_URL": "https://api.tu-zi.com"
  },
  "includeCoAuthoredBy": false
}
```

然后点击保存.

 ![](https://wiki.tu-zi.com/api/files.get?sig=eyJhbGciOiJIUzI1NiIsInR5cCI6IkpXVCJ9.eyJrZXkiOiJ1cGxvYWRzL2FjNjBlNmRhLTdjYTQtNDdjMS04ZTQxLTAxMDUyMDAwNzM3NS9mZDg3MTExMS04OTAzLTQzMWEtYmFkOC0xZmNlZmRkYWJkNTAvMi0yNi0wMi5naWYiLCJ0eXBlIjoiYXR0YWNobWVudCIsImlhdCI6MTc4MDQ1NDg5NywiZXhwIjoxNzgwNDU4NDk3fQ.Oe62a87nuJgVSRZHIH4h3T0mjNouLbfabz80GJggriA " =514x361")



---

### 第 4 步：重启会话并测试

* 关闭当前 Claude 会话（或终端）
* 重新启动
* 发一个简单请求测试（例如"你好"或小段代码解释）

如果能正常返回，说明 Claude 配置完成 ✅


---

## Codex 配置步骤（完整详细）🧠

### 第 1 步：（若本地已配置过codex）备份并删除原有配置文件

在终端执行：

```bash
for f in config.toml auth.json; do [ -f ~/.codex/$f ] && mv ~/.codex/$f ~/.codex/$f.bak; done
```

### 第 2 步：新增 Codex 供应商

进入 Codex 供应商页，点击新增。

填写：

* **供应商名称**：例如 `tuzi-codex`
* **API Key**：填 tuzi 的 **Codex 分组 Key**
* **请求地址 / Base URL**：`https://api.tu-zi.com/v1`\n⚠️ **注意**：Codex 接口通常带 `/v1`。
* **API 格式**：`Anthropic Messages`（按你的要求）

点击保存即可。

 ![](https://wiki.tu-zi.com/api/files.get?sig=eyJhbGciOiJIUzI1NiIsInR5cCI6IkpXVCJ9.eyJrZXkiOiJ1cGxvYWRzL2FjNjBlNmRhLTdjYTQtNDdjMS04ZTQxLTAxMDUyMDAwNzM3NS9jMDk0NTQ4Ni1jYzdhLTQ0NWItOTU0Ny0zNWRjMmY5YWU5YzQvMi0yNi0wMy5naWYiLCJ0eXBlIjoiYXR0YWNobWVudCIsImlhdCI6MTc4MDQ1NDg5NywiZXhwIjoxNzgwNDU4NDk3fQ.F5sgvPChUF0NvA8XX3Txde_Oa1Gy0SAUsNSML-frwD0 " =514x361")



---

### 第 3 步：测试

切换到刚配置的 Codex 供应商，发起一次简单请求，确认能正常返回 ✅


---
