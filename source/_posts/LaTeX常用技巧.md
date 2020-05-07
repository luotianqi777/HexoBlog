---
title: LaTeX常用技巧
date: 2020-05-07 16:50:41
tags:
  - LaTeX
---

## 插入代码

```
% 代码环境
\usepackage{listings}
\usepackage{xcolor}
% 代码格式设置
\lstset{
    % 语言
    language=python,
    % 自动换行
    breaklines=true,
    % 行号
    numbers=left,
    % 基础字体设置
    basicstyle=\footnotesize,
    % 行号风格
    numberstyle=\tiny,
    % 字符串风格
    stringstyle=\color{orange},
    % 注释风格
    commentstyle=\color{gray},
    % 关键字风格
    keywordstyle=\color{blue},
    % 左侧margin
    xleftmargin = 25pt,
    % 添加frame
    frame = tb,
    % 设置frame左侧margin
    framexleftmargin = 20pt,
}
% 引用代码
\lstinputlisting{filepath}
```
