---
title: LaTeX安装配置
date: 2020-04-15 12:38:22
tags:
  - LaTeX
  - VSCode
---

## LaTeX 环境安装

- Windows

  [官网](http://www.tug.org/texlive/) 下载安装

- Linux

  [官网](http://www.tug.org/texlive/) 可以下载，推荐 `apt` 安装

  `sudo apt install texlive-full`

## IDE 安装配置

### TexStudio

- 优点：安装方便，操作方便，免费， 跨平台

- 缺点：UI 丑陋，格式化不方便，中文支持差

- 安装

  - Windows

    [官网](https://www.texstudio.org/)

  - Linux

    `sudo apt install texstudio`

- 配置

  1. Options > Configure
  2. General > Language 选择语言
  3. Build 下调整编译设置(中文文档推荐 xelatex)

### VSCode

- 优点：安装简单，UI 漂亮，插件多，维护积极，开源免费，跨平台，中文友好

- 缺点：配置较为繁琐

- 安装

  [官网](https://code.visualstudio.com/Download)

- 配置

  1. 安装 latex workshop(提供良好的开发环境)

     `Ctrl`+`Shift`+`P` 搜索 `Latex workshop` 可以查看插件命令

  2. 安装 Latex Preview(文档预览，根据个人喜好选择)
  3. 设置中搜索 `latex workshop json` 加入如下内容( xelatex + bib 配置)
     ```
     // LaTeX
     // 从tab打开pdf预览
     "latex-workshop.view.pdf.viewer": "tab"
     // 保存自动编译
     // "latex-workshop.latex.autoBuild.run": "never",
     // 不显示警告(错误)气泡
     "latex-workshop.message.error.show": false,
     "latex-workshop.message.warning.show": false,
     "latex-workshop.latex.tools": [
        {
            // 编译工具和命令
            "name": "xelatex",
            "command": "xelatex",
            "args": [
                "-synctex=1",
                "-interaction=nonstopmode",
                "-file-line-error",
                "-pdf",
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
            "name": "xe->bib->xe->xe",
            "tools": [
                "xelatex",
                "bibtex",
                "xelatex",
                "xelatex"
            ]
        },
     ],
     // 自动清理无用的中间文件
     "latex-workshop.latex.autoClean.run": "onBuilt",
     "latex-workshop.latex.clean.fileTypes": [
        "*.aux",
        "*.bbl",
        "*.blg",
        "*.idx",
        "*.ind",
        "*.lof",
        "*.lot",
        "*.out",
        "*.toc",
        "*.acn",
        "*.acr",
        "*.alg",
        "*.glg",
        "*.glo",
        "*.gls",
        "*.ist",
        "*.fls",
        "*.log",
        "*.fdb_latexmk",
     ],
     ```
