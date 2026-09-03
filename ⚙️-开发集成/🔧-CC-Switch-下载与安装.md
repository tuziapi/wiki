# 🔧 CC Switch 下载与安装

> 适用对象：需要安装 CC Switch，并在多个 Codex / Claude Code 供应商之间切换的用户。

## 先确认官方下载入口

CC Switch 是免费的开源桌面工具。请只从官方 GitHub Releases 下载：

- [CC Switch 官方 Releases](https://github.com/farion1231/cc-switch/releases/latest)
- 官方仓库：`farion1231/cc-switch`

截至 2026-08-03 核对的版本为 `v3.19.1`。版本号和文件名会更新，请始终从 `releases/latest` 进入，不要依赖历史截图中的固定版本号。

> CC Switch（`farion1231/cc-switch`）与兔子 Switch（`tuziapi/tuzi-switch`）不是同一个软件，请注意区分。

## 按系统和架构选择安装包

| 系统 / 架构 | 优先选择 | 可选方式 |
| --- | --- | --- |
| Windows x64 | `Windows.msi` | `Windows-Portable.zip` |
| Windows ARM64 | `Windows-arm64.msi` | `Windows-arm64-Portable.zip` |
| macOS | `macOS.dmg` | `macOS.zip` 或 Homebrew |
| Debian / Ubuntu | `Linux-x86_64.deb` | ARM 设备选择 `Linux-arm64.deb` |
| Fedora / RHEL | 对应架构的 `.rpm` | 不要混用 `x86_64` 与 `arm64` |
| 其他 Linux | 对应架构的 `.AppImage` | 首次运行前添加可执行权限 |

Windows 查看架构：打开“设置 → 系统 → 系统信息/关于 → 系统类型”。绝大多数普通电脑是 x64，只有 ARM Windows 设备才选择文件名含 `arm64` 的版本。

## 安装步骤

### Windows

1. 在 Releases 页的 Assets 中下载与电脑架构匹配的 `.msi`。
2. 双击 `.msi`，按安装向导完成安装，然后从开始菜单打开 CC Switch。
3. 如果使用 Portable 版，先完整解压，再从解压后的文件夹运行，不要在压缩包内直接启动。

### macOS

1. 下载文件名带 `macOS` 的 `.dmg`。
2. 打开 DMG，将 CC Switch 拖入“应用程序”，再从“应用程序”启动。
3. 已安装 Homebrew 时，也可以执行：

   ```bash
   brew install --cask cc-switch
   ```

### Linux

1. Ubuntu、Debian、Linux Mint 优先选择 `.deb`；Fedora、RHEL、CentOS、Rocky Linux 选择 `.rpm`。
2. 其他发行版可选择 `.AppImage`，首次运行前为文件添加可执行权限。
3. 文件名中的 `x86_64` 与 `arm64` 必须和设备架构一致。

## Releases 页面文件说明

| 文件后缀 | 用途 | 普通用户是否运行 |
| --- | --- | --- |
| `.msi` / `.dmg` / `.deb` / `.rpm` | 对应系统的安装包 | 是，按系统选择 |
| `Portable.zip` | Windows 便携版 | 解压后运行 |
| `.AppImage` | Linux 单文件应用 | 添加执行权限后运行 |
| `.sig` | 数字签名验证文件 | 否 |
| `latest.json` | 自动更新元数据 | 否 |

## 安全提醒

- 只使用官方 GitHub Releases，不要下载所谓“绿色版”“破解版”或第三方打包版。
- 任何向你收费、要求充值或索取登录凭据的“CC Switch”网站或客户端，都应先核实来源。
- 不要把完整 API Key、Token 或密码发给他人。

## 下一步：配置兔子模型

安装完成后，再阅读 [用 cc-switch 配置 tuzi 第三方模型（Claude Code + Codex）](🔧-用-cc-switch-配置-tuzi-第三方模型（Claude-Code-+-Codex）.md)。
