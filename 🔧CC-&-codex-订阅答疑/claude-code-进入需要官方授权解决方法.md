# claude code 进入需要官方授权解决方法

## 跳过官方验证

【.claude.json】路径：c盘/用户/用户名 路径下替换掉原来的，如果路径下有.claude.json.backup可以直接删了

```javascript
{
  "installMethod": "unknown",
  "cachedStatsigGates": {
    "tengu_log_1p_events": true,
    "tengu_disable_bypass_permissions_mode": false,
    "code_slack_app_install_banner": false,
    "tengu_tool_pear": false
  },
  "hasCompletedOnboarding": true
}
```


\
## 更改配置后需要新开cmd或者ide