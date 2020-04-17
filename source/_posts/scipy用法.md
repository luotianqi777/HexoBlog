---
title: scipy用法
date: 2020-04-17 13:17:50
tags:
  - Python
  - Scipy
---

## 下载

`sudo apt install python(3)-scipy`

`pip(3) install scipy`

## 解微分方程

### `odeint()`函数

需要至少三个参数

- 微分方程函数
- 微分方程初值
- 微分自变量

### 用法

```
import numpy as np
from scipy.integrate import odeint

def diff(y, x):
  # dy/dx = x
	return np.array(x)
# x 范围
x = np.linspace(0, 10, 100)
# 设初值为0 此时y为一个数组，元素为不同x对应的y值
y = odeint(diff, 0, x)
# 也可以直接y = odeint(lambda y, x: x, 0, x)
```
