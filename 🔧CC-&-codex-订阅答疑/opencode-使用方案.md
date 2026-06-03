# opencode 使用方案

# cluadecode

GAC已经支持并适配 OpenCode  ,使用方法是

## 1.\~/.config/opencode/opencode.json

 填写我们的接入点，比如 


1. { "$schema": "<https://opencode.ai/config.json>", "provider": { "anthropic": { "options": { "baseURL": "<https://relay01.gaccode.com/claudecode/v1>" } } } }

   \
   ### gac订阅 配置

   \
   ```javascript
   { 
     "$schema": "https://opencode.ai/config.json", 
     "provider": { 
       "anthropic": { 
         "options": { 
           "baseURL": "https://relay01.gaccode.com/claudecode/v1" 
         } 
       } 
     } 
   }
   ```

   ### 兔子api 接入 配置

   \
   ```javascript
   { 
     "$schema": "https://opencode.ai/config.json", 
     "provider": { 
       "anthropic": { 
         "options": { 
           "baseURL": "https://api.tu-zi.com/v1" 
         } 
       } 
     } 
   }
   ```

## \n2. 获取key

### gac订阅 获取方法 

**<https://gaccode.com/api-keys> 生成一个秘钥** 


### 兔子api  获取方法


<https://api.tu-zi.com/panel>  → 令牌管理 → 生成一个 密钥 (注意: 配置  cluadecode 分组 或者 原价分组)

## 3. OpenCode选择连接Anthropic，选择手动输入API Key，使用上一步生成的秘钥,codex也是类似的操作步骤

### 3.1 进入 opencode → 输入 /connect

 ![](https://wiki.tu-zi.com/api/files.get?sig=eyJhbGciOiJIUzI1NiIsInR5cCI6IkpXVCJ9.eyJrZXkiOiJ1cGxvYWRzL2I3MTgwNDFlLWUwNjItNDRlMy1iNTljLTlkYzliNjNjODczMi8zYmMzY2U3MC01ZWI0LTQ4ZWYtOThiYi1hYWIyNzk3YmUzZDUvaW1hZ2UucG5nIiwidHlwZSI6ImF0dGFjaG1lbnQiLCJpYXQiOjE3ODA0NTQ5NTEsImV4cCI6MTc4MDQ1ODU1MX0.2EzlpZ_qYHqsxhcm_E1j3sCIKduIH62sZWXqk9jKUrE " =588x310")

### 3.2 选择模型厂商  → Manually enter API Key

 ![](https://wiki.tu-zi.com/api/files.get?sig=eyJhbGciOiJIUzI1NiIsInR5cCI6IkpXVCJ9.eyJrZXkiOiJ1cGxvYWRzL2I3MTgwNDFlLWUwNjItNDRlMy1iNTljLTlkYzliNjNjODczMi81N2Q5ZDVhNy02ZGVmLTQ2MDQtYTYzNi1hYWY3ZDk5MThmYTgvaW1hZ2UucG5nIiwidHlwZSI6ImF0dGFjaG1lbnQiLCJpYXQiOjE3ODA0NTQ5NTEsImV4cCI6MTc4MDQ1ODU1MX0.vn0MZy-0O7sIMGoeawMicIK-GTicsVrZzIrHGHQ6fQQ " =554x353")


 ![](https://wiki.tu-zi.com/api/files.get?sig=eyJhbGciOiJIUzI1NiIsInR5cCI6IkpXVCJ9.eyJrZXkiOiJ1cGxvYWRzL2I3MTgwNDFlLWUwNjItNDRlMy1iNTljLTlkYzliNjNjODczMi8xMDg0MGU2Zi1lZjg4LTRlZmUtYjgwNC0xZjkzOWYyMzA0YWEvaW1hZ2UucG5nIiwidHlwZSI6ImF0dGFjaG1lbnQiLCJpYXQiOjE3ODA0NTQ5NTEsImV4cCI6MTc4MDQ1ODU1MX0.iEmi5GKb9BM4jItS9sqUK8LkBy5FIqUOyx9Of9bSbUI " =590x180")


 ![](https://wiki.tu-zi.com/api/files.get?sig=eyJhbGciOiJIUzI1NiIsInR5cCI6IkpXVCJ9.eyJrZXkiOiJ1cGxvYWRzL2I3MTgwNDFlLWUwNjItNDRlMy1iNTljLTlkYzliNjNjODczMi9iMzg0NjJmZi03OTc0LTRlZmYtYTEzZC1lMDAxNjhhZTBkNzgvaW1hZ2UucG5nIiwidHlwZSI6ImF0dGFjaG1lbnQiLCJpYXQiOjE3ODA0NTQ5NTEsImV4cCI6MTc4MDQ1ODU1MX0.IcAIChLBrJVKIyPE_o2ufMFAGKOLpMp7zUQ8nlhbSYY " =561x224")

完成

##  ![](https://wiki.tu-zi.com/api/files.get?sig=eyJhbGciOiJIUzI1NiIsInR5cCI6IkpXVCJ9.eyJrZXkiOiJ1cGxvYWRzL2I3MTgwNDFlLWUwNjItNDRlMy1iNTljLTlkYzliNjNjODczMi9mMGZlNzE2Zi0yYTZmLTQ0Y2YtODA1YS1kMGFhNjFlZmJkNDQvd2Vjb20tdGVtcC0zOTI0Mi1lODZlMTJjNGEzODE3Njc4NDdhNmM2NjljNGIyOTdhOC5qcGciLCJ0eXBlIjoiYXR0YWNobWVudCIsImlhdCI6MTc4MDQ1NDk1MSwiZXhwIjoxNzgwNDU4NTUxfQ.oTeMHL-ahkkgRX3JXDsoYbGHE_WeH39HoQ87V3d5ANE "left-50 =799x661")

# codex


### gac 订阅 配置

```javascript
{ 
  "$schema": "https://opencode.ai/config.json", 
  "provider": { 
    "openai": { 
      "options": { 
        "baseURL": "https://relay01.gaccode.com/codex/v2" 
      },
      "models": {
        "gpt-5-codex": {
          "options": {
            "store": false
          }
        },
        "gpt-5.2": {
          "options": {
            "store": false
          }
        }
      }    
    } 
  } 
}
```


### 兔子api 配置

```javascript
{ 
  "$schema": "https://opencode.ai/config.json", 
  "provider": { 
    "openai": { 
      "options": { 
        "baseURL": "https://api.tu-zi.com/v1" 
      } ,
      "models": {
        "gpt-5-codex": {
          "options": {
            "store": false
          }
        },
        "gpt-5.2": {
          "options": {
            "store": false
          }
        }
      }    
    } 
  } 
}
```