---
title: bresenham算法
date: 2018-09-17 22:16:44
tags:
  - c++
  - Computer Graphics
---

在实验课上用自己的算法画直线被 diss 效率低  
花了半天时间看了下 Bresenham 算法真 🐮🍺  
总结一下其中的精妙之处  
Bresebham 直线生成算法的基本原理是，每次在最大位移方向上走一步，而另一个方向是走步还是不走步取决于误差项的判别。  
声明 k 为斜率  
在 0≤k<1 的情况下，假设当前点是 P($x_1$,$y_1$)，则下一个点在 $P_u$($x_1$+1,$y_1$+1)与 $P_d$($x_1$+1,$y_1$)中选一。  
以 M 表示 $P_u$ 与 $P_d$ 的中点，即 M($x_1$+1,$y_1$+0.5)。设 Q 是理想直线与 x=$x_i$+1 的交点；  
显然，若 M 在 Q 的下方，则 Pu($x_1$+1,$y_1$+1)离直线较近，应取为下一个像素；否则应取 $P_d$($x_1$+1,$y_1$)。  
理解并不难 主要在于实现  
依据该算法的原理基本能够实现  
窝先试着自己写了一会  
如果要实现各个方向的二维直线绘制  
需要考虑多种情况 写出来很不美观  
教材上给出了更好的解决方案：  
同样以 0≤k<1 为例  
每次选取下个点时理想直线的 y 坐标都步进 k 个单位长度  
累加值即为误差项 $d_i$  
当 $d_i$ 大于 0.5 时选取 Pu 否则选取 $P_d$ 并使 $d_i$-1  
令 $e_i$=$d_i$-0.5  
则 $e_i$>0 时选取 Pu 否则选取 $P_d$  
经过改进，算法的效率大幅提升  
但其中在计算斜率与误差项时会用到小数和除法  
并且下一步的选择只与误差项的符号有关  
因此可以进一步改进：  
可知 $e_i$ 的值由三种值组成：$e_i$=-1/2(初始值)+(n 个)y/x(步进值)-(m 个)1(调整值)...  
同乘 2x 即得 2x*$e_i$=-x+(n 个)2*y-(m 个)2\*x....  
这样即可得到仅由整数构成的算法  
以上仅为对 0≤k<1 情况下的讨论  
其余的情况类似  
附一段杂乱无章的代码

```
point<Type> now_point = start;
  point<Type> e_step, point_step;
  e_step.x = abs(step.x);
  e_step.y = abs(step.y);
  glBegin(GL_POINTS);
  if (step.x == 0 && step.y == 0) //No Step
    return;
  point_step.x = (step.x == 0) ? 1 : step.x / e_step.x;
  point_step.y = (step.y == 0) ? 1 : step.y / e_step.y;
  if (step.x == 0) {   // k is endless
    do{
      glVertex2i(now_point.x, now_point.y);
      now_point.y += point_step.y;
    } while (now_point.y != end.y);
  }
  else if (step.y == 0) {   //k is zero
    do {
      glVertex2i(now_point.x, now_point.y);
      now_point.x += point_step.x;
    } while (now_point.x != end.x);
  }
  else if (abs(step.y / step.x) == 0) {   // |k| < 1
    Type e = -e_step.x;
    do {
      glVertex2i(now_point.x, now_point.y);
      e += 2 * e_step.y;
      now_point.x += point_step.x;
      if (e > 0) {
        now_point.y += point_step.y;
        e -= 2 * e_step.x;
      }
    } while (now_point.x != end.x);
  }
  else {    // |k| >= 1
    Type e = -e_step.y;
    do {
      glVertex2i(now_point.x, now_point.y);
      e += 2 * e_step.x;
      now_point.y += point_step.y;
      if (e > 0) {
        now_point.x += point_step.x;
        e -= 2 * e_step.y;
      }
    } while (now_point.y != end.y);
  }
  glEnd();
  glFlush();

```
