# (已废弃)Claude Code 安装及使用教程

# **Claude Code 安装及使用教程请点击跳转以下链接**


1. [方案一：改版 Claude Code + 订阅账户](https://wiki.tu-zi.com/s/8c61a536-7a59-4410-a5e2-8dab3d041958/doc/gaccode-elzksQdhFx)  ；**强烈推荐这个，如果你稍微强度点跑，比方案二就能省数十倍乃至百倍以上的费用**
2. [方案二：官方原版 + 兔子折扣 API](https://wiki.tu-zi.com/s/8c61a536-7a59-4410-a5e2-8dab3d041958/doc/api-QVB4CXRqJN) 


\
没有 Claude Pro/Max 也想用 Claude Code？试试 **兔子 API**


---

# 目录

# 方案一：改版 Claude Code + 订阅账户

## 1. 安装并运行

> 改版会自动适配路径，**主要解决线路稳定性问题**，请放心使用 原版claude也能用，但是人多会经常性timeout

### 1.1 系统要求

* **操作系统**：macOS 10.15+ / Ubuntu 20.04+ / Debian 10+ / Windows
* **硬件**：≥ 2 GB RAM
* **软件**：
  * Node.js 18+
  * Git 2.23+（可选，用于源码克隆）
  * GitHub/GitLab CLI（可选，用于 PR 工作流）
* **网络**：**无需翻墙**

### 1.2 安装 Claude Code (改编版)

```bash
npm install -g https://gaccode.com/claudecode/install --registry=https://registry.npmmirror.com
```

> `-g` 表示全局安装，可在任意目录调用 `claude`

如果已经安装过原版的，可执行如下卸载

```
npm uninstall -g @anthropic-ai/claude-code

rm -rf ~/.claude*
```

## 2. 启动与登录

**如果遇到与cc链接的网络问题：claude --pick-relay 切换线路试下**

```bash
# 进入项目目录
cd your-project-folder

# 启动 Claude Code
claude
```

浏览器登录并绑定账户：\n注意：一定要用邀请链接注册的才有购买月卡的1万积分赠送，兔子的邀请链接；然后复制窗口中的https地址进行绑定

 ![](https://wiki.tu-zi.com/api/files.get?sig=eyJhbGciOiJIUzI1NiIsInR5cCI6IkpXVCJ9.eyJrZXkiOiJ1cGxvYWRzL2UxMjc0Y2E3LWNmZTEtNDdlOC04MjA0LTNhMDkzMTNlNzM4ZC85ZGM1Y2QyMC01MzFhLTQwMTQtODUyOS1mYTAyMTA3ZGEyM2QvaW1hZ2UucG5nIiwidHlwZSI6ImF0dGFjaG1lbnQiLCJpYXQiOjE3ODA0NTQ5MDcsImV4cCI6MTc4MDQ1ODUwN30.sfMGRIfolLgRsQEjn45fqGGt3N_vBzqIieKvnKBKG5Y " =1405x919")   ![](https://wiki.tu-zi.com/api/files.get?sig=eyJhbGciOiJIUzI1NiIsInR5cCI6IkpXVCJ9.eyJrZXkiOiJ1cGxvYWRzL2UxMjc0Y2E3LWNmZTEtNDdlOC04MjA0LTNhMDkzMTNlNzM4ZC9jODdkODhiNy1jMTgwLTQ2ZWQtOTZjMi0zMzQwYThlNTQ3YTIvaW1hZ2UucG5nIiwidHlwZSI6ImF0dGFjaG1lbnQiLCJpYXQiOjE3ODA0NTQ5MDcsImV4cCI6MTc4MDQ1ODUwN30.sy5bd_pCnygm-q7DWXulFeH-2_y4Z1JE88oFMK8ki6g " =1279x801")   ![](https://wiki.tu-zi.com/api/files.get?sig=eyJhbGciOiJIUzI1NiIsInR5cCI6IkpXVCJ9.eyJrZXkiOiJ1cGxvYWRzL2UxMjc0Y2E3LWNmZTEtNDdlOC04MjA0LTNhMDkzMTNlNzM4ZC84NWE0MDg0OC1kY2JiLTQzZTctOTc1OS1lODg0MmNhNGJkNGQvaW1hZ2UucG5nIiwidHlwZSI6ImF0dGFjaG1lbnQiLCJpYXQiOjE3ODA0NTQ5MDcsImV4cCI6MTc4MDQ1ODUwN30.cvbMYlifhH73RvySBapADaexGfsCNEZwnF8BSsnNBA8 " =1260x718")   ![浏览器登录](https://tuziai.oss-cn-shenzhen.aliyuncs.com/wiki/code/claude/claudecode9.png)

* 默认模型：**Claude 4**
* 可强制切换至 Claude 4 Opus\n模型切换

## 3. 购买订阅

购买兑换码（含体验卡）地址：[兔小店](https://store.tu-zi.com)   ![浏览器登录](https://tuziai.oss-cn-shenzhen.aliyuncs.com/wiki/code/claude/claudecode11.png)

或扫码联系客服  

 ![](https://wiki.tu-zi.com/api/files.get?sig=eyJhbGciOiJIUzI1NiIsInR5cCI6IkpXVCJ9.eyJrZXkiOiJ1cGxvYWRzL2UxMjc0Y2E3LWNmZTEtNDdlOC04MjA0LTNhMDkzMTNlNzM4ZC85NmExOTM2Ny1kNTQxLTQ2OGMtYjVhZi03NWFhMjgzZWUxOTkvaW1hZ2UucG5nIiwidHlwZSI6ImF0dGFjaG1lbnQiLCJpYXQiOjE3ODA0NTQ5MDcsImV4cCI6MTc4MDQ1ODUwN30.g_n4PuVcqAZsglI0ToBC-ntNvgJ-kJFAldQ8E10KoYU "left-50 =152x152")


\

\

购买后获得兑换码如"M\*\*-\*5"，再回到[gaccode账户](https://gaccode.com)内激活   ![](https://wiki.tu-zi.com/api/files.get?sig=eyJhbGciOiJIUzI1NiIsInR5cCI6IkpXVCJ9.eyJrZXkiOiJ1cGxvYWRzL2UxMjc0Y2E3LWNmZTEtNDdlOC04MjA0LTNhMDkzMTNlNzM4ZC83N2ZkMDM2ZC1hYjhkLTQ0OGYtOTk5Yi1hOGM4MGM4YzhjMmEvaW1hZ2UucG5nIiwidHlwZSI6ImF0dGFjaG1lbnQiLCJpYXQiOjE3ODA0NTQ5MDcsImV4cCI6MTc4MDQ1ODUwN30.cuhgGzSm1b0eTDXyKckySZfRH_Lavolqhcfz4Jur6q0 " =1324x781")

### 积分说明

**月卡订阅会获得** 1、初始5400积分 2、邀新首充的10000积分

**同时享受2种免费的补充积分方式** 1、等每小时100积分加 2、每日1次的申请重置（恢复初始的5400积分）机会

> 估算：4 byte ≈ 1 token；若一次消耗 50 000 token ≈ 9 积分（含基础 2 分 + 7 分）

积分详情\n积分示例

## 4. 推荐活动

### 邀请好友获得奖励


1. 与朋友分享您的专属推荐链接
2. 您的朋友使用您的链接注册
3. 当他们进行首次消费或后续消费时，您们都将获得奖励！

ℹ️ **注意：账户间的推荐关系是永久有效的**

### 奖励系统

首次消费\n您和您的朋友都将获得 3×2000 积分 + 4×1000 积分

后续消费\n您和您的朋友都将获得 1×2000 积分

💡 被推荐人可以在任何时候进行多次消费，每次符合条件的消费都会获得相应奖励，你可以积累到很多噢

 ![推荐奖励](https://tuziai.oss-cn-shenzhen.aliyuncs.com/wiki/claude-code-mg5.png " =418x902")

## 5. 升级 Claude Code

```bash
npm install -g https://gaccode.com/claudecode/install --registry=https://registry.npmmirror.com
```


---

# 方案二：官方原版 + "兔子折扣API" / "gaccode订阅账户"

## 1. 注册账号并获取 API Key（以下两种任选其一）

### 1.1 api.tu-zi.com上获取


1. 访问
2. 在左侧「**API 令牌创建**」处生成 Key
3. **重点**：分组请选择`Claude-Code` 或`Claude` 或 `Claude原价`（比 `default` 分组稳定得多）
4. 记得在后台为 Key 设置调用限额

### 1.2 gaccode账户中获得

 ![](https://wiki.tu-zi.com/api/files.get?sig=eyJhbGciOiJIUzI1NiIsInR5cCI6IkpXVCJ9.eyJrZXkiOiJ1cGxvYWRzL2UxMjc0Y2E3LWNmZTEtNDdlOC04MjA0LTNhMDkzMTNlNzM4ZC84OWVhNDU0Yy03MDhjLTQ3MzEtYTg5Ny00NjE0MzM3YjI4MTgvaW1hZ2UucG5nIiwidHlwZSI6ImF0dGFjaG1lbnQiLCJpYXQiOjE3ODA0NTQ5MDcsImV4cCI6MTc4MDQ1ODUwN30.cTJFaTlZcOMk4mUj042EawFRZ0c2pkItbDGeNV8-ZA4 " =1284x877")

gaccode订阅获得方式，参考方案一

## 2. 安装并运行 Claude Code

### 2.1 系统要求

* **操作系统**：macOS 10.15+ / Ubuntu 20.04+ / Debian 10+ / Windows
* **硬件**：≥ 2 GB RAM
* **软件**：
  * Node.js 18+
  * Git 2.23+（可选，用于源码克隆）
  * GitHub/GitLab CLI（可选，用于 PR 工作流）
* **网络**

  
  1. 首次身份验证需「科学上网」（非中国大陆及港澳台）
  2. 若使用兔子 API 或 gaccode，后续 AI 调用阶段无需继续翻墙

### 2.2 安装 Claude Code

```bash
# 全局安装（更多用法见官方文档）
npm install -g @anthropic-ai/claude-code
```

如果已经安装过改版的需要卸载，可执行如下卸载

```
npm uninstall -g @anthropic-ai/claude-code

rm -rf ~/.claude*
```

### 2.3 启动与环境变量（根据你的api来源配置）

#### 2.3.1 兔子api

```bash
# 注意，我们用的是key，不是token，为防止冲突，强行重置
export ANTHROPIC_API_TOKEN=""
export ANTHROPIC_API_KEY=sk-xxxxxxxxxxxxxxxxx
export ANTHROPIC_BASE_URL=https://api.tu-zi.com
# win- CMD（命令提示符）中
# setx ANTHROPIC_API_KEY "sk-xxxxxxxxxxxxxxxxx"
# setx ANTHROPIC_BASE_URL "https://api.tu-zi.com"
claude
```

#### 2.3.2 gaccode

```bash
# 注意，我们用的是key，不是token，为防止冲突，强行重置
export ANTHROPIC_API_TOKEN=""
export ANTHROPIC_API_KEY=sk-xxxxxxxxxxxxxxxxx
export ANTHROPIC_BASE_URL=https://gaccode.com/claudecode
# win- CMD（命令提示符）中
# setx ANTHROPIC_API_KEY "sk-xxxxxxxxxxxxxxxxx"
# setx ANTHROPIC_BASE_URL "https://gaccode.com/claudecode"
claude
```

### 2.4 初始化界面示例（Debian 12）


1. 选择外观\n![](https://wiki.tu-zi.com/api/files.get?sig=eyJhbGciOiJIUzI1NiIsInR5cCI6IkpXVCJ9.eyJrZXkiOiJ1cGxvYWRzL2UxMjc0Y2E3LWNmZTEtNDdlOC04MjA0LTNhMDkzMTNlNzM4ZC81ZDMwMTIzMC0yNzMxLTRkNjMtYjM1Yi0xZWY0ZjkzY2Q5NzMvaW1hZ2UucG5nIiwidHlwZSI6ImF0dGFjaG1lbnQiLCJpYXQiOjE3ODA0NTQ5MDcsImV4cCI6MTc4MDQ1ODUwN30.D6WeYlmFPcTgoVCiNeuusc7d2SNw8s6EYJHtiWtFhFk " =1479x906")
2. 选择创建账户 / 已有账户登录\n![](https://wiki.tu-zi.com/api/files.get?sig=eyJhbGciOiJIUzI1NiIsInR5cCI6IkpXVCJ9.eyJrZXkiOiJ1cGxvYWRzL2UxMjc0Y2E3LWNmZTEtNDdlOC04MjA0LTNhMDkzMTNlNzM4ZC9lNWQ2ZDZkYS1jYzdkLTQ4YTgtOTA3Zi1iYWYxODAzMzAzYjIvaW1hZ2UucG5nIiwidHlwZSI6ImF0dGFjaG1lbnQiLCJpYXQiOjE3ODA0NTQ5MDcsImV4cCI6MTc4MDQ1ODUwN30.bivoWc6u7Ipq3y0rGKauMXULxw-iT1iKW5yKg7s19PU " =1363x814")
3. 复制浏览器链接登录 Claude\n![](https://wiki.tu-zi.com/api/files.get?sig=eyJhbGciOiJIUzI1NiIsInR5cCI6IkpXVCJ9.eyJrZXkiOiJ1cGxvYWRzL2UxMjc0Y2E3LWNmZTEtNDdlOC04MjA0LTNhMDkzMTNlNzM4ZC82ZTk2MGZkMS0xY2U4LTQ0ODUtODU0Mi02MzA3MDA1OGYwMjQvaW1hZ2UucG5nIiwidHlwZSI6ImF0dGFjaG1lbnQiLCJpYXQiOjE3ODA0NTQ5MDcsImV4cCI6MTc4MDQ1ODUwN30.6L-t_DYKR-Bl54Wa-NOSoefsUoeWP8lt5Yan1sC_M8I " =1491x817")
4. 粘贴绑定 code\n![](https://wiki.tu-zi.com/api/files.get?sig=eyJhbGciOiJIUzI1NiIsInR5cCI6IkpXVCJ9.eyJrZXkiOiJ1cGxvYWRzL2UxMjc0Y2E3LWNmZTEtNDdlOC04MjA0LTNhMDkzMTNlNzM4ZC9kODRhY2IxNy03YjczLTQxYmYtYjhhMS1hMGExM2NkMmZmYzIvaW1hZ2UucG5nIiwidHlwZSI6ImF0dGFjaG1lbnQiLCJpYXQiOjE3ODA0NTQ5MDcsImV4cCI6MTc4MDQ1ODUwN30.giq9F7hX576jkOw2lPAi5-XP_OQP6aQedw-mUoWkV_0 " =1936x1299")
5. 绑定成功，显示账户邮箱\n![](https://wiki.tu-zi.com/api/files.get?sig=eyJhbGciOiJIUzI1NiIsInR5cCI6IkpXVCJ9.eyJrZXkiOiJ1cGxvYWRzL2UxMjc0Y2E3LWNmZTEtNDdlOC04MjA0LTNhMDkzMTNlNzM4ZC9iY2E4MDMzYS0xMGM1LTRjMDUtODY3ZS1jMzNkODA0MTA3NjIvaW1hZ2UucG5nIiwidHlwZSI6ImF0dGFjaG1lbnQiLCJpYXQiOjE3ODA0NTQ5MDcsImV4cCI6MTc4MDQ1ODUwN30.CYNE-Fn2HUWnn5fZCvuS5quaZhYsxuTfMIdi1pVT4vc " =1486x864")
6. 选择 API 令牌模式\n![](https://wiki.tu-zi.com/api/files.get?sig=eyJhbGciOiJIUzI1NiIsInR5cCI6IkpXVCJ9.eyJrZXkiOiJ1cGxvYWRzL2UxMjc0Y2E3LWNmZTEtNDdlOC04MjA0LTNhMDkzMTNlNzM4ZC9mMThkMDUzYi1iMGIwLTRmNTQtYmRjMS1mNGFkNTZjZmU0YmIvaW1hZ2UucG5nIiwidHlwZSI6ImF0dGFjaG1lbnQiLCJpYXQiOjE3ODA0NTQ5MDcsImV4cCI6MTc4MDQ1ODUwN30.PGLu7yQu6bE3hxnVMZEeK1reQVsj9sKd9TIrdkNJbjk " =1501x723")
7. **登入可以看到设置好的令牌信息,包括key和url** ![](https://wiki.tu-zi.com/api/files.get?sig=eyJhbGciOiJIUzI1NiIsInR5cCI6IkpXVCJ9.eyJrZXkiOiJ1cGxvYWRzL2UxMjc0Y2E3LWNmZTEtNDdlOC04MjA0LTNhMDkzMTNlNzM4ZC8xNzA3OTJiNi0xYTczLTRhMTUtYTc1Yi04MDZhYmY2Yzc4MjkvaW1hZ2UucG5nIiwidHlwZSI6ImF0dGFjaG1lbnQiLCJpYXQiOjE3ODA0NTQ5MDcsImV4cCI6MTc4MDQ1ODUwN30.WPdBRXNjLHOoyupi1ZfSVURpFqDjJ7kAqVS5pl-Rqkc " =1717x1122")

# 🎮 效果演示


1. 提出问题\n![](https://wiki.tu-zi.com/api/files.get?sig=eyJhbGciOiJIUzI1NiIsInR5cCI6IkpXVCJ9.eyJrZXkiOiJ1cGxvYWRzL2UxMjc0Y2E3LWNmZTEtNDdlOC04MjA0LTNhMDkzMTNlNzM4ZC80ZTU2NWMwZS1iZmUxLTRmNDgtYTQ2MS03MjhjNjIxNmJmODMvaW1hZ2UucG5nIiwidHlwZSI6ImF0dGFjaG1lbnQiLCJpYXQiOjE3ODA0NTQ5MDcsImV4cCI6MTc4MDQ1ODUwN30.gn3RHc0NNdBvP-ysBzMYyF90mQ2WRK5TLQqFRPHwH5s " =1477x943")
2. 生成文件保存至服务器对应目录\n![](https://wiki.tu-zi.com/api/files.get?sig=eyJhbGciOiJIUzI1NiIsInR5cCI6IkpXVCJ9.eyJrZXkiOiJ1cGxvYWRzL2UxMjc0Y2E3LWNmZTEtNDdlOC04MjA0LTNhMDkzMTNlNzM4ZC9lOTcwNmFlMi04MDQ0LTRkNGMtYTRlOS1hZDc0MjUxOGY4YWIvaW1hZ2UucG5nIiwidHlwZSI6ImF0dGFjaG1lbnQiLCJpYXQiOjE3ODA0NTQ5MDcsImV4cCI6MTc4MDQ1ODUwN30.DbHdjr9pToJ1g9wusaJqFlmkNFF1ouuD6wEDz0-MFCQ " =907x489")
3. **效果展示**

   [https://www.bilibili.com/video/BV1Q4MkzVEpU?share%5Fsource=copy%5Fweb](https://www.bilibili.com/video/BV1Q4MkzVEpU?share%5Fsource=copy%5Fweb)



---

# 使用教程

## 高级参数：YOLO 模式

对于批量处理任务，可以使用 `--dangerously-skip-permissions` 参数：

```bash
claude --dangerously-skip-permissions
```

**安全的 YOLO 模式** | 绕过所有权限检查，让 Claude 不受干扰地工作直到完成，而不是监督 Claude。这对于修复 lint 错误或生成样板代码等工作流程非常有效。

⚠️ **使用场景建议**：

* 修复代码风格和 lint 错误
* 生成重复性样板代码
* 批量文件处理任务
* 已知安全的自动化操作

## 视频教程

* 原版claude code的使用教程，我们两个方案的一致使用

  [https://www.bilibili.com/video/BV1VkMTzjEhy?share%5Fsource=copy%5Fweb](https://www.bilibili.com/video/BV1VkMTzjEhy?share%5Fsource=copy%5Fweb)


## 更多资源

* 推荐关注推特的[宝玉老师](https://x.com/dotey)、[海拉鲁编程客](https://x.com/hylarucoder)获得更多claude code的实务经验
* 推荐两官文[Claude Code：代理编码的最佳实践](https://www.anthropic.com/engineering/claude-code-best-practices)、[Claude Code进行常见工作流程的分步教程](https://docs.anthropic.com/zh-CN/docs/claude-code/tutorials)
* [社区服务与支持](https://wiki.tu-zi.com/zh/group)：加入兔子AI活跃的用户社区，获取最新资讯、技术支持和使用技巧。

> 现在就开启你的 **Claude Code** 之旅，尽情发挥创意吧！🚀