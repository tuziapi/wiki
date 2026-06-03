# ClaudeCode 官方版本配置教程

### 原版Claude Code+API调用详细步骤

#### 1 安装官方原版Claude Code

```bash
# 全局安装（更多用法见官方文档）
npm install -g @anthropic-ai/claude-code
```

> ⚠️ **如果已经安装过改版的需要卸载，可执行如下卸载：**
>
> ```bash
> npm uninstall -g @anthropic-ai/claude-code
> rm -rf ~/.claude*
> ```


> **安装claude 遇到问题**
>
> 点击下面链接
>
> **[claudecode 无法连接Anthropic 服务](https://wiki.tu-zi.com/s/8c61a536-7a59-4410-a5e2-8dab3d041958/doc/claudecode-anthropic-kBqvPtVURx)**
>
> 例如：
>
> \
>  ![](https://wiki.tu-zi.com/api/files.get?sig=eyJhbGciOiJIUzI1NiIsInR5cCI6IkpXVCJ9.eyJrZXkiOiJ1cGxvYWRzLzA0MTA4NzY3LTk1YjgtNDYzMi05YWFmLTgwNzgwZjIwMmFkMi9hZTM5NzZkNS00MzRjLTQ2ZWMtYTk1Yi1mNGUzYjJiOGM4NWYvd2Vjb20tdGVtcC03NjAyMTYtNjE4MTYyYWQ2MTA3ZDZhMTlhN2U0YjE2Mjk4MTgyZDYucG5nIiwidHlwZSI6ImF0dGFjaG1lbnQiLCJpYXQiOjE3ODA0NTQ5NjIsImV4cCI6MTc4MDQ1ODU2Mn0.G5GV63iJ-mfXotdBIxyl3iAAS5pM7PX0yxrXJGf-rfs " =1654x910")
>
> \

#### 2 获得API Key

使用gaccode账户登录后，在账户页面获得API Key。

**获取步骤：**


1. **注册账户** - 使用邀请链接注册gaccode账户
2. **登录账户** - 登录gaccode网站获取API Key
3. **配置使用** - 将API Key配置到环境变量中

#### B.3 配置环境变量

```bash
# 配置环境变量
export ANTHROPIC_API_TOKEN=""
export ANTHROPIC_API_KEY=你的gaccode_api_key

export ANTHROPIC_BASE_URL=https://gaccode.com/claudecode

# Windows CMD 中
# setx ANTHROPIC_API_KEY "你的gaccode_api_key"
# setx ANTHROPIC_BASE_URL "https://gaccode.com/claudecode"
```


 ![](https://wiki.tu-zi.com/api/files.get?sig=eyJhbGciOiJIUzI1NiIsInR5cCI6IkpXVCJ9.eyJrZXkiOiJ1cGxvYWRzLzA0MTA4NzY3LTk1YjgtNDYzMi05YWFmLTgwNzgwZjIwMmFkMi8yZGNiZmJkNy0xOGZiLTRjYzQtOGY2Mi02MGRlZjc3ZDVhZTMvaW1hZ2UucG5nIiwidHlwZSI6ImF0dGFjaG1lbnQiLCJpYXQiOjE3ODA0NTQ5NjIsImV4cCI6MTc4MDQ1ODU2Mn0._Uo2d8fdqI67hnmcdd567rHR-jYFy221ZugBYMIJZ6w " =824x136")

或更改文件`~/.claude/settings.json`

```bash
{ "env": 
  { "ANTHROPIC_BASE_URL": "https://gaccode.com/claudecode", 
    "ANTHROPIC_AUTH_TOKEN": "sk-xxx"
  } 
}
```

#### B.4 把 Anthropic API Key 的最后 20 位加入 `.claude.json` 中的 "approved" 列表，作为一个已允许的 key 标识

```bash
(cat ~/.claude.json 2>/dev/null || echo 'null') | jq --arg key "${ANTHROPIC_API_KEY: -20}" '(. // {}) | .customApiKeyResponses.approved |= ([.[]?, $key] | unique)' > ~/.claude.json.tmp && mv ~/.claude.json.tmp ~/.claude.json
```


 ![](https://wiki.tu-zi.com/api/files.get?sig=eyJhbGciOiJIUzI1NiIsInR5cCI6IkpXVCJ9.eyJrZXkiOiJ1cGxvYWRzLzA0MTA4NzY3LTk1YjgtNDYzMi05YWFmLTgwNzgwZjIwMmFkMi9kODM4Njk2NS01NmNmLTRiYWUtODRmZS05NDkyZWEzN2EwZGYvaW1hZ2UucG5nIiwidHlwZSI6ImF0dGFjaG1lbnQiLCJpYXQiOjE3ODA0NTQ5NjIsImV4cCI6MTc4MDQ1ODU2Mn0.G88T_xxwnBkSNLlDjeJ43PgMaCQUl4xyyS8xvSw2iG8 " =920x113")


#### B.5 启动与登录

```bash
# 进入项目目录
cd your-project-folder

# 启动 Claude Code

claude
```

> **说明：** 使用官方原版 + API Key 时，通常无需浏览器授权；若终端提示登录，请按指引完成。

B.5.1 选择主题


 ![](https://wiki.tu-zi.com/api/files.get?sig=eyJhbGciOiJIUzI1NiIsInR5cCI6IkpXVCJ9.eyJrZXkiOiJ1cGxvYWRzLzA0MTA4NzY3LTk1YjgtNDYzMi05YWFmLTgwNzgwZjIwMmFkMi81NDlkMjJmNS1iNGQwLTQyZmEtYTIxMi05NTA1YzY2ZWY0MTQvaW1hZ2UucG5nIiwidHlwZSI6ImF0dGFjaG1lbnQiLCJpYXQiOjE3ODA0NTQ5NjIsImV4cCI6MTc4MDQ1ODU2Mn0.7dtXMIrimB5OrFAjv9P-4Q9-VcDgyXPZ0x0LV6ZPBmU " =923x378")


B.5.2 直接按回车，表示已知悉


 ![](https://wiki.tu-zi.com/api/files.get?sig=eyJhbGciOiJIUzI1NiIsInR5cCI6IkpXVCJ9.eyJrZXkiOiJ1cGxvYWRzLzA0MTA4NzY3LTk1YjgtNDYzMi05YWFmLTgwNzgwZjIwMmFkMi84ZDRlZjM4Zi1kNTRkLTRmNDMtOTBmMC1mZmE0ZTJjNGQ3OTEvaW1hZ2UucG5nIiwidHlwZSI6ImF0dGFjaG1lbnQiLCJpYXQiOjE3ODA0NTQ5NjIsImV4cCI6MTc4MDQ1ODU2Mn0.vVnFj1WGOKslTSZPZM_5ppmJtk68K_BOSo_b8LK1VeM " =921x410")


B.5.3 选择 1 接受推荐设置


 ![](https://wiki.tu-zi.com/api/files.get?sig=eyJhbGciOiJIUzI1NiIsInR5cCI6IkpXVCJ9.eyJrZXkiOiJ1cGxvYWRzLzA0MTA4NzY3LTk1YjgtNDYzMi05YWFmLTgwNzgwZjIwMmFkMi9jNDQ3ZDE2OC1hMjc1LTQ2N2MtYjlmNi1kMDY1NzM1OWRhMmUv5LyB5Lia5b6u5L-h5oiq5Zu-Xzk5ZjA1ZWZiLTZhOGYtNGM3OS1hYzg3LTJjMGNjZTQwNmJiYS5wbmciLCJ0eXBlIjoiYXR0YWNobWVudCIsImlhdCI6MTc4MDQ1NDk2MiwiZXhwIjoxNzgwNDU4NTYyfQ.qbI53giJbyBGucTMWaHHYb6l1MdQMKZ0LrElTJwVK5Y " =918x413")


B.5.4 选择 yes，相信这个文件夹


 ![](https://wiki.tu-zi.com/api/files.get?sig=eyJhbGciOiJIUzI1NiIsInR5cCI6IkpXVCJ9.eyJrZXkiOiJ1cGxvYWRzLzA0MTA4NzY3LTk1YjgtNDYzMi05YWFmLTgwNzgwZjIwMmFkMi9mYTBhMTFjYS1hZWM4LTQwMGItYjNiYy00ZDNkZjYyMzUzNDEvaW1hZ2UucG5nIiwidHlwZSI6ImF0dGFjaG1lbnQiLCJpYXQiOjE3ODA0NTQ5NjIsImV4cCI6MTc4MDQ1ODU2Mn0.s3nUu-7D1MTlUGD33m-NjepmsUWsiAvfdlcRUc653x4 " =919x407")


B.5.5 开始对话


 ![](https://wiki.tu-zi.com/api/files.get?sig=eyJhbGciOiJIUzI1NiIsInR5cCI6IkpXVCJ9.eyJrZXkiOiJ1cGxvYWRzLzA0MTA4NzY3LTk1YjgtNDYzMi05YWFmLTgwNzgwZjIwMmFkMi84OWRlNTQyMS0xYTMzLTQ5NDctOWJiMy0xMTYzZTc2NWU1ZTAvaW1hZ2UucG5nIiwidHlwZSI6ImF0dGFjaG1lbnQiLCJpYXQiOjE3ODA0NTQ5NjIsImV4cCI6MTc4MDQ1ODU2Mn0.n2Z6dQGcUf4pni62vsUoYakOctQw80qLC5w5xvILJxY " =922x413")



---