# 🔧 Claude 一键安装工具与常见问题

## 1）前置准备

* 电脑保持联网状态
* 可用的 API Key（支持 api.tu-zi / gaccode）


---

## 2）开始安装

### macOS / Linux

 ![](https://wiki.tu-zi.com/api/files.get?sig=eyJhbGciOiJIUzI1NiIsInR5cCI6IkpXVCJ9.eyJrZXkiOiJ1cGxvYWRzL2FjNjBlNmRhLTdjYTQtNDdjMS04ZTQxLTAxMDUyMDAwNzM3NS85NTRkY2IzZC0zZWFkLTQ2YTMtOTIzYS0wY2U4ZmNjNTBmMGQvMy0wNi0wMi5naWYiLCJ0eXBlIjoiYXR0YWNobWVudCIsImlhdCI6MTc4MDQ1NDk1NiwiZXhwIjoxNzgwNDU4NTU2fQ.TZoUqg8_pit0q0ODglb8Z4S1D-PCcLldH-QCvDS3cqg " =642x439")



1. 打开终端（Terminal）
2. 复制安装命令并粘贴到终端执行

   
   1. macOS 指令

      ```bash
      curl -fsSL https://sh.tu-zi.com/sh/install_claude/install_claude.sh | bash
      ```
   2. Linux 指令

      ```bash
      curl -fsSL https://sh.tu-zi.com/sh/install_claude/install_claude_linux.sh | bash
      ```
3. 按提示输入方案（如果电脑通过其他渠道安装过claude，建议都卸载重新安装）
4. 安装完成后输入：`claude`

### Windows

 ![](https://wiki.tu-zi.com/api/files.get?sig=eyJhbGciOiJIUzI1NiIsInR5cCI6IkpXVCJ9.eyJrZXkiOiJ1cGxvYWRzL2FjNjBlNmRhLTdjYTQtNDdjMS04ZTQxLTAxMDUyMDAwNzM3NS9hMGY3YWE3ZC05ZGE1LTQwYTItYjk4OS03MDU2N2NjN2FlYmMvMy0wNi0wMS5naWYiLCJ0eXBlIjoiYXR0YWNobWVudCIsImlhdCI6MTc4MDQ1NDk1NiwiZXhwIjoxNzgwNDU4NTU2fQ.PtQXldn-sdKy8ZKMNOhdUysAI9eYm5bgKHi0USZ3RZs " =556x360")



1. 按下 win+R 后输入 powershell 打开终端
2. 复制安装命令并执行

   ```bash
   irm https://sh.tu-zi.com/sh/install_claude/install_claude_windows.ps1 | iex
   ```
3. 按提示输入方案（如果电脑通过其他渠道安装过claude，建议都卸载重新安装）
4. 关闭窗口后重新打开终端，输入：`claude`
5. 若 powershell 不支持，按下 win+R 后输入 cmd 并打开，再尝试运行 claude


---

## 3）A / B / C 怎么选

* **A：改版 Claude - gaccode 渠道**（完全不需要输入任何 Key；首次登录会自动跳转网页完成登录）
* **B：原版 Claude + gaccode Key**
* **C：原版 Claude + tu-zi Key**

如果你不确定先选哪个：

* 最便捷：选 **A**
* 你有 gaccode key：选 **B**
* 你有 tu-zi key：选 **C**


---

## 4）已经装过了怎么办

重新执行同一脚本后，会看到：


1. 卸载并重新安装（推荐）
2. 仅切换路线
3. 升级 Claude Code（保留配置）

直接输入对应数字即可：`1 / 2 / 3`


---

## 5）新手常见问题（FAQ）

### Q1：提示"未检测到 npm，请先安装 Node.js 和 npm"

处理：先安装 Node.js（会带 npm）。

* macOS（有 Homebrew）：`brew install node`
* Linux：使用你的系统包管理器安装 nodejs/npm
* Windows：去 Node.js 官网下载安装


---

### Q2：安装完成后 `claude` 不能用

处理顺序：


1. 先关闭终端
2. 再打开一个新终端
3. 再次输入：`claude`

如果还不行，重新运行脚本并选择 `1）卸载并重新安装`。


---

### Q3：脚本提示"未检测到有效的 API 配置"

这是原版常见提示。建议直接选重装，按提示重新输入 Key。


---

### Q4：原版已安装但提示没有路线配置文件

建议按提示输入 `1）卸载并重新安装` -> `y` 直接进入重装流程。


---

### Q5：切换路线后像是没生效

处理：


1. 关闭终端
2. 打开新终端
3. 输入 `claude`


---

### Q6：提示"改版不支持路线修改"

这是正常行为。改版如需切路线，请先卸载，再按原版方案重装。


---

如果你只记一件事： **打不开就重开终端；还不行就重装。**