---
title: LaTeX常见问题
date: 2020-05-07 16:50:51
tags:
  - LaTeX
---

## 警告：Font shape `OT1/cmss/m/n' in size <4> not available

    \usepackage{lmodern}

或者

    \usepackage{anyfontsize}

## 警告：引用未标号

> bibtex 编译后再进行**两次** xelatex 编译

## 错误：There's no line here to end

错误的使用换行符

> <https://www.overleaf.com/learn/latex/Errors/LaTeX_Error:_There%27s_no_line_here_to_end>

## 警告：Underfull(Overfull) \hbox message

> underfull 是说该处排版内容太稀疏了（badness 10000)是 TeX 衡量排版效果好不好的一个尺度  
> Overfull 则是说该处内容太多，超出了设定的印刷范围，这多数是由于系统无法找到合适的自动换行点造成的
