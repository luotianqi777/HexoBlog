---
title: git合并分支强行覆盖当前分支
date: 2020-04-10 23:31:17
tags:
  - git
---

- 将 dev 分支传到远程
  > `git push -u origin dev`
- 切换到本地 master 分支
  > `git checkout master`
- 将本地 master 分支重置为 dev
  > `git reset --hard dev`
- 将重置后的 master 分支强制推送更新
  > `git push origin master --force`

> 这个方法重点在于用 reset 将 master 分支直接指向 dev
