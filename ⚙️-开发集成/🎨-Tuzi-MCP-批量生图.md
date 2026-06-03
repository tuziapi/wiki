# 🎨 Tuzi MCP 批量生图

# 使用tuzi-mcp批量生图

## 工具准备

* Chatgpt
* Claude Code
* Gemini 2.5 flash image generation api

以上工具均可从tuzi站获取。

## 步骤

### 1. 生成元提示词（meta prompt）

首先使用gpt 5 thinking生成提示词的meta prompt，也就是指导提示词如何产生的提示词。复制产生的文本存为guide.md。重点是提示词结构，产生英文的更好一些。

 ![](https://wiki.tu-zi.com/api/files.get?sig=eyJhbGciOiJIUzI1NiIsInR5cCI6IkpXVCJ9.eyJrZXkiOiJ1cGxvYWRzL2UxMjc0Y2E3LWNmZTEtNDdlOC04MjA0LTNhMDkzMTNlNzM4ZC8yM2Y3ZTViNi1lYzRlLTQ3YzMtOWRjNC01OGI5MjhmMTc4NDMvaW1hZ2UucG5nIiwidHlwZSI6ImF0dGFjaG1lbnQiLCJpYXQiOjE3ODA0NTQ5MDMsImV4cCI6MTc4MDQ1ODUwM30.EHXmkyXkNyYc0ehR_J5FUqQojXfikOUtrWur_syhKRU " =830x702")

### 2. 配置mcp.json

```json
{
  "mcpServers": {
    "tuzi-mcp": {
      "command": "uvx",
      "args": ["tuzi-mcp"],
      "env": {
        "TUZI_API_KEY": "你的tuzi api key，注意配置好gemini的分组"
      }
    }
  }
}
```

### 3. 启动Claude Code

```bash
claude --mcp-config mcp.json
```

输入 `/mcp`，可以看到tuzi-mcp已经被启用了，支持gemini图像生成。

 ![](https://wiki.tu-zi.com/api/files.get?sig=eyJhbGciOiJIUzI1NiIsInR5cCI6IkpXVCJ9.eyJrZXkiOiJ1cGxvYWRzL2UxMjc0Y2E3LWNmZTEtNDdlOC04MjA0LTNhMDkzMTNlNzM4ZC8xOGZhYTFjYi05OGU2LTRhOTEtYWZiYS0yYjAyNTU5YjE4MWIvaW1hZ2UucG5nIiwidHlwZSI6ImF0dGFjaG1lbnQiLCJpYXQiOjE3ODA0NTQ5MDMsImV4cCI6MTc4MDQ1ODUwM30.Jqw_-ZNTqSsOfN3xJxBdrLrt3pjVbM2NWTSWgc2H10s " =830x288")

### 4. 批量生成图片

使用如下提示词：

```
使用 @ref/IMG_6830.PNG 作为主角参考，生成9张高清照片，描述她的一天的生活，如起床、上班、锻炼、聚会等等，每张都有不同的场景和心情。参考 @guide.md 的提示词构成方法。文件存在images/
```

不到一分钟即可生成：

 ![](https://wiki.tu-zi.com/api/files.get?sig=eyJhbGciOiJIUzI1NiIsInR5cCI6IkpXVCJ9.eyJrZXkiOiJ1cGxvYWRzL2UxMjc0Y2E3LWNmZTEtNDdlOC04MjA0LTNhMDkzMTNlNzM4ZC8yYzM2ZWVhNS01Y2I0LTQ1OGYtYWMyNS1iOWQ4MzViMWE4OTgvaW1hZ2UucG5nIiwidHlwZSI6ImF0dGFjaG1lbnQiLCJpYXQiOjE3ODA0NTQ5MDMsImV4cCI6MTc4MDQ1ODUwM30.3Q4pwSnPl0i7sHdsFdKbeRqHh5PCwKMVH18rq7cYPi0 " =830x524")

查看下images/目录：

 ![](https://wiki.tu-zi.com/api/files.get?sig=eyJhbGciOiJIUzI1NiIsInR5cCI6IkpXVCJ9.eyJrZXkiOiJ1cGxvYWRzL2UxMjc0Y2E3LWNmZTEtNDdlOC04MjA0LTNhMDkzMTNlNzM4ZC9iOGViY2JiNy1jYzIwLTQ3NjAtOTUxOS0xZjQxNWFiNTNkNzEvaW1hZ2UucG5nIiwidHlwZSI6ImF0dGFjaG1lbnQiLCJpYXQiOjE3ODA0NTQ5MDMsImV4cCI6MTc4MDQ1ODUwM30.sTHIN30uYoab3nycWtDQA52JhFwrFER781pust-FAOg " =830x622")

 ![](https://wiki.tu-zi.com/api/files.get?sig=eyJhbGciOiJIUzI1NiIsInR5cCI6IkpXVCJ9.eyJrZXkiOiJ1cGxvYWRzL2UxMjc0Y2E3LWNmZTEtNDdlOC04MjA0LTNhMDkzMTNlNzM4ZC9iN2UyZWE4Ni01YzBlLTRjZGUtYThhZi1iMjkyYjQ2MWYzZjYvaW1hZ2UucG5nIiwidHlwZSI6ImF0dGFjaG1lbnQiLCJpYXQiOjE3ODA0NTQ5MDMsImV4cCI6MTc4MDQ1ODUwM30.lHabUuoLZUaUAqC4v72aYNkBu4kNpUAkmY_wx7JEomY " =829x829")