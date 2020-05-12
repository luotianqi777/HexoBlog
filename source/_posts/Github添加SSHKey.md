---
title: Github添加SSH Key
date: 2020-05-12 15:47:41
tags:
  - Git
---

## 安装 git

- 安装 git

  `sudo apt install git-core`

- 第一次使用要先设置 git 的用户名和邮箱

  `git config --global user.name 'your_name'`  
  `git config --global user.email 'your_email@example.com'`

## 注册 github 账户

- 注册 github 账户

## 添加 SSH 公匙

- 创建 SSH key

  `ssh-keygen -C "your_email@example.com"`

  接下来几次询问密码  
  建议连续回车  
  默认将 key 存到用户文件下`~/.ssh/`中

- 将`~/.ssh/id_rsa.pub`中的内容粘贴到 github 的 SSH key 中

- 可以通过下指令测试链接

  `ssh -T git@github.com`
