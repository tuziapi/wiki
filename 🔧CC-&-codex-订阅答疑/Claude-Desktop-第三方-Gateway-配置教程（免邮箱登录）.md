# Claude Desktop 第三方 Gateway 配置教程（免邮箱登录）

# Claude Desktop 第三方 Gateway 配置教程（免邮箱登录）

适用对象：已经安装 Claude Desktop App，希望通过第三方 Gateway 的 URL 和 API key 使用 Claude，而不是登录 Anthropic 邮箱账号的用户。

## 一句话结论

Claude Desktop 可以通过第三方 Gateway 的 URL 和 API key 直接接入使用，不需要登录 Anthropic 邮箱账号。

配置完成后，启动时选择 `Continue with Gateway` 即可进入 `Cowork 3P | Gateway` 模式。

需要注意的是：`Developer` 菜单只是配置入口，不是日常使用开关。配置保存后，可以关闭开发者模式；平时继续使用 Gateway 不受影响。

## 你需要准备

| 项目  | 示例  | 说明  |
|-----|-----|-----|
| Gateway URL | `https://api.tu-zi.com/v1` | 按供应商提供的地址填写。 |
| API key | `sk-...` | 只填到 Claude App，不要写进文档或截图。 |
| 模型名称 | `claude-opus-4-6`、`claude-opus-4-7` | 当前版本的配置面板会要求至少填一个模型。 |

本文档验证过：URL + key 可以进入 Claude Desktop 的 Gateway 模式；如果后续报模型不可用，通常是网关模型渠道、权限、额度或负载问题，不是邮箱登录问题。

## 完整流程

`开启开发者模式 -> 重启 Claude -> 顶部菜单出现 Developer -> Configure Third-Party Inference... -> 填 URL、API key、模型 -> Apply locally -> Continue with Gateway`

如果你只想快速完成配置，照着上面这条流程走一遍即可；下面是逐步说明。

## 第一步：开启 Developer 菜单

Claude Desktop 默认隐藏 `Developer` 菜单。没开启开发者模式时，你在 macOS 顶部菜单栏里只能看到：

`Claude / File / Edit / View / Window / Help`

