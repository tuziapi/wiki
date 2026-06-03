# codex 线路问题

## 1.「改版codex」切换线路

### 1.1 执行命令（如执行这步报错跳转到1.4查看）

```bash
codex --pick-relay
```

 ![](https://wiki.tu-zi.com/api/files.get?sig=eyJhbGciOiJIUzI1NiIsInR5cCI6IkpXVCJ9.eyJrZXkiOiJ1cGxvYWRzLzA0MTA4NzY3LTk1YjgtNDYzMi05YWFmLTgwNzgwZjIwMmFkMi8xNTZjMGE1ZS1hMTY4LTQ4NGQtYTAyYi1kNTNhODIxNjI5MTEvaW1hZ2UucG5nIiwidHlwZSI6ImF0dGFjaG1lbnQiLCJpYXQiOjE3ODA0NTQ5NjUsImV4cCI6MTc4MDQ1ODU2NX0.6dP7KDyh8xxlUb0CSM4pcaADDZn91GCkCVAYr6SE--E " =514x207")

### 1.2 选择一个线路（建议选延迟低且非ip地址的）

 ![](https://wiki.tu-zi.com/api/files.get?sig=eyJhbGciOiJIUzI1NiIsInR5cCI6IkpXVCJ9.eyJrZXkiOiJ1cGxvYWRzLzA0MTA4NzY3LTk1YjgtNDYzMi05YWFmLTgwNzgwZjIwMmFkMi83ZDQwZjc0My00Y2I4LTRlNTItYTg4MS05N2FhNjM5ZTliZGYvaW1hZ2UucG5nIiwidHlwZSI6ImF0dGFjaG1lbnQiLCJpYXQiOjE3ODA0NTQ5NjUsImV4cCI6MTc4MDQ1ODU2NX0.XDnNhMssLYyXcoJse1Rj9ZuYquElJk2CIX9C_tRomuU " =942x636")

### 1.3 执行codex后提问测试结果

 ![](https://wiki.tu-zi.com/api/files.get?sig=eyJhbGciOiJIUzI1NiIsInR5cCI6IkpXVCJ9.eyJrZXkiOiJ1cGxvYWRzLzA0MTA4NzY3LTk1YjgtNDYzMi05YWFmLTgwNzgwZjIwMmFkMi9hZDRmZjNiOS0yMGEwLTRkZTctODQ3MS00MmYwM2QyM2Q2ZDYvaW1hZ2UucG5nIiwidHlwZSI6ImF0dGFjaG1lbnQiLCJpYXQiOjE3ODA0NTQ5NjUsImV4cCI6MTc4MDQ1ODU2NX0.mC2IJhT6T57fXDG60Frh_VH3pSsrJDO7RHqKYw_kTCo " =752x605")

### 1.4 手动直接配置线路

codex 配置api优化线路： 

```bash
ping gaccode.com
ping relay01.gaccode.com
ping relay05.gaccode.com
ping relay08.gaccode.com
ping relay11.gaccode.com
```

如果是授权登录的就ping完后  选个延时小的，假设relay01延时小，就运行codex --pick-relay [relay01.gaccode.com](http://relay01.gaccode.com)

## 2.「官方 codex」切换线路

codex 配置api优化线路： 

```bash
ping gaccode.com
ping relay01.gaccode.com
ping relay05.gaccode.com
ping relay08.gaccode.com
ping relay11.gaccode.com
```

ping完选个延时小的，替换在config.toml里的url里

譬如relay01延时最小，就把c盘/用户/用户名/.codex/config.toml文件里url那里的gaccode.com变成relay01.gaccode.com