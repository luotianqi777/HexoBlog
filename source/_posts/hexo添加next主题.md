---
title: hexo添加next主题
date: 2020-04-11 19:31:37
tags:
  - Hexo
---

## 进入 blog 目录

> `cd blog_folder`

## 下载 Next 主题

> `git clone https://github.com/iissnan/hexo-theme-next themes/next`

## 修改`/_config.yml`

- 修改主题
  ```
  theme: next
  ```
- 修改站点信息
  ```
  title:
  subtitle:
  description:
  author: author
  language: zh-Hans (next主题的简体中文为zh-Hans)
  timezone: Asia/Shanghai
  ```

## 修改`/theme/next/_config.yml`

- 选择风格

  搜索 `scheme`，去掉所选风格前的注释

  ```
  #scheme: Muse
  #scheme: Mist
  scheme: Pisces
  #scheme: Gemini
  ```

- 设置菜单项及所对应的文件目录

  搜索 `menu` ，通过注释菜单项来开启或关闭菜单项

  ```
  menu:
    home: /|| home
    #about: /about/|| user
    tags: /tags/|| tags
    #categories: /categories/|| th
    #archives: /archives/|| archive # 归档显示错误注释此行
    #schedule: /schedule/|| calendar
    #sitemap: /sitemap.xml|| sitemap
    #commonweal: /404/|| heartbeat
  ```

  ||后面的图标  
  图标必须为 [FontAwesome](https://fontawesome.com/) 网站中存在的图标的名字

- 创建菜单项对应文件目录，以`tags`为例

  > `hexo n page tags`

  编辑`/source/tags/index.md`，`type`属性的值写为`tags`

  ```
  ---
  title: tags
  date: 2020-04-10 17:40:53
  type: "tags"
  ---
  ```

  - 在新创建的文章中加入 tag

    ```
    ---
    title: new_file
    date: 2020-04-11 19:55:31
    tags:
      - tag_1
      - tag_2
    ---
    ```

- 添加头像

  搜索 `Avatar`，可以用图片链接或本地图片(本地图片需要放在`/source/images/`下)

  ```
  # avatar: http://example.com/avatar.png
  avatar: /images/avatar.jpg
  ```

- 显示浏览进度

  搜索 `scrollpercent`，值改为`true`

  ```
  scrollpercent: true
  ```

- 侧边栏社交链接

  搜索 `social`

  ```
  social:
    GitHub: https://github.com/luotianqi777 || github
    E-Mail: mailto:luotianqi777@gmail.com || envelope
  ```

  ||后为图标，图标必须为 [FontAwesome](https://fontawesome.com/) 网站中存在的图标的名字
