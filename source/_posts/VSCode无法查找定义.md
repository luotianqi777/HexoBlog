---
title: VSCode无法查找定义
date: 2020-06-17 10:32:26
tags:
- VSCode
- Java
- Maven
---

## VSCode查找定义失效
看openrasp源码时不能查找定义超恶心，一开始pom.xml报错应该是maven的问题，找了几个小时都找到合适的解决方案。
在java插件中把maven的更新啥的都去掉有可能避免这个问题，但会出现飘红，在找到合适的解决方案前忍忍吧。
记得重新导一下项目。
## 解决方案
插件设置中搜索Java Server Launch Mode，
模式改为LightWeight。