---
title: Linux屏蔽崩溃日志
date: 2020-05-23 19:02:43
tags:
- Linux
---

## 临时关闭
`sudo service apport stop`
在重启后失效
## 永久关闭
编辑`/etc/default/apport`
修改
```
enabled=0
```
重启生效
