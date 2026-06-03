# 🔧 Codex yoga.wasm 报错修复

# Codex Pick-Relay 命令错误解决方案

## 问题描述

执行 `codex --pick-relay` 命令时出现以下错误： Error: Cannot find module './yoga.wasm' Require stack:

* /Users/\[用户名\]/\[项目路径\]/node_modules/yoga-wasm-web/dist/node.js

## 解决方案

### 步骤1：重新安装 Codex

**重要：必须使用 gaccode.com 的安装源**

```bash
# 卸载现有的 codex
npm uninstall -g codex
```

```bash
# 安装正确版本的 codex
npm install -g https://gaccode.com/codex/install
```

### 步骤2：检查 Node.js 版本

确保 Node.js 版本 >= 20：

```bash
  # 检查当前版本
  node --version
```

```bash
  # 如果版本低于 20，使用 nvm 升级
  nvm install 20
  nvm use 20
```

### 步骤3：解决硬编码路径问题

3\.1 查看具体错误路径

先执行一次命令，记录错误信息中的具体路径：

```bash
  codex --pick-relay
```

3\.2 创建所需目录结构

根据错误信息中显示的路径创建目录（替换为你看到的实际路径）：

```bash
  # 示例路径，请替换为你的实际错误路径
  mkdir -p "/Users/[你的用户名]/[你的项目路径]/node_modules/yoga-wasm-web/dist/"
```

3\.3 查找系统中的 yoga.wasm 文件

```bash
  find /usr -name "yoga.wasm" 2>/dev/null
```

3\.4 创建符号链接

使用上一步找到的文件路径创建符号链接：

```bash
  # 替换路径为你的实际情况
  ln -sf "[找到的yoga.wasm完整路径]" "[错误信息中的目录路径]/yoga.wasm"
```

```bash
  # 示例：
  # ln -sf "/usr/lib/node_modules/@anthropic-ai/claude-code/node_modules/yoga-wasm-web/dist/yoga.wasm" "/Users/kevin/project/node_modules/yoga-wasm-web/dist/yoga.wasm"
```

### 步骤4：验证修复

重新执行命令：

```bash
  codex --pick-relay
```

如果看到进度条和网络扫描过程，说明修复成功。最后可能出现的 "Raw mode is not supported" 错误是终端兼容性问题，不影响核心功能。

注意事项

* 错误路径因用户和系统不同而异，请根据实际错误信息调整
* 某些系统可能需要 sudo 权限来创建目录和符号链接
* 确保使用 gaccode.com 的安装源，其他源可能导致问题
* Node.js 版本必须 >= 20，低版本会有兼容性问题

故障排除

如果仍然遇到问题：


1. 检查权限：确保有足够权限创建目录和文件
2. 检查路径：确认错误信息中的路径被正确复制
3. 检查符号链接：使用 ls -la \[目标路径\] 检查链接是否正确创建
4. 重启终端：有时需要重启终端使更改生效

技术原理

此错误是由于 codex 内部存在硬编码路径问题，程序寻找特定目录结构中的 yoga.wasm 文件。通过创建符号链接，我们将硬编码路径指向系统中实际存在的 yoga.wasm 文件，从而解决模块加载问题。