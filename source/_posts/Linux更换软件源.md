---
title: Linux更换软件源
date: 2020-05-12 16:19:27
tags:
  - Linux
---

## 查找所使用系统的清华源

在[清华源](https://mirrors.tuna.tsinghua.edu.cn/help/ubuntu/)选择系统版本

## 编辑文件 `/etc/apt/sources.list`

> 建议先将文件备份

将文件内容替换为所查内容

## 更新源

`sudo apt update`
