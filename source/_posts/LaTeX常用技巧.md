---
title: LaTeX常用技巧
date: 2020-05-07 16:50:41
tags:
  - LaTeX
---

## 入门教程

[一份(不太)简短的 LaTeX 介绍](/download/lshort-zh-cn.pdf)

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

## 绘制流程图

```
% 引入tikz包
\usepackage{tikz}
% 加入形状箭头
\usetikzlibrary{shapes.geometric,arrows}
% 定义各类节点
\tikzstyle{startstop} = [rectangle,rounded corners, minimum width=1cm,minimum height=1cm,text centered, draw=black,fill=red!30]
\tikzstyle{io} = [trapezium, trapezium left angle = 70,trapezium right angle=110,minimum width=1cm,minimum height=1cm,text centered,draw=black,fill=blue!30]
\tikzstyle{process} = [rectangle,minimum width=1cm,minimum height=1cm,text centered,text width =3cm,draw=black,fill=orange!30]
\tikzstyle{decision} = [diamond,minimum width=1cm,minimum height=1cm,text centered,draw=black,fill=green!30]
\tikzstyle{arrow} = [thick,->,>=stealth]

% 绘制
\begin{figure}[H]
    \centering
    % 开始tikzpicture绘制环境
    % node distance为节点间默认距离
    \begin{tikzpicture}[node distance=2cm]
        % 定义各个节点及相对(或绝对)位置
        \node[startstop](S){S};
        \node[startstop,right of=S](E){E};
        \node[startstop,right of=E](I){I};
        \node[startstop,right of=I](D){D};
        \node[startstop,below of=I](R){R};
        % 开始连线
        \draw[arrow](S)--node[above]{$S\to E$}(E);
        \draw[arrow](E)--node[above]{$E\to I$}(I);
        \draw[arrow](I)--node[above]{}(D);
        % out, in 为绘制曲线的角度， 详见LaTeX教程
        \draw[arrow,out=-90,in=180](E) to node[left]{$E\to R$}(R);
        \draw[arrow,out=-120,in=120](I) to node[left]{$I\to R$}(R);
        \draw[arrow,out=60,in=-60](R) to node[right]{$R\to I$}(I);
    \end{tikzpicture}
    \caption{$SEIRD$模型流程图}
\end{figure}
```

效果如下
![SEIRD模型流程图](/images/LaTeX/SEIRD.png)
