---
title: eclipse配置Tomcat环境
date: 2020-05-31 18:08:54
tags:
- Java
- Linux
- Eclipse
- Tomcat
---

## 下载Tomcat

[官方地址](https://tomcat.apache.org/)

## 将Tomcat解压到一个位置
## 配置Eclipse
- `Window`
- Preferences
- Server
- Runtime Environment
- Add
- 选择服务器
- 选择JRE
## 建议使用托管模式
- 双击Servers中的服务器
- Server Locations选择第二个选项(use Tomcat installation)
    > 如果不能选择试试删掉当前Server并重新添加Server  
    > 注意先不要把项目添加到Server  
    > 等设置好托管模式后再添加项目