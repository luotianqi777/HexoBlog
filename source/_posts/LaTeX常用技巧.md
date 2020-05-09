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
% 颜色
\usepackage{xcolor}
% 字体
\usepackage{fontspec}
% 代码格式设置
\lstset{
    % 语言
    language=python,
    % 自动换行
    breaklines=true,
    % 行号
    numbers=left,
    % 字符串显示空格
    showstringspaces=false,
    % 基础字体设置
    basicstyle=\footnotesize\fontspec{Ubuntu Mono},
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

## 图表公式章节编号

```
% 重定义表编号格式
\renewcommand{\thetable}{\thesection-\arabic{table}}
% 重定义图编号格式
\renewcommand{\thefigure}{\thesection-\arabic{figure}}
% 重定义公式编号格式
\renewcommand{\theequation}{\thesection.\arabic{equation}}
\makeatletter
% section计数器增加时重置table计数器
\@addtoreset{table}{section}
% section计数器增加时重置figure计数器
\@addtoreset{figure}{section}
% section计数器增加时重置equation计数器
\@addtoreset{equation}{section}
\makeatother
```

## 中英文摘要

```
% 英文摘要
\newenvironment{enabstract}{
    \par\small
    \noindent\mbox{}\hfill{\bfseries Abstract}\hfill\mbox{}\par
    \vskip 2.5ex}{\par\vskip 2.5ex}
% 中文摘要
\newenvironment{cnabstract}{
    \par\small
    \noindent\mbox{}\hfill{\bfseries 摘要}\hfill\mbox{}\par
    \vskip 2.5ex}{\par\vskip 2.5ex}
```
