# claudecode 无法连接到 Anthropic 服务

使用npm安装完claude之后。\n在命令行输入claude报了如下错误：

```bash
Unable to connect to Anthropic services
Failed to connect to api.anthropic.com: ERR BAD REQUEST
lease check your internet connection and network settings.
Note: Claude Code might not be available in your country, Check supported countries atnttps://anthropic.com/supported-countriesS E:ltoollclaude code>
```

 ![](https://wiki.tu-zi.com/api/files.get?sig=eyJhbGciOiJIUzI1NiIsInR5cCI6IkpXVCJ9.eyJrZXkiOiJ1cGxvYWRzLzA0MTA4NzY3LTk1YjgtNDYzMi05YWFmLTgwNzgwZjIwMmFkMi8wYzUwZDA4Zi1jN2ZjLTRjNzctOWNkYy1kMWM1OGViMDlmZTEvMzAyODY5Ny0yMDI1MDkyMTE1MTcwMjk1OS01NTQ0NDc2NjUuanBnIiwidHlwZSI6ImF0dGFjaG1lbnQiLCJpYXQiOjE3ODA0NTQ5NjMsImV4cCI6MTc4MDQ1ODU2M30.b7iFk597joxCGpFaPdrHedf1ozX0FEyXCQ6UqToddRE " =1878x518")

或

 ![](https://wiki.tu-zi.com/api/files.get?sig=eyJhbGciOiJIUzI1NiIsInR5cCI6IkpXVCJ9.eyJrZXkiOiJ1cGxvYWRzLzA0MTA4NzY3LTk1YjgtNDYzMi05YWFmLTgwNzgwZjIwMmFkMi9jZmQ1ZDg2Yi1kNTc5LTRkOGEtYWQ3Yi04MjNjZDhhODlhYTYvd2Vjb20tdGVtcC03NjAyMTYtNjE4MTYyYWQ2MTA3ZDZhMTlhN2U0YjE2Mjk4MTgyZDYucG5nIiwidHlwZSI6ImF0dGFjaG1lbnQiLCJpYXQiOjE3ODA0NTQ5NjMsImV4cCI6MTc4MDQ1ODU2M30.RiCwLte1oO8dYwapAKNEOFvlG-Qn8jNAlceEZHxEOgE " =1654x910")


可以在\~目录找到.claude.json，修改如下,在最后添加 "hasCompletedOnboarding": true

```bash
{
  "installMethod": "unknown",
  "autoUpdates": true,
  "firstStartTime": "2025-07-14T06:11:03.877Z",
  "userID": "f5afdd05117c901a4a5a0761d08230bfcbb76f9fd380ff7bc144cc12c52e55aa",
  "projects": {
    "/home/nassi": {
      "allowedTools": [],
      "history": [],
      "mcpContextUris": [],
      "mcpServers": {},
      "enabledMcpjsonServers": [],
      "disabledMcpjsonServers": [],
      "hasTrustDialogAccepted": false,
      "projectOnboardingSeenCount": 0,
      "hasClaudeMdExternalIncludesApproved": false,
      "hasClaudeMdExternalIncludesWarningShown": false
    }
  },  //这里要加逗号，注意英文的
  "hasCompletedOnboarding": true  // 新增字段放在这里，注意位置
}
```

本文来自博客园，作者：[GordonCC](https://www.cnblogs.com/gordonMlxg/)，转载请注明原文链接：<https://www.cnblogs.com/gordonMlxg/articles/19103691>