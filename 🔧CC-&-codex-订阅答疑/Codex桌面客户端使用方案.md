# Codex桌面客户端使用方案

1. 下载Codex桌面版，未配置成功时打开见到如下登陆页：

   ![](https://wiki.tu-zi.com/api/files.get?sig=eyJhbGciOiJIUzI1NiIsInR5cCI6IkpXVCJ9.eyJrZXkiOiJ1cGxvYWRzLzA0MTA4NzY3LTk1YjgtNDYzMi05YWFmLTgwNzgwZjIwMmFkMi9lYjY2NTNkNC0wOTAyLTQxZmQtOGRmMC0yYWIyNGQ5NmQwYzAvaW1hZ2UucG5nIiwidHlwZSI6ImF0dGFjaG1lbnQiLCJpYXQiOjE3ODA0NTQ5NjEsImV4cCI6MTc4MDQ1ODU2MX0.5rKZwAvmWjAkn9_hD4XY-F1lx5CNGZDd65vLqQaVhw4 " =407x401")
2. 配置环境变量，在 Shell 中导入从 gaccode 获取的 API Key  或 api.tu-zi.com 获取的 API Key ：

   ```bash
   # 到此页面获取 API Key
   # https://gaccode.com/api-keys
   # https://api.tu-zi.com/token
   # https://coding.tu-zi.com 购买时自动发送的
   
   echo 'export CODEX_API_KEY="你的Key字符串"' 
   
   ```


那么开始我们的配置，1. 关闭Codex桌面端，2.进入.codex文件夹（如果没有则在 ～ 目录下创建）

 ![](https://wiki.tu-zi.com/api/files.get?sig=eyJhbGciOiJIUzI1NiIsInR5cCI6IkpXVCJ9.eyJrZXkiOiJ1cGxvYWRzLzA0MTA4NzY3LTk1YjgtNDYzMi05YWFmLTgwNzgwZjIwMmFkMi9jMTE1YTg4ZS01MjY4LTQzY2YtOTBmNC1kNzkzMzcyNDZhMDcvaW1hZ2UucG5nIiwidHlwZSI6ImF0dGFjaG1lbnQiLCJpYXQiOjE3ODA0NTQ5NjEsImV4cCI6MTc4MDQ1ODU2MX0.GDcPN3KlxihFlezJFjlALoWy8OsH-OfNZrwKYnimKxI " =859x560")\n3. 创建config.toml文件\n ![](https://wiki.tu-zi.com/api/files.get?sig=eyJhbGciOiJIUzI1NiIsInR5cCI6IkpXVCJ9.eyJrZXkiOiJ1cGxvYWRzLzA0MTA4NzY3LTk1YjgtNDYzMi05YWFmLTgwNzgwZjIwMmFkMi9mYmU5YzAzNy0yMzIxLTQ3YjEtYWY1OS02YWE1OWQ0OTYxNGQvaW1hZ2UucG5nIiwidHlwZSI6ImF0dGFjaG1lbnQiLCJpYXQiOjE3ODA0NTQ5NjEsImV4cCI6MTc4MDQ1ODU2MX0.Ivn3snwEIN6ftX9ENNG_SD5IUjRmMQmH32ZNIbSJzNQ " =543x478")


4. 打开填写内容

   ```bash
   profile = "gac"
   
   [model_providers.gac]
   name = "gac"
   base_url = "https://gaccode.com/codex/v1" 或 "https://api.tu-zi.com" 或 "https://coding.tu-zi.com"
   wire_api = "responses"
   env_key = "CODEX_API_KEY"
   
   [profiles.gac]
   model_provider = "gac" 或 "tuzi" 或 "Coding"
   model = "gpt-5.4"
   model_reasoning_effort = "high"
   approval_policy = "on-request"
   
   
   
   
   ```

   \
   \
5. 重启codex，即可开始对话

 ![](https://wiki.tu-zi.com/api/files.get?sig=eyJhbGciOiJIUzI1NiIsInR5cCI6IkpXVCJ9.eyJrZXkiOiJ1cGxvYWRzLzA0MTA4NzY3LTk1YjgtNDYzMi05YWFmLTgwNzgwZjIwMmFkMi9iYzA5OWM5Ny1kMTRkLTRiNGMtODNkZS00NTcwNDM3Zjc2YmUvaW1hZ2UucG5nIiwidHlwZSI6ImF0dGFjaG1lbnQiLCJpYXQiOjE3ODA0NTQ5NjEsImV4cCI6MTc4MDQ1ODU2MX0.4SCeM9ZYEjCm6tVH6CKrbhbU425enuc_QQJ-N6mhBJU " =788x590")


\