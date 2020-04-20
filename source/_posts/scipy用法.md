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

以 SIR 模型为例

```
import numpy as np
import pandas as pd
from scipy.integrate import odeint
from matplotlib import pyplot as plt


# 微分方程
def diff(y, t, s2ip, i2rp):
    s, i, r = y
    s2i = i * s * s2ip
    i2r = i * i2rp
    ds = -s2i
    di = s2i - i2r
    dr = i2r
    return [ds, di, dr]

# 自变量范围
t = np.arange(0, 90)
# 求解
y = odeint(
    # 微分方程
    func=diff,
    # y初值
    y0=(1, 0.01, 0),
    # 自变量
    t=t,
    # 其他参数(此处为s2ip,i2rp)
    args=(0.4, 0.2)
    )

# 返回数据为积分后的数值序列
data = pd.DataFrame(y)
data.columns = ['S', 'I', 'R']
data.plot()
plt.show()

```

## 优化模型，拟合数据

### minimize

```
# 定义损失函数
# 返回一个值用来量化与期望的大小
def lose_fun(
    x0, # 变量值
    args, # 其他参数(常数值)
)
```

```
# 优化函数
# 返回值res.x取得优化后的参数
def minimize(
    fun, # 损失函数/目标函数
    x0, # 变量的初始值猜测值
    args, # lose_fun的其他参数
    method, # 优化方法
    bounds， # 参数范围[(min,max),(min,max),...]
)
```
