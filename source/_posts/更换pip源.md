---
title: 更换pip源
date: 2020-05-12 16:08:27
tags:
  - Python
---

## 镜像

> 阿里云<https://mirrors.aliyun.com/pypi/simple/>  
> 中国科技大学<https://pypi.mirrors.ustc.edu.cn/simple/>  
> 豆瓣(douban) <http://pypi.douban.com/simple/>  
> 清华大学 <https://pypi.tuna.tsinghua.edu.cn/simple/>  
> 中国科学技术大学 <http://pypi.mirrors.ustc.edu.cn/simple/>

## 临时换源

`pip(3) install [something] -i [src]`

例如 pip3 使用 清华源 安装 numpy

`pip3 install numpy -i https://pypi.tuna.tsinghua.edu.cn/simple/`

## 永久换源

- Linux

  编辑 `~/.pip/pip.conf`

- Windows

  编辑 `C:\Users\user_name\pip\pip.ini`

```
[global]
index-url = https://mirrors.aliyun.com/pypi/simple/
```
