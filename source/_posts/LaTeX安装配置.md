---
title: LaTeX安装配置
date: 2020-04-15 12:38:22
tags:
  - LaTeX
---

## LaTeX 环境安装

- Windows

  [官网](http://www.tug.org/texlive/) 下载安装映像

- Linux

  `sudo apt install texlive`

## LaTeX 使用

[一份(不太)简短的 LaTeX 介绍](/download/lshort-zh-cn.pdf)

## IDE 配置

- TexStudio
  - Options > Configure
  - General > Language 选择语言
  - Build 下调整编译设置(中文文档推荐 xelatex)
- VSCode

  1. 安装 latex workshop(提供良好的开发环境)

     `Ctrl`+`Shift`+`P` 搜索 `Latex workshop` 可以查看插件命令

  2. 安装 Latex Preview(文档预览，根据个人喜好选择)
  3. 设置中搜索 `latex workshop json` 加入如下内容
     ```
     // LaTeX
     // 保存自动编译
     // "latex-workshop.latex.autoBuild.run": "never",
     // 不显示警告(错误)气泡
     "latex-workshop.message.error.show": false,
     "latex-workshop.message.warning.show": false,
     "latex-workshop.latex.tools": [
         {
             "name": "xelatex",
             "command": "xelatex",
             "args": [
                 "-synctex=1",
                 "-interaction=nonstopmode",
                 "-file-line-error",
                 "%DOCFILE%"
             ]
         },
         {
             "name": "pdflatex",
             "command": "pdflatex",
             "args": [
                 "-synctex=1",
                 "-interaction=nonstopmode",
                 "-file-line-error",
                 "%DOCFILE%"
             ]
         },
         {
             "name": "bibtex",
             "command": "bibtex",
             "args": [
                 "%DOCFILE%"
             ]
         }
     ],
     "latex-workshop.latex.recipes": [
         {
             "name": "xelatex",
             "tools": [
                 "xelatex"
             ],
         },
         {
             "name": "pdflatex",
             "tools": [
                 "pdflatex"
             ]
         },
         {
             "name": "xe->bib->xe->xe",
             "tools": [
                 "xelatex",
                 "bibtex",
                 "xelatex",
                 "xelatex"
             ]
         },
         {
             "name": "pdf->bib->pdf->pdf",
             "tools": [
                 "pdflatex",
                 "bibtex",
                 "pdflatex",
                 "pdflatex"
             ]
         }
     ],
     ```
