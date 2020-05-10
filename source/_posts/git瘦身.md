---
title: git瘦身
date: 2020-05-11 00:48:03
tags:
  - Git
---

## 前言

Git 仓库一不注意就变得十分臃肿，很多不想跟踪的文件都留在历史记录里没有删除。

原地址 <https://www.jianshu.com/p/fe3023bdc825>

## 查找占用空间最大的文件

`git rev-list --objects --all | grep "$(git verify-pack -v .git/objects/pack/*.idx | sort -k 3 -n | tail -5 | awk '{print$1}')"`

## 从 git 中移除

big_file_name 为要移除的文件
`git filter-branch --force --index-filter 'git rm -rf --cached --ignore-unmatch big_file_name' --prune-empty --tag-name-filter cat -- --all`

## 真正删除

`rm -rf .git/refs/original/`

`git reflog expire --expire=now --all`

`git gc --prune=now`

`git gc --aggressive --prune=now`

## 提交到远程

`git push origin master --force`

`git remote prune origin`
