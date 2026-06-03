# Vscode  claude code 和 codex插件 配置

# claude code 插件

## 1.1 插件市场安装 **Claude Code for VS Code**

搜索 并下载 **Claude Code for VS Code** 

 ![](https://wiki.tu-zi.com/api/files.get?sig=eyJhbGciOiJIUzI1NiIsInR5cCI6IkpXVCJ9.eyJrZXkiOiJ1cGxvYWRzL2I3MTgwNDFlLWUwNjItNDRlMy1iNTljLTlkYzliNjNjODczMi8zNDM2NmNkMi1iMmVkLTQwZWMtYWRmZC0yZDYxYzA0ODg4NzYvaW1hZ2UucG5nIiwidHlwZSI6ImF0dGFjaG1lbnQiLCJpYXQiOjE3ODA0NTQ4NTcsImV4cCI6MTc4MDQ1ODQ1N30.khgbnwmBZcH6IoYGRP_E4czjAr9qufQ5mmSWTYTAnWs " =1047x366")

## 1.2 配置 ～/.claude/config.json

```javascript
{ 

"primaryApiKey": "api" 

}
```


## 1.3 配置 ～/.claude/settings.json

### 1.3.1 配置兔子api 站点

```none
 "env": {
    "ANTHROPIC_API_KEY": "sk-****",
    "ANTHROPIC_BASE_URL": "https://api.tu-zi.com"
  }
```

### 1.3.2 配置 gac 订阅

```javascript
  "env": {
    "ANTHROPIC_API_KEY": "sk-ant-****",
    "ANTHROPIC_BASE_URL": "https://gaccode.com/claudecode"
  }
```


**例如:**

 ![](https://wiki.tu-zi.com/api/files.get?sig=eyJhbGciOiJIUzI1NiIsInR5cCI6IkpXVCJ9.eyJrZXkiOiJ1cGxvYWRzL2I3MTgwNDFlLWUwNjItNDRlMy1iNTljLTlkYzliNjNjODczMi82MWVjNjcxMS0zOGJhLTQ3OTEtYjViZC03ZjAzNmIxYWU0N2IvaW1hZ2UucG5nIiwidHlwZSI6ImF0dGFjaG1lbnQiLCJpYXQiOjE3ODA0NTQ4NTcsImV4cCI6MTc4MDQ1ODQ1N30.NmAp1HWpuLEbi2m5-23DRF0_Q2bqFyabeO4-Z5wAANQ " =734x379")


保存后即可使用 claude插件

 ![](https://wiki.tu-zi.com/api/files.get?sig=eyJhbGciOiJIUzI1NiIsInR5cCI6IkpXVCJ9.eyJrZXkiOiJ1cGxvYWRzL2I3MTgwNDFlLWUwNjItNDRlMy1iNTljLTlkYzliNjNjODczMi82ZWYzZmRiMi02YWMwLTQ4YjYtYmY0My1kNTMxOTc1NTU4MjYvaW1hZ2UucG5nIiwidHlwZSI6ImF0dGFjaG1lbnQiLCJpYXQiOjE3ODA0NTQ4NTcsImV4cCI6MTc4MDQ1ODQ1N30.lo1HCM2CJC2u8lupV2IRL6y2lCU-M3-3bv2nexA4QkY " =1456x696")

# codex 插件

## 2.1 插件市场安装 **Codex – OpenAI's coding agent**

 ![](https://wiki.tu-zi.com/api/files.get?sig=eyJhbGciOiJIUzI1NiIsInR5cCI6IkpXVCJ9.eyJrZXkiOiJ1cGxvYWRzL2I3MTgwNDFlLWUwNjItNDRlMy1iNTljLTlkYzliNjNjODczMi9hODBjYWExYi00M2E5LTQ2MmMtODUyZi1lNTY0YWY2M2JhODIvaW1hZ2UucG5nIiwidHlwZSI6ImF0dGFjaG1lbnQiLCJpYXQiOjE3ODA0NTQ4NTcsImV4cCI6MTc4MDQ1ODQ1N30.k6J5Uq7SK4sWoBas3HHWaPdiRoGEAK5mMfnEmnEFDFw " =1151x474")

## 2.2 进入 ～/.codex/config.toml  配置

 ![](https://wiki.tu-zi.com/api/files.get?sig=eyJhbGciOiJIUzI1NiIsInR5cCI6IkpXVCJ9.eyJrZXkiOiJ1cGxvYWRzL2I3MTgwNDFlLWUwNjItNDRlMy1iNTljLTlkYzliNjNjODczMi8xYTkwZmI4OC00YzYwLTQ4ZGItYTBkYy01MzZjOGI0NzQ1N2YvaW1hZ2UucG5nIiwidHlwZSI6ImF0dGFjaG1lbnQiLCJpYXQiOjE3ODA0NTQ4NTcsImV4cCI6MTc4MDQ1ODQ1N30.MPtvUCnuJHw2olXYX1IIRpyKKuT00B_WwkV9aB8wIEk " =1029x471")


```javascript
# 核心设置
model = "gpt-5.5"
model_provider = "tuzi"  # 服务提供商
model_reasoning_effort = "high"
disable_response_storage = true

[model_providers.tuzi]
name = "tuzi"
#  gac 订阅   base URL地址 https://gaccode.com/codex/v1
#  兔子api平台 base URL地址 https://api.tu-zi.com
#  codex粉色订阅 base URL地址 https://api.tu-zi.com/coding
# 例如
base_url = "https://gaccode.com/codex/v1"
env_key = "CODEX_API_KEY"    
wire_api = "responses"
```


 ![](https://wiki.tu-zi.com/api/files.get?sig=eyJhbGciOiJIUzI1NiIsInR5cCI6IkpXVCJ9.eyJrZXkiOiJ1cGxvYWRzL2I3MTgwNDFlLWUwNjItNDRlMy1iNTljLTlkYzliNjNjODczMi8zYWNmNzc5MS03ODAzLTQwN2MtYjFkZi1lNjIyMThkOTZjNGEvaW1hZ2UucG5nIiwidHlwZSI6ImF0dGFjaG1lbnQiLCJpYXQiOjE3ODA0NTQ4NTcsImV4cCI6MTc4MDQ1ODQ1N30.tY9fXYE4haQKZvSfjw8Wf3KDtlxRmjJXL-zr1twOZO4 " =903x274")


## 2.3 创建auth.json 文件

```javascript
nano ~/.codex/auth.json   #创建auth.json 文件
```

**auth.json 配置模板**

```bash
{
  "OPENAI_API_KEY" null  # 填 null 就可以了
}
```

**环境配置管理**

```bash
# mac/linux 方法
# ~/.bashrc 或 ~/.zshrc
echo 'export CODEX_API_KEY=sk-MP***' >> ~/.bashrc # 配置兔子api key

#  重新加载环境
source ~/.bashrc
```

```bash
# windonws方法
setx CODEX_API_KEY "sk-*****" 
echo %CODEX_API_KEY%  #然后 关闭这个命令窗口，再重新打开一个，就生效了。验证一下
```