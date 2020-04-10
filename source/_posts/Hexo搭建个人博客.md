---
title: Hexo 搭建个人博客
date: 2020-04-10 16:18:29
tags:
  - Linux
  - Hexo
---

- 安装 git
  > `sudo apt install git-core`
- 安装 nodejs, npm
  > 建议通过[官网](https://nodejs.org/en/)安装  
  > (如果通过 apt 安装`sudo apt install nodejs npm`有可能版本过低)  
  > 通过`ln -s [src] [obj]`将 nodejs 和 npm 软链接到`/usr/local/bin/`下
- 注册 github 账户并创建仓库, 添加 SSH 公匙
  > 略
- 安装 hexo
  > `npm install -g hexo-cli`
