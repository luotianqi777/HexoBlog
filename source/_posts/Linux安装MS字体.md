---
title: Linux安装MS字体
date: 2020-05-10 22:49:22
tags:
  - Linux
---

## 说明

写论文时要求英文字体为`Times New Roman`和`Arial`，
Linux 系统并没有自带这些字体。

注意：Microsoft 已免费发布其核心字体，但**请注意 Minrosoft 字体是禁止使用在其他操作系统中**。
在任何 Linux 操作系统中安装 MS 字体之前请仔细阅读 EULA。

## 安装 MS 字体

`sudo apt install ttf-mscorefonts-installer`

会有较为良好的安装引导界面。
安装完成后更新字体缓存：

`sudo fc-cache -f -v`
