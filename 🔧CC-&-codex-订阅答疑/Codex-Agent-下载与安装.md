# Codex Agent 下载与安装

> 适用对象：需要安装 Codex 图形界面桌面客户端的用户。

## 先确认产品范围

本教程中的“Codex 下载”指 **Codex Agent（Codex App）桌面客户端**，不是 Codex API，也不是命令行版 Codex CLI。安装完成后的兔子线路配置，请继续阅读 [Codex 桌面客户端使用方案](Codex桌面客户端使用方案.md)。

## 根据电脑选择下载方式

| 电脑 | 正确下载方式 | 说明 |
| --- | --- | --- |
| Windows 10/11 | 官方 Windows 安装器 | 直接运行安装器，也可使用 `winget` |
| Mac，Apple 芯片 | `Codex.dmg` | 适用于 M1、M2、M3、M4 及后续 Apple 芯片 |
| Mac，Intel 芯片 | `Codex-latest-x64.dmg` | 只适用于“关于本机”显示 Intel 的 Mac |

Mac 不确定芯片时，点击左上角苹果菜单 → “关于本机”，查看“芯片”或“处理器”。显示 M1/M2/M3/M4 等 Apple 芯片时选择 Apple 芯片版，显示 Intel 时选择 Intel 版。

## 官方下载入口

- [Windows 官方安装器](https://get.microsoft.com/installer/download/9PLM9XGG6VKS?cid=website_cta_psi)
- [Apple 芯片 Mac 官方镜像](https://persistent.oaistatic.com/codex-app-prod/Codex.dmg)
- [Intel Mac 官方镜像](https://persistent.oaistatic.com/codex-app-prod/Codex-latest-x64.dmg)

## 安装步骤

### Windows

1. 打开上方 Windows 下载入口，保存官方安装器。
2. 双击运行安装器，按系统提示完成安装。
3. 安装完成后，从开始菜单打开 Codex，并按页面提示登录。

如果更习惯使用命令行，也可以在 Windows 终端或 PowerShell 中执行：

```powershell
winget install Codex -s msstore
```

### macOS

1. 先在“关于本机”确认 Apple 芯片或 Intel 芯片，再下载对应 DMG。
2. 打开下载完成的 DMG，将 Codex 拖入“应用程序”文件夹。
3. 从“应用程序”打开 Codex，按页面提示完成登录。

## 常见问题

### Windows 打不开 Microsoft Store

先使用本教程提供的官方安装器；仍然失败时，在终端执行 `winget` 命令。若 `msstore` 源异常，可先查看：

```powershell
winget source list
```

必要时再执行：

```powershell
winget source reset --force
```

### Mac 提示无法打开

先确认下载地址和芯片版本正确，再到“系统设置 → 隐私与安全性”查看系统拦截原因。不要为了绕过提示下载第三方修改版。

### 需要使用兔子线路

完成安装后，可以先看 [CC Switch 下载与安装](../⚙️-开发集成/🔧-CC-Switch-下载与安装.md)，再按需阅读 [cc-switch 兔子模型配置教程](../⚙️-开发集成/🔧-用-cc-switch-配置-tuzi-第三方模型（Claude-Code-+-Codex）.md) 或 [Codex 桌面客户端使用方案](Codex桌面客户端使用方案.md)。下载教程不会要求填写 API Key、Token 或兑换码。

## 安全提醒

只使用本页列出的官方地址。不要下载所谓“绿色版”“破解版”或第三方打包版，避免账号、代码和本地文件泄露。