看不到 `Developer` 是正常的。

 ![Developer 菜单入口标注](https://wiki.tu-zi.com/api/files.get?sig=eyJhbGciOiJIUzI1NiIsInR5cCI6IkpXVCJ9.eyJrZXkiOiJ1cGxvYWRzLzA0MTA4NzY3LTk1YjgtNDYzMi05YWFmLTgwNzgwZjIwMmFkMi8yNzY5OTk0Ni0wOTViLTQ1Y2MtOGY2ZS04YjIyNDFiZmFlMmUvMDFfYXBwX21lbnVfZW50cnlfYW5ub3RhdGVkLnBuZyIsInR5cGUiOiJhdHRhY2htZW50IiwiaWF0IjoxNzgwNDU0OTUwLCJleHAiOjE3ODA0NTg1NTB9.4YOEZYcXmssBEXEeBX8BHPUUi4Znc9v2ViPMbySIz74)

开启方式：


1. 完全退出 Claude Desktop。
2. 找到或创建下面的配置文件：

```text
~/Library/Application Support/Claude/developer_settings.json
```

如果你使用的是本教程验证过的 3P 数据目录，也可以同时设置：

```text
~/Library/Application Support/Claude-3p/developer_settings.json
```


3. 写入下面内容：

```json
{
  "allowDevTools": true
}
```


4. 重新打开 Claude Desktop。
5. 点击 Claude 窗口，让 Claude 成为当前 App。
6. 看屏幕最顶部菜单栏，应该出现 `Developer`。

为什么要重启 Claude：`Developer` 菜单是在 Claude 启动时根据 `developer_settings.json` 生成的。App 已经运行时再改文件，不一定会立刻刷新菜单。

## 第二步：进入第三方供应商配置

在 macOS 顶部菜单栏点击：

```text
Developer -> Configure Third-Party Inference...
```

注意：`Developer` 是屏幕最顶部的系统菜单栏，不在 Claude 左侧栏，也不是聊天窗口里的按钮。

如果屏幕左上角显示的是 `Finder`、`Chrome`、`Codex` 等，说明当前激活的不是 Claude。先点一下 Claude 窗口，再看顶部菜单。

## 第三步：填写 Gateway 配置

在 `Configure third-party inference` 页面里选择 `Gateway`，然后填写：

| 字段  | 填法  |
|-----|-----|
| Gateway base URL | `https://api.tu-zi.com/v1` |
| Gateway API key | 填你的 API key |
| Gateway auth scheme | 保持 `bearer` |
| Model list | 例如 `claude-opus-4-6`、`claude-opus-4-7` |

填完后点击 `Apply locally`。如果 Claude 提示重启，选择 `Relaunch now`。

如果 `Apply locally` 是灰色，通常是必填项没填完整。当前版本里 `Model list` 也可能被标成必填。

 ![Gateway 配置面板标注](https://wiki.tu-zi.com/api/files.get?sig=eyJhbGciOiJIUzI1NiIsInR5cCI6IkpXVCJ9.eyJrZXkiOiJ1cGxvYWRzLzA0MTA4NzY3LTk1YjgtNDYzMi05YWFmLTgwNzgwZjIwMmFkMi9mOTQ0NThiZi0xNDQ3LTQ4ZGMtYmNjMy03YWNiNmNkMzZlMTcvMDJfZ2F0ZXdheV9jb25maWdfYW5ub3RhdGVkLnBuZyIsInR5cGUiOiJhdHRhY2htZW50IiwiaWF0IjoxNzgwNDU0OTUwLCJleHAiOjE3ODA0NTg1NTB9.gsRYZ-xxnH02ro3sNYH-BW2leko95c72QPjHPCwvL84)

## 第四步：不用邮箱登录，选择 Gateway

重启后，如果出现登录页，不要填邮箱。

如果底部有：

```text
Or continue with Gateway
```

点击它。

如果出现选择页：

```text
How do you want to use Claude?
```

选择：

```text
Continue with Gateway
No Anthropic account needed
```

进入后，左下角显示：

```text
Cowork 3P | Gateway
```

这就表示已经进入第三方 Gateway 模式。

 ![Gateway 模式成功状态标注](https://wiki.tu-zi.com/api/files.get?sig=eyJhbGciOiJIUzI1NiIsInR5cCI6IkpXVCJ9.eyJrZXkiOiJ1cGxvYWRzLzA0MTA4NzY3LTk1YjgtNDYzMi05YWFmLTgwNzgwZjIwMmFkMi8yMTZmMDE0Yi03ZmYzLTQyODUtOTFjYS1iNWM3MDFiZWFiMmUvMDNfM3BfcmVhZHlfYW5ub3RhdGVkLnBuZyIsInR5cGUiOiJhdHRhY2htZW50IiwiaWF0IjoxNzgwNDU0OTUwLCJleHAiOjE3ODA0NTg1NTB9.F2GxUsttZJC8iq3Q6cRjTOFoRTqjytfYsni14sz8mtE)

## 开发者模式要一直开着吗

不需要。

开发者模式只用于显示配置入口：

```text
Developer -> Configure Third-Party Inference...
```

配置保存以后，可以把 `developer_settings.json` 改回：

```json
{
  "allowDevTools": false
}
```

重启 Claude 后，`Developer` 菜单会消失，但已经保存的 `Cowork 3P | Gateway` 配置仍然可以继续使用。

只有在你需要修改 URL、key、模型列表或重新打开第三方配置面板时，才需要再次开启开发者模式。

## 以后想改 URL/key，在哪里打开设置

如果已经进入 `Cowork 3P | Gateway`，以后想修改 URL、API key 或模型列表，有两种入口。

**方法一：点黄色报错框里的** `**Open Setup**`**。**

当页面上方出现 `Gateway returned an error` 这类黄色提示框时，里面通常会有 `Open Setup` 按钮。点击它，会直接回到 `Configure third-party inference` 配置页，可以修改 URL、key 和模型列表。

 ![Open Setup 入口标注](https://wiki.tu-zi.com/api/files.get?sig=eyJhbGciOiJIUzI1NiIsInR5cCI6IkpXVCJ9.eyJrZXkiOiJ1cGxvYWRzLzA0MTA4NzY3LTk1YjgtNDYzMi05YWFmLTgwNzgwZjIwMmFkMi82YjcwOGQ0OC1hOGY1LTRiNDAtOTc5Ny01OTJkYmRmYTU3ZDkvMDRfb3Blbl9zZXR1cF9lbnRyeV9hbm5vdGF0ZWQucG5nIiwidHlwZSI6ImF0dGFjaG1lbnQiLCJpYXQiOjE3ODA0NTQ5NTAsImV4cCI6MTc4MDQ1ODU1MH0.QaUpk79OjaaphAQv66j9YZHD6hrfI7LAW8MAbkUhcRQ)

**方法二：重新开启 Developer 菜单。**

如果页面上没有 `Open Setup`，就临时打开开发者模式：


1. 退出 Claude。
2. 把 `developer_settings.json` 改成 `{ "allowDevTools": true }`。
3. 重新打开 Claude。
4. 点击 Claude 窗口，让 macOS 顶部菜单栏切到 Claude。
5. 点击 `Developer -> Configure Third-Party Inference...`。
6. 修改 URL、API key 或 `Model list`。
7. 点击 `Apply locally`，按提示重启。

改完以后，可以再把开发者模式关掉。开发者模式只负责显示配置入口；已经保存的 Gateway 配置仍然可以继续使用。

## 常见报错与排查

### 1. Gateway returned HTTP 404

示例：

```text
Gateway returned an error
httpStatus: 404
endpoint: https://api.tu-zi.com/
```

这不代表邮箱登录失败。通常表示 Claude 的 Gateway 自检请求被网关拒绝，或者网关根路径没有健康检查接口。

如果黄色报错框里有 `Open Setup`，可以直接点它回到 URL、key 和模型列表的设置页。

判断配置是否已经生效，看两个位置：

* 左下角是否显示 `Cowork 3P | Gateway`
* `claude_desktop_config.json` 是否出现 `"deploymentMode": "3p"`

如果都成立，说明 App 已经进入 Gateway 模式。

### 2. There's an issue with the selected model

示例：

```text
There's an issue with the selected model (claude-opus-4-7).
It may not exist or you may not have access to it.
```

这是模型问题，不是 Developer 模式问题，也不是邮箱登录问题。

常见原因：

* 当前 key 所属分组没有这个模型的渠道。
* 模型名在列表里能看到，但实际调用没有权限。
* 渠道临时不可用、负载高或额度不足。

处理办法：

* 换一个实际可调用的模型。
* 联系 Gateway 服务商确认当前 key 是否有该模型权限。
* 不要只看 `/v1/models` 列表，最好实际发一条最小请求测试。

## 本机验证结果

验证时间：2026-04-27

本次从清空第三方推理字段开始重新配置，不依赖已有成功配置。

| 验证项 | 结果  |
|-----|-----|
| `/v1/models` 鉴权 | 200，可读取模型列表 |
| App 免邮箱入口 | 通过，出现 `Continue with Gateway` |
| App 模式 | 通过，进入 \`Cowork 3P |
| `deploymentMode` | 已写入 `3p` |
| `claude-opus-4-6` | App 内报模型不可用；直接 API 曾返回 200 但耗时较长且回复异常 |
| `claude-opus-4-7` | 直接 API 返回 503，提示当前分组无可用渠道 |

结论：URL + key 的 App 配置链路可行；具体模型是否能稳定使用，需要以 Gateway 服务商的模型渠道和账号权限为准。

## 使用建议与安全提醒

* 不要把完整 API key 写进教程、截图、聊天记录或公开文档。
* 分享给其他用户时，只分享发布版 PDF、Word、Markdown 和截图。
* 不要把 `test_backups` 目录一起发出去；测试备份可能包含本机配置或敏感信息。

## 文件说明

| 文件  | 用途  |
|-----|-----|
| `ClaudeCode_API_Key_NoEmail_Tutorial.pdf` | 面向用户的 PDF 版教程 |
| `ClaudeCode_API_Key_NoEmail_Tutorial.docx` | 可编辑 Word 版教程 |
| `README.md` | Markdown 版教程 |
| `04_developer_mode_app_test.md` | 本机验证记录和技术附录 |
| `01_app_menu_entry_annotated.png` | Developer 菜单入口标注 |
| `02_gateway_config_annotated.png` | Gateway 配置面板标注 |
| `03_3p_ready_annotated.png` | Gateway 模式成功状态标注 |
| `04_open_setup_entry_annotated.png` | Open Setup 返回设置页入口标注 |