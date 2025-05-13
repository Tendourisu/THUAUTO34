---
title: week-12-信号处理的变换与性质总结
tags:
  - 信号与系统
categories: 
date: 2025-05-13T21:00:59+08:00
modify: 2025-05-13T21:00:59+08:00
dir: 
share: false
cdate: 2025-05-13T21
mdate: 2025-05-13T21
---

##  1  Z 变换性质总汇

### 1.1 Z 变换的主要性质表

下表总结了 Z 变换的主要性质：

| 名称             | $x[n]$                      | $X(z)$                                      | 收敛域 (ROC)                                                                      |
| ---------------- | --------------------------- | ------------------------------------------- | --------------------------------------------------------------------------------- |
| **线性性质** | $ax[n]+by[n]$               | $aX(z)+bY(z)$                               | $max(R_{x_{-}},R_{y_{-}})<\ |z\|<min (R_{x_{+}}, R_{y_{+}})$ (有可能扩大)              |
| **位移性质** | $x[n-m]$                    | $z^{-m}X(z)$                                | $R_{x_{-}}<\ |z\|<R_{x_{+}}$                                                       |
|                  | $x[n+m]$                    | $z^{m}X(z)$                                 | $R_{x_{-}}<\ |z\|<R_{x_{+}}$                                                       |
| **指数加权** | $a^{n}x[n]$                 | $X(z/a)$                                    | $R_{x_{-}}\ |a\|<\|z\|<R_{x_{+}}\|a\|$ (双边 Z 变换)                                    |
|                  | $(-1)^{n}x[n]$              | $X(-z)$                                     | $R_{x_{-}}<\ |z\|<R_{x_{+}}$                                                       |
| **反褶** | $x[-n]$                     | $X(1/z)$                                    | $1/R_{x_{+}}<\ |z\|<1/R_{x_{-}}$                                                     |
| **尺度变换** | $x_{(k)}[n]$ (序列抽取)      | $X(z^{k})$                                  | $R_{x_{-}}^{1/k}<\ |z\|<R_{x_{+}}^{1/k}$                                               |
| **线性加权** | $nx[n]$                     | $-z\frac{d}{dz}X(z)$                        | $R_{x_{-}}<\ |z\|<R_{x_{+}}$                                                       |
| **共轭对称** | $x^{*}[n]$                  | $X^{*}(z^{*})$                              | $R_{x_{-}}<\ |z\|<R_{x_{+}}$                                                       |
| **初值定理** | $x[0]$ (x[n]为因果序列)     | $\lim_{z\rightarrow\infty}X(z)$              | $\ |z\|>R_{x}$                                                                        |
| **终值定理** | $\lim_{n\rightarrow\infty}x[n]$ (x[n]为因果序列) | $\lim_{z\rightarrow1}(z-1)X(z)$              | $(z-1)X(z)$ 收敛于 $\ |z\|>1$                                                      |
| **卷积定理** | $x[n]*y[n]$                 | $X(z) \cdot Y(z)$                           | $max(R_{x_{-}},R_{y_{-}})<\ |z\|<min (R_{x_{+}}, R_{y_{+}})$ (有可能扩大)              |
| **变换域卷积定理** (序列相乘) | $x[n]y[n]$                  | $\frac{1}{2\pi j}\oint_{C}X(v)Y(\frac{z}{v})v^{-1}dv$ | $R_{x_{-}}R_{y_{-}}<\ |z\|<R_{x_{+}}R_{y_{+}}$ (积分路径 C: $max(R_{x_{-}},\frac{\ |z\|}{R_{y_{+}}})<\|v\|<min (R_{x_{+}},\frac{\|z\|}{R_{y_{-}}})$) |

## 2  Z 变换线性性质

### 2.1 定义
Z 变换是一种线性变换。如果：
$Z\{x[n]\}=X(z)$ , 收敛域为 $(R_{x_{-}}<\|z\|<R_{x_{+}})$
$Z\{y[n]\}=Y(z)$ , 收敛域为 $(R_{y_{-}}<\|z\|<R_{y_{+}})$

则：
$Z\{ax[n]+by[n]\}=aX(z)+bY(z)$
收敛域为 $max(R_{x_{-}},R_{y_{-}})<\|z\|<min(R_{x_{+}},R_{y_{+}})$ 。
*注：当出现收敛域边界的零极点抵消时，收敛域可能扩大。*

### 2.2 示例

#### 示例 1：
已知 $x[n]=a^{n}u[n]$ 和 $h[n]=a^{n}u[n-m]$ 。令 $y[n]=x[n]-h[n]$ 。
求:
(1) $Y(z)=Z\{y[n]\}$
(2) 画出 $Y(z)$ 的零、极点图
(3) 讨论 $Y(z)$ 的收敛域

**解：**
(1) 首先求 $X(z)$ 和 $H(z)$ :
$X(z) = \frac{1}{1-az^{-1}}$ , 收敛域 $\|z\|>\|a\|$
$H(z) = \sum_{n=-\infty}^{\infty}h[n]z^{-n} = \sum_{n=m}^{\infty}a^{n}z^{-n}$
根据 PDF 中的推导:
$H(z) = \sum_{n=0}^{\infty}a^{n}z^{-n} - \sum_{n=0}^{m-1}a^{n}z^{-n} = \frac{1}{1-az^{-1}} - \frac{1-(az^{-1})^{m}}{1-az^{-1}} = \frac{(az^{-1})^{m}}{1-az^{-1}} = \frac{a^{m}z^{-m}}{1-az^{-1}}$
收敛域 $\|z\|>\|a\|$

利用线性性质：
$Y(z) = X(z) - H(z) = \frac{1}{1-az^{-1}} - \frac{a^{m}z^{-m}}{1-az^{-1}} = \frac{1-a^{m}z^{-m}}{1-az^{-1}}$
$Y(z) = \frac{z^{m}-a^{m}}{z^{m-1}(z-a)}$
PDF 指出，由于零极点抵消，收敛域变为 $\|z\|>0$ (假设 $a \neq 0$ )。

(2) 零极点图：
极点： $z=a$ (原有一个极点)， $m-1$ 阶极点在 $z=0$ 处。
零点： $z^{m}-a^{m}=0 \Rightarrow z_{k}=\|a\|e^{j\frac{2\pi k}{m}}$ for $k=0,1,\cdot\cdot\cdot,m-1$
当 $k=0$ 时， $z_0 = \|a\| e^{j0} = \|a\|$ 。此零点与极点 $z=a$ 抵消。

(3) 收敛域讨论：
由于 $z=a$ 处的零极点抵消，原来的收敛域 $\|z\|>\|a\|$ 扩大了。
抵消后，函数变为 $Y(z) = \frac{\prod_{k=1}^{m-1} (z - \|a\|e^{j\frac{2\pi k}{m}})}{z^{m-1}}$ 。
因此，收敛域变为 $\|z\|>0$ (假设 $a \neq 0$ )。

**图表示例: $Y(z)$ 零极点分布图 (描述)**
- 极点：原点 $z=0$ 处有 $m-1$ 阶极点。
- 零点： $m-1$ 个零点均匀分布在半径为 $\|a\|$ 的圆上 (不包括 $z=\|a\|$ )。
- 收敛域： $\|z\| > 0$ 。

#### 示例 2：求双曲余弦和双曲正弦序列的 Z 变换
$x[n]=cosh[n\omega_{0}]u[n]$
$y[n]=sinh[n\omega_{0}]u[n]$

**解：**
已知 $Z\{e^{n\omega_{0}}u[n]\} = \frac{z}{z-e^{\omega_{0}}}$ , ROC: $\|z\| > \|e^{\omega_{0}}\|$
$Z\{e^{-n\omega_{0}}u[n]\} = \frac{z}{z-e^{-\omega_{0}}}$ , ROC: $\|z\| > \|e^{-\omega_{0}}\|$

$cosh[n\omega_{0}] = \frac{e^{n\omega_{0}}+e^{-n\omega_{0}}}{2}$
$Z\{cosh[n\omega_{0}]u[n]\} = Z\{(\frac{e^{n\omega_{0}}+e^{-n\omega_{0}}}{2})u[n]\}$
$= \frac{1}{2}Z\{e^{n\omega_{0}}u[n]\} + \frac{1}{2}Z\{e^{-n\omega_{0}}u[n]\}$
$= \frac{1}{2}\frac{z}{z-e^{\omega_{0}}} + \frac{1}{2}\frac{z}{z-e^{-\omega_{0}}}$
$= \frac{z(z-e^{-\omega_{0}}) + z(z-e^{\omega_{0}})}{2(z-e^{\omega_{0}})(z-e^{-\omega_{0}})}$
$= \frac{z(2z - (e^{\omega_{0}}+e^{-\omega_{0}}))}{2(z^{2} - (e^{\omega_{0}}+e^{-\omega_{0}})z + 1)}$
$= \frac{z(z - cosh\omega_{0})}{z^{2} - 2zcosh\omega_{0} + 1}$ , ROC: $\|z\| > max(\|e^{\omega_{0}}\|,\|e^{-\omega_{0}}\|)$

$sinh[n\omega_{0}] = \frac{e^{n\omega_{0}}-e^{-n\omega_{0}}}{2}$
$Z\{sinh[n\omega_{0}]u[n]\} = \frac{1}{2}Z\{e^{n\omega_{0}}u[n]\} - \frac{1}{2}Z\{e^{-n\omega_{0}}u[n]\}$
$= \frac{1}{2}\frac{z}{z-e^{\omega_{0}}} - \frac{1}{2}\frac{z}{z-e^{-\omega_{0}}}$
$= \frac{z(z-e^{-\omega_{0}}) - z(z-e^{\omega_{0}})}{2(z-e^{\omega_{0}})(z-e^{-\omega_{0}})}$
$= \frac{z(e^{\omega_{0}}-e^{-\omega_{0}})}{2(z^{2} - 2zcosh\omega_{0} + 1)}$
$= \frac{z sinh\omega_{0}}{z^{2} - 2zcosh\omega_{0} + 1}$ , ROC: $\|z\| > max(\|e^{\omega_{0}}\|,\|e^{-\omega_{0}}\|)$

##  3  Z 变换位移性质

### 3.1 双边 Z 变换位移性质
如果序列 $x[n]$ 的双边 Z 变换为：
$Z\{x[n]\}=X(z)$ , 收敛域 $R_{x_{-}}<\|z\|<R_{x_{+}}$

则序列经过位移后的 Z 变换为：
$Z\{x[n-m]\}=z^{-m}X(z)$ , 收敛域 $R_{x_{-}}<\|z\|<R_{x_{+}}$ (收敛域不变)
$Z\{x[n+m]\}=z^{m}X(z)$ , 收敛域 $R_{x_{-}}<\|z\|<R_{x_{+}}$ (收敛域不变)

**证明 $Z\{x[n-m]\}=z^{-m}X(z)$ :**
$Z\{x[n-m]\} = \sum_{n=-\infty}^{\infty}x[n-m]z^{-n}$
令 $k=n-m$ , 则 $n=k+m$
$= \sum_{k=-\infty}^{\infty}x[k]z^{-(k+m)} = z^{-m}\sum_{k=-\infty}^{\infty}x[k]z^{-k} = z^{-m}X(z)$
收敛域不变。同理可证 $Z\{x[n+m]\}=z^{m}X(z)$ 。

### 3.2 单边 Z 变换位移性质
如果 $x[n]$ 是一个序列 (不一定是因果序列)，它的单边 Z 变换定义为 $Z\{x[n]u[n]\}$ 。
令 $X(z) = Z\{x[n]u[n]\} = \sum_{n=0}^{\infty}x[n]z^{-n}$ 。

则序列右移的单边 Z 变换为 (对于 $m>0$ )：
$Z\{x[n-m]u[n]\} = z^{-m}[X(z)+\sum_{k=-m}^{-1}x[k]z^{-k}]$
*关键概念：对于因果序列 $x[n]$ (即 $x[k]=0$ for $k<0$ ), 则 $\sum_{k=-m}^{-1}x[k]z^{-k} = 0$ 。此时 $Z\{x[n-m]u[n]\}=z^{-m}X(z)$ 。*

序列左移的单边 Z 变换为 (对于 $m>0$ )：
$Z\{x[n+m]u[n]\} = z^{m}[X(z)-\sum_{k=0}^{m-1}x[k]z^{-k}]$

**证明右移性质：**
$Z\{x[n-m]u[n]\} = \sum_{n=0}^{\infty}x[n-m]z^{-n}$
令 $k=n-m$ , 则 $n=k+m$ 。当 $n=0, k=-m$ 。当 $n=\infty, k=\infty$ 。
$= \sum_{k=-m}^{\infty}x[k]z^{-(k+m)} = z^{-m}\sum_{k=-m}^{\infty}x[k]z^{-k}$
$= z^{-m}[\sum_{k=-m}^{-1}x[k]z^{-k} + \sum_{k=0}^{\infty}x[k]z^{-k}]$
$= z^{-m}[X(z) + \sum_{k=-m}^{-1}x[k]z^{-k}]$ (PDF 中的顺序与此略有不同，但结果一致)

### 3.3 示例
**例题 1：**
已知 $x[n]=\delta[n+1]+2\delta[n]+\delta[n-1]$
求 $x[n]$ , $x[n+1]$ , $x[n-1]$ 的单边 Z 变换。

**解：**
$x[-1]=1, x[0]=2, x[1]=1$ .
单边 Z 变换 $X_U(z) = Z\{x[n]u[n]\} = \sum_{n=0}^{\infty}x[n]z^{-n}$
$X_U(z) = x[0]z^0 + x[1]z^{-1} + x[2]z^{-2} + \dots$
$= 2 \cdot z^0 + 1 \cdot z^{-1} + 0 + \dots = 2+z^{-1}$

$Z\{x[n-1]u[n]\}$ : 右移 $m=1$ .
$= z^{-1}[X_{U}(z) + \sum_{k=-1}^{-1}x[k]z^{-k}] = z^{-1}[X_{U}(z) + x[-1]z^{1}]$
$= z^{-1}[2+z^{-1} + 1 \cdot z] = z^{-1}[2+z^{-1}+z] = 2z^{-1}+z^{-2}+1 = 1+2z^{-1}+z^{-2}$

$Z\{x[n+1]u[n]\}$ : 左移 $m=1$ .
$= z^{1}[X_{U}(z) - \sum_{k=0}^{0}x[k]z^{-k}] = z[X_{U}(z) - x[0]z^{0}]$
$= z[2+z^{-1} - 2] = z[z^{-1}] = 1$

**图示序列：**
| n    | $x[n]$ | $x[n]u[n]$ | $x[n-1]u[n]$ | $x[n+1]u[n]$ |
| ---- | ------ | ---------- | ------------ | ------------ |
| -2   | 0      | 0          | 0            | 0            |
| -1   | 1      | 0          | $x[-1]=1$    | $x[0]=2$     |
| 0    | 2      | $x[0]=2$   | $x[0]=2$     | $x[1]=1$     |
| 1    | 1      | $x[1]=1$   | $x[1]=1$     | $x[2]=0$     |
| 2    | 0      | $x[2]=0$   | $x[2]=0$     | $x[3]=0$     |
单边 Z 变换:
$Z\{x[n]u[n]\} = 2+z^{-1}$
$Z\{x[n-1]u[n]\} = 1+2z^{-1}+z^{-2}$
$Z\{x[n+1]u[n]\} = 1$
结果与公式计算一致。

##  4  Z 变换初值与终值定理

### 4.1 初值定理
如果 $x[n]$ 为因果序列 (即 $x[n]=0$ for $n<0$ ), 且 $X(z)=Z\{x[n]\} = \sum_{n=0}^{\infty}x[n]z^{-n}$ ，则：
$x[0] = \lim_{z\rightarrow\infty}X(z)$

**证明：**
$X(z) = x[0] + x[1]z^{-1} + x[2]z^{-2} + \dots$
$\lim_{z\rightarrow\infty}X(z) = \lim_{z\rightarrow\infty}(x[0] + x[1]z^{-1} + x[2]z^{-2} + \dots)$
$= x[0] + x[1]\cdot 0 + x[2]\cdot 0 + \dots = x[0]$

### 4.2 终值定理
如果 $x[n]$ 为因果序列，且 $X(z)=Z\{x[n]\}$ ，则：
$\lim_{n\rightarrow\infty}x[n] = \lim_{z\rightarrow1}(z-1)X(z)$

**关键概念：终值定理条件**
序列 $x[n]$ 必须收敛 (即 $\lim_{n\rightarrow\infty}x[n]$ 存在)。
这等价于 $(z-1)X(z)$ 的所有极点必须都位于单位圆内，或者说 $X(z)$ 的所有极点必须位于单位圆内，除了在 $z=1$ 处可能有一个一阶极点。

**一个证明思路 (来自 PDF)：**
$Z\{x[n+1]-x[n]\} = zX(z)-zx[0]-X(z) = (z-1)X(z)-zx[0]$ (PDF 中为 $zx[n]$ ，应为 $zx[0]$ )
$\lim_{z\rightarrow1}(z-1)X(z) = \lim_{z\rightarrow1}zx[0] + \lim_{z\rightarrow1}\sum_{n=0}^{\infty}(x[n+1]-x[n])z^{-n}$
$= x[0] + \sum_{n=0}^{\infty}(x[n+1]-x[n])$ (如果和收敛)
$= x[0] + (x[1]-x[0]) + (x[2]-x[1]) + \dots$
$= \lim_{N\rightarrow\infty} x[N+1] = x[\infty]$ (伸缩求和)

### 4.3 示例
**例题 1：**
设有差分方程： $x[n]-ax[n-1]=u[n]$ , $-1<a<1$
初始条件 $x[n]=0, n<0$ (即因果系统，初始松弛)。
(1) 使用初值定理和终值定理求 $x[0], x[\infty]$ 。
(2) 求出 $x[n]$ 的表达式，并验证上述结果。

**解：**
(1) 对差分方程两边取 Z 变换 (由于是因果且初始松弛, $Z\{x[n-1]\} = z^{-1}X(z)$ ):
$X(z) - az^{-1}X(z) = Z\{u[n]\} = \frac{1}{1-z^{-1}}$ (ROC: $\|z\|>1$ )
$X(z)(1-az^{-1}) = \frac{1}{1-z^{-1}}$
$X(z) = \frac{1}{(1-z^{-1})(1-az^{-1})} = \frac{z^2}{(z-1)(z-a)}$ , ROC: $\|z\|>1$ (因为 $-1<a<1$ , 所以 $a<1$ )

初值定理：
$x[0] = \lim_{z\rightarrow\infty}X(z) = \lim_{z\rightarrow\infty}\frac{z^2}{(z-1)(z-a)} = \lim_{z\rightarrow\infty}\frac{1}{(1-1/z)(1-a/z)} = 1$

终值定理：
极点为 $z=1$ 和 $z=a$ 。由于 $-1<a<1$ , 极点 $z=a$ 在单位圆内。极点 $z=1$ 在单位圆上 (一阶)。
$(z-1)X(z) = (z-1)\frac{z^2}{(z-1)(z-a)} = \frac{z^2}{z-a}$
该函数的极点为 $z=a$ , 在单位圆内。终值定理适用。
$x[\infty] = \lim_{z\rightarrow1}(z-1)X(z) = \lim_{z\rightarrow1}\frac{z^2}{z-a} = \frac{1^2}{1-a} = \frac{1}{1-a}$

(2) 求 $X(z)$ 的反 Z 变换：
$X(z) = \frac{1}{1-a}(\frac{1}{1-z^{-1}} - \frac{a}{1-az^{-1}})$ (PDF 中的部分分式形式)
$x[n] = \frac{1}{1-a}(1^n u[n] - a \cdot a^n u[n]) = \frac{1}{1-a}(1-a^{n+1})u[n]$ (PDF 结果)

验证：
$x[0] = \frac{1}{1-a}(1-a^{0+1})u[0] = \frac{1}{1-a}(1-a) \cdot 1 = 1$ . (与初值定理结果一致)
$x[\infty] = \lim_{n\rightarrow\infty} \frac{1}{1-a}(1-a^{n+1})$
由于 $-1<a<1$ , $\lim_{n\rightarrow\infty}a^{n+1} = 0$ .
$x[\infty] = \frac{1}{1-a}(1-0) = \frac{1}{1-a}$ . (与终值定理结果一致)

##  5  Z 变换时域卷积定理

### 5.1 定义
已知 $x[n]$ 和 $y[n]$ 的 Z 变换为：
$X(z)=Z\{x[n]\}$ , 收敛域 $R_{x_{-}}<\|z\|<R_{x_{+}}$
$Y(z)=Z\{y[n]\}$ , 收敛域 $R_{y_{-}}<\|z\|<R_{y_{+}}$

则：
$Z\{x[n]*y[n]\} = X(z) \cdot Y(z)$
收敛域为 $max(R_{x_{-}},R_{y_{-}})<\|z\|<min(R_{x_{+}},R_{y_{+}})$ 。
*注：当出现收敛域边界的零极点抵消时，收敛域可能扩大。*

**证明：**
$Z\{x[n]*y[n]\} = \sum_{n=-\infty}^{\infty} (\sum_{m=-\infty}^{\infty}x[m]y[n-m]) z^{-n}$
$= \sum_{m=-\infty}^{\infty}x[m] \sum_{n=-\infty}^{\infty}y[n-m]z^{-n}$
令 $k=n-m$ , 则 $n=k+m$ .
$= \sum_{m=-\infty}^{\infty}x[m] \sum_{k=-\infty}^{\infty}y[k]z^{-(k+m)}$
$= \sum_{m=-\infty}^{\infty}x[m]z^{-m} \sum_{k=-\infty}^{\infty}y[k]z^{-k}$
$= X(z)Y(z)$

### 5.2 解卷积
如果 $y[n]=x[n]*h[n]$ , 则 $Y(z)=X(z)H(z)$ 。
- 已知 $Y(z), X(z) \Rightarrow H(z) = Y(z)/X(z) \Rightarrow h[n]$
- 已知 $Y(z), H(z) \Rightarrow X(z) = Y(z)/H(z) \Rightarrow x[n]$

### 5.3 示例
#### 示例 1：
已知 LTI 系统的单位脉冲响应为 $h[n]=a^{n}u[n]$ , $0<a<1$ 。
系统输入为 $x[n]=\begin{cases}1, & 0\le n\le N-1\\ 0, & \text{Otherwise}\end{cases}$ 。
求系统的零状态响应 $y[n]=x[n]*h[n]$ 。

**解：**
$H(z) = Z\{a^{n}u[n]\} = \frac{z}{z-a}$ , ROC: $\|z\|>a$
$x[n] = u[n] - u[n-N]$
$X(z) = Z\{u[n]\} - Z\{u[n-N]\}$
$Z\{u[n]\} = \frac{z}{z-1}$ , ROC: $\|z\|>1$
$Z\{u[n-N]\} = z^{-N}\frac{z}{z-1} = \frac{z^{-N+1}}{z-1}$ , ROC: $\|z\|>1$
$X(z) = \frac{z}{z-1} - \frac{z^{-N+1}}{z-1} = \frac{z-z^{-N+1}}{z-1} = \frac{z(1-z^{-N})}{z-1}$ , ROC: $\|z\|>1$

$Y(z) = X(z)H(z) = \frac{z(1-z^{-N})}{z-1} \cdot \frac{z}{z-a} = \frac{z^2(1-z^{-N})}{(z-1)(z-a)}$ , ROC: $\|z\|>1$ (因为 $0<a<1$ )

令 $Y_1(z) = \frac{z^2}{(z-1)(z-a)}$ 。则 $Y(z) = Y_1(z)(1-z^{-N})$ 。
$\frac{Y_1(z)}{z} = \frac{z}{(z-1)(z-a)} = \frac{A}{z-1} + \frac{B}{z-a}$
$A = \frac{1}{1-a}$ , $B = \frac{a}{a-1} = \frac{-a}{1-a}$
$Y_1(z) = \frac{1}{1-a}\frac{z}{z-1} - \frac{a}{1-a}\frac{z}{z-a}$
$y_1[n] = (\frac{1}{1-a} - \frac{a}{1-a}a^n)u[n] = \frac{1-a^{n+1}}{1-a}u[n]$

$Y(z) = Y_1(z) - z^{-N}Y_1(z)$
$y[n] = y_1[n] - y_1[n-N]$
$y[n] = \frac{1-a^{n+1}}{1-a}u[n] - \frac{1-a^{n-N+1}}{1-a}u[n-N]$

#### 示例 2：求下列两序列的卷积
$h[n]=a^{n}u[n]-a^{n-1}u[n-1]$
$x[n]=u[n]$

**解：**
$X(z) = \frac{z}{z-1}$ , ROC: $\|z\|>1$
根据 PDF: $H(z) = \frac{z}{z-a} - \frac{z}{z-a} \cdot z^{-1} = \frac{z-1}{z-a}$ , ROC: $\|z\|>a$
(这里假设 $Z\{a^{n-1}u[n-1]\}$ 是 $Z\{a \cdot (a^{n-1}u[n-1])\}$ 还是 $Z\{k[n-1]\}$ 其中 $k[n]=a^n u[n]$ 。PDF 的推导 $Z\{a^n u[n]\} - z^{-1}Z\{a^n u[n]\}$ 意味着 $h[n]$ 实际上是 $a^n u[n] - a^n u[n-1]$ 。如果严格按照 $a^{n-1}u[n-1]$ ，则 $H(z) = \frac{z}{z-a} - \frac{1}{a} \frac{az^{-1}}{1-az^{-1}} = \frac{z}{z-a} - \frac{1}{z-a}$ 。但 PDF 结果是 $\frac{z-1}{z-a}$ 。)

使用 PDF 的 $H(z)$ :
$Y(z) = X(z)H(z) = \frac{z}{z-1} \cdot \frac{z-1}{z-a} = \frac{z}{z-a}$
ROC: $\max(1,\|a\|) < \|z\|$ 。由于 $z=1$ 处的零极点抵消，收敛域扩大为 $\|z\|>\|a\|$ 。
$y[n] = Z^{-1}\{\frac{z}{z-a}\} = a^n u[n]$

**图示： $Y(z)$ 的收敛域 (描述)**
- 零极点抵消在 $z=1$ 处。
- 极点在 $z=a$ 。
- 收敛域为 $\|z\| > \|a\|$ 。

##  6  Z 变换变换域卷积定理 (序列相乘定理)

### 6.1 定理
已知 $w[n]=x[n] \cdot y[n]$ , 且：
$X(z)=Z\{x[n]\}$ , 收敛域 $R_{x_{-}}<\|z\|<R_{x_{+}}$
$Y(z)=Z\{y[n]\}$ , 收敛域 $R_{y_{-}}<\|z\|<R_{y_{+}}$

则：
$W(z) = Z\{x[n] \cdot y[n]\} = \frac{1}{2\pi j}\oint_{C}X(v)Y(\frac{z}{v})v^{-1}dv$
收敛域为 $R_{x_{-}}R_{y_{-}} < \|z\| < R_{x_{+}}R_{y_{+}}$ 。
积分围线 C (contour of integration) 必须在 $X(v)$ 和 $Y(z/v)$ 的收敛域的重叠区域内。
具体来说，C 必须满足：
$R_{x_{-}} < \|v\| < R_{x_{+}}$
$R_{y_{-}} < \|\frac{z}{v}\| < R_{y_{+}} \Rightarrow \frac{\|z\|}{R_{y_{+}}} < \|v\| < \frac{\|z\|}{R_{y_{-}}}$
所以，围线 C 必须在 $max(R_{x_{-}}, \frac{\|z\|}{R_{y_{+}}}) < \|v\| < min(R_{x_{+}}, \frac{\|z\|}{R_{y_{-}}})$ 内。

**证明 (来自 PDF)：**
$Z\{x[n] \cdot y[n]\} = \sum_{n=-\infty}^{\infty} (x[n]y[n])z^{-n}$
我们知道 $x[n] = \frac{1}{2\pi j}\oint_{C_1}X(v)v^{n-1}dv$ (PDF 中 $y[n]$ 被替换)
$W(z) = \sum_{n=-\infty}^{\infty} y[n] (\frac{1}{2\pi j}\oint_{C_1}X(v)v^{n-1}dv) z^{-n}$
$= \frac{1}{2\pi j}\oint_{C_1}X(v) (\sum_{n=-\infty}^{\infty}y[n](vz^{-1})^{n}) v^{-1}dv$ (PDF 中为 $y[n]v^{n-1}z^{-n}$ , 应该为 $y[n](v/z)^n$ 或 $y[n](z/v)^{-n}$ )
PDF 的推导: $\frac{1}{2\pi j}\oint_{C}X(v) (\sum_{n=-\infty}^{\infty}y[n](\frac{z}{v})^{-n}) v^{-1}dv$
The sum is $Y(z/v)$ .
$= \frac{1}{2\pi j}\oint_{C}X(v)Y(\frac{z}{v})v^{-1}dv$

### 6.2 示例
已知 $x[n]=a^{n}u[n]$ , $y[n]=b^{n}u[n]$ 。 $w[n]=x[n] \cdot y[n] = (ab)^n u[n]$ 。
用 z 域卷积定理求 $W(z)$ 。

**解：**
$X(z) = \frac{z}{z-a}$ , ROC: $\|z\|>\|a\|$ (so $X(v) = \frac{v}{v-a}$ , ROC: $\|v\|>\|a\|$ )
$Y(z) = \frac{z}{z-b}$ , ROC: $\|z\|>\|b\|$ (so $Y(z/v) = \frac{z/v}{z/v-b} = \frac{z}{z-bv}$ , ROC: $\|z/v\|>\|b\| \Rightarrow \|v\|<\|z/b\|$ )

$W(z) = \frac{1}{2\pi j}\oint_{C}X(v)Y(\frac{z}{v})v^{-1}dv$
$= \frac{1}{2\pi j}\oint_{C} \frac{v}{v-a} \cdot \frac{z/v}{z/v-b} \cdot v^{-1} dv$
$= \frac{z}{2\pi j}\oint_{C} \frac{1}{(v-a)(z-bv)} dv$

积分围线 C 必须满足 $\|a\| < \|v\| < \|z/b\|$ (假设 $\|z/b\| > \|a\|$ , i.e., $\|z\| > \|ab\|$ ).
The integrand is $\frac{1}{(v-a)(-b)(v-z/b)} = \frac{-1/b}{(v-a)(v-z/b)}$ .
The poles of the integrand (with respect to $v$ ) are at $v=a$ and $v=z/b$ .
The contour C encloses the pole $v=a$ but not $v=z/b$ .

Using Cauchy's Residue Theorem:
$W(z) = z \cdot (\text{Residue of } \frac{1}{(v-a)(z-bv)} \text{ at } v=a)$
Residue at $v=a$ is $\lim_{v\rightarrow a} (v-a) \frac{1}{(v-a)(z-bv)} = \frac{1}{z-ab}$
$W(z) = z \cdot \frac{1}{z-ab} = \frac{z}{z-ab}$
ROC: $\|z\| > \|ab\|$ (derived from $\|a\| < \|z/b\| \Rightarrow \|ab\| < \|z\|$ ).

This matches $Z\{(ab)^n u[n]\} = \frac{z}{z-ab}$ .

**图示：积分围线 C (描述)**
- 复平面 $v$ 。
- 极点在 $v=a$ 和 $v=z/b$ 。
- 围线 C 是一个圆，其半径 $\rho$ 满足 $\|a\| < \rho < \|z/b\|$ 。C 逆时针环绕 $v=a$ 。

##  7 应用 LT 求解微分方程

### 7.1 基本步骤
1.  **微分方程**: $\sum_{k=0}^{N}a_{k}\frac{d^{k}}{dt^{k}}y(t)=\sum_{r=0}^{M}b_{r}\frac{d^{r}}{dt^{r}}x(t)$
2.  **取单边拉普拉斯变换 (LT)**: 利用微分性质 $L\{\frac{d^{n}}{dt^{n}}x(t)\} = s^{n}X(s) - \sum_{j=0}^{n-1}s^{j}x^{(n-1-j)}(0_{-})$
3.  **代数方程**: 将微分方程转换为关于 $Y(s)$ 和 $X(s)$ 的代数方程，包含初始条件。
    $\sum_{k=0}^{N}a_{k}[s^{k}Y(s)-\sum_{l=0}^{k-1}s^{l}y^{(k-1-l)}(0_{-})] = \sum_{r=0}^{M}b_{r}[s^{r}X(s)-\sum_{m=0}^{r-1}s^{m}x^{(r-1-m)}(0_{-})]$
4.  **求解 $Y(s)$ **:
    $Y(s)$ 可以分解为零状态响应 $Y_{zs}(s)$ 和零输入响应 $Y_{zi}(s)$ 。
    $Y_{zs}(s) = H(s)X_{eff}(s)$ where $X_{eff}(s)$ 包含输入信号及其初始条件。
    $Y_{zi}(s)$ 只包含系统输出的初始条件。
    系统函数 $H(s) = \frac{\sum_{r=0}^{M}b_{r}s^{r}}{\sum_{k=0}^{N}a_{k}s^{k}}$ (在零初始条件下定义， $Y(s)=H(s)X(s)$ )
5.  **LT 反变换**: $y(t) = L^{-1}\{Y(s)\}$

### 7.2 示例

#### 示例 (Page 197):
求解微分方程 $\frac{d^{2}f(t)}{dt^{2}}+13\frac{df(t)}{dt}+40f(t)=0$
已知 $f(0_{-})=2, f^{\prime}(0_{-})=-4$

**解：**
对方程两边取 LT:
$(s^2F(s) - sf(0_{-}) - f^{\prime}(0_{-})) + 13(sF(s) - f(0_{-})) + 40F(s) = 0$
$F(s)(s^2+13s+40) = s f(0_{-}) + f^{\prime}(0_{-}) + 13f(0_{-})$
$F(s) = \frac{s(2) + (-4) + 13(2)}{s^2+13s+40} = \frac{2s-4+26}{s^2+13s+40} = \frac{2s+22}{(s+5)(s+8)}$
$F(s) = \frac{A}{s+5} + \frac{B}{s+8}$
$A = \frac{2(-5)+22}{-5+8} = \frac{12}{3}=4$
$B = \frac{2(-8)+22}{-8+5} = \frac{6}{-3}=-2$
$F(s) = \frac{4}{s+5} - \frac{2}{s+8}$
求 LT 反变换:
$f(t) = (4e^{-5t} - 2e^{-8t})u(t)$

#### 示例 1 (Page 198):
因果 LTI 系统的微分方程: $\frac{d^{2}}{dt^{2}}y(t)+\frac{3}{2}\frac{d}{dt}y(t)+\frac{1}{2}y(t)=5e^{-3t}u(t)$
已知 $y(0_{-})=1, y^{\prime}(0_{-})=0$
求系统的全响应 $y(t)$ 以及零状态响应 $y_{zs}(t)$ 和零输入响应 $y_{zi}(t)$ 。

**解：**
对方程两边取 LT:
$(s^2Y(s)-sy(0_{-})-y^{\prime}(0_{-})) + \frac{3}{2}(sY(s)-y(0_{-})) + \frac{1}{2}Y(s) = \frac{5}{s+3}$
$Y(s)(s^2+\frac{3}{2}s+\frac{1}{2}) - s(1) - 0 - \frac{3}{2}(1) = \frac{5}{s+3}$
$Y(s)(s^2+\frac{3}{2}s+\frac{1}{2}) = \frac{5}{s+3} + s + \frac{3}{2}$
$Y(s) = \frac{\frac{5}{s+3}}{s^2+\frac{3}{2}s+\frac{1}{2}} + \frac{s+\frac{3}{2}}{s^2+\frac{3}{2}s+\frac{1}{2}}$
$Y_{zs}(s) = \frac{5}{(s+3)(s+1)(s+1/2)}$
$Y_{zi}(s) = \frac{s+3/2}{(s+1)(s+1/2)}$

$Y_{zs}(s) = \frac{1}{s+3} - \frac{5}{s+1} + \frac{4}{s+1/2}$ (根据 PDF 部分分式结果)
$y_{zs}(t) = (e^{-3t} - 5e^{-t} + 4e^{-t/2})u(t)$

$Y_{zi}(s) = \frac{-1}{s+1} + \frac{2}{s+1/2}$ (根据 PDF 部分分式结果)
$y_{zi}(t) = (-e^{-t} + 2e^{-t/2})u(t)$

系统全响应 $y(t) = y_{zs}(t) + y_{zi}(t)$
$y(t) = (e^{-3t} - 6e^{-t} + 6e^{-t/2})u(t)$

##  8 应用 ZT 求解差分方程

### 8.1 基本步骤
1.  **差分方程**: $\sum_{k=0}^{N}a_{k}y[n-k]=\sum_{r=0}^{M}b_{r}x[n-r]$
2.  **取单边 Z 变换**:
    - 右移: $Z\{f[n-m]u[n]\} = z^{-m}[F(z)+\sum_{j=-m}^{-1}f[j]z^{-j}]$ (对于 $m>0$ )
    - 左移: $Z\{f[n+m]u[n]\} = z^{m}[F(z)-\sum_{j=0}^{m-1}f[j]z^{-j}]$ (对于 $m>0$ )
3.  **代数方程**: 将差分方程转换为关于 $Y(z)$ 和 $X(z)$ 的代数方程，包含初始条件。
4.  **求解 $Y(z)$ **:
    $Y(z)$ 可以分解为零状态响应 $Y_{zs}(z)$ 和零输入响应 $Y_{zi}(z)$ 。
5.  **ZT 反变换**: $y[n] = ZT^{-1}\{Y(z)\}$

### 8.2 示例

#### 示例 1 (Page 199):
求解系统的差分方程: $y[n+2]-\frac{3}{2}y[n+1]+\frac{1}{2}y[n]=(\frac{1}{4})^{n}$ , $n\ge0$
已知: $y[0]=10, y[1]=4$

**解：**
对方程两边取 Z 变换 (使用左移性质):
$Z\{y[n+2]\} = z^2(Y(z)-y[0]-y[1]z^{-1})$
$Z\{y[n+1]\} = z(Y(z)-y[0])$
$Z\{(\frac{1}{4})^n u[n]\} = \frac{z}{z-1/4}$

$(z^2(Y(z)-y[0]-y[1]z^{-1})) - \frac{3}{2}(z(Y(z)-y[0])) + \frac{1}{2}Y(z) = \frac{z}{z-1/4}$
$Y(z)(z^2 - \frac{3}{2}z + \frac{1}{2}) - z^2y[0] - zy[1] + \frac{3}{2}zy[0] = \frac{z}{z-1/4}$
代入 $y[0]=10, y[1]=4$ :
$Y(z)(z-1)(z-1/2) = \frac{z}{z-1/4} + 10z^2 + 4z - 15z = \frac{z}{z-1/4} + 10z^2 - 11z$
$Y(z) = \frac{z + (10z^2-11z)(z-1/4)}{(z-1/4)(z-1)(z-1/2)} = \frac{10z^3 - 13.5z^2 + 3.75z}{(z-1/4)(z-1)(z-1/2)}$
PDF 中给出 $\frac{Y(z)}{z} = \frac{10z^2 - \frac{27}{2}z + \frac{15}{4}}{(z-\frac{1}{4})(z-\frac{1}{2})(z-1)}$
$\frac{Y(z)}{z} = \frac{16/3}{z-1/4} + \frac{4}{z-1/2} + \frac{2/3}{z-1}$ (根据 PDF 部分分式结果)
$Y(z) = \frac{16}{3}\frac{z}{z-1/4} + 4\frac{z}{z-1/2} + \frac{2}{3}\frac{z}{z-1}$
$y[n] = [\frac{16}{3}(\frac{1}{4})^n + 4(\frac{1}{2})^n + \frac{2}{3}(1)^n]u[n]$

#### 示例 2 (Page 200):
已知系统差分方程: $y[n]-\frac{3}{2}y[n-1]+\frac{1}{2}y[n-2]=(\frac{1}{4})^{n}$ , $n\ge0$
起始条件: $y[-1]=4, y[-2]=10$

**解：**
对方程两边取 Z 变换 (使用右移性质):
$Z\{y[n-1]\} = z^{-1}Y(z) + y[-1]$
$Z\{y[n-2]\} = z^{-2}Y(z) + z^{-1}y[-1] + y[-2]$
$Z\{(\frac{1}{4})^n u[n]\} = \frac{1}{1-(1/4)z^{-1}}$

$Y(z) - \frac{3}{2}(z^{-1}Y(z)+y[-1]) + \frac{1}{2}(z^{-2}Y(z)+z^{-1}y[-1]+y[-2]) = \frac{1}{1-(1/4)z^{-1}}$
$Y(z)(1-\frac{3}{2}z^{-1}+\frac{1}{2}z^{-2}) = \frac{1}{1-(1/4)z^{-1}} + \frac{3}{2}y[-1] - \frac{1}{2}z^{-1}y[-1] - \frac{1}{2}y[-2]$
代入 $y[-1]=4, y[-2]=10$ :
$Y(z)(1-\frac{3}{2}z^{-1}+\frac{1}{2}z^{-2}) = \frac{1}{1-(1/4)z^{-1}} + 6 - 2z^{-1} - 5 = \frac{1}{1-(1/4)z^{-1}} + 1 - 2z^{-1}$
$Y(z) = \frac{\frac{1}{1-(1/4)z^{-1}} + 1 - 2z^{-1}}{1-\frac{3}{2}z^{-1}+\frac{1}{2}z^{-2}} = \frac{2 - (9/4)z^{-1} + (1/2)z^{-2}}{(1-(1/4)z^{-1})(1-z^{-1})(1-(1/2)z^{-1})}$
根据 PDF 部分分式结果:
$Y(z) = \frac{1/3}{1-(1/4)z^{-1}} + \frac{1}{1-(1/2)z^{-1}} + \frac{2/3}{1-z^{-1}}$
$y[n] = [\frac{1}{3}(\frac{1}{4})^n + (\frac{1}{2})^n + \frac{2}{3}(1)^n]u[n]$

分解为零状态和零输入响应 (根据 PDF):
$Y_{zs}(z) = \frac{\frac{1}{1-(1/4)z^{-1}}}{(1-z^{-1})(1-\frac{1}{2}z^{-1})} = \frac{1/3}{1-(1/4)z^{-1}} - \frac{2}{1-(1/2)z^{-1}} + \frac{8/3}{1-z^{-1}}$
$y_{zs}[n]=[\frac{1}{3}(\frac{1}{4})^{n}-2(\frac{1}{2})^{n}+\frac{8}{3}]u[n]$

$Y_{zi}(z) = \frac{1-2z^{-1}}{(1-z^{-1})(1-\frac{1}{2}z^{-1})} = \frac{3}{1-(1/2)z^{-1}} - \frac{2}{1-z^{-1}}$
$y_{zi}[n]=[3(\frac{1}{2})^{n}-2]u[n]$
$y[n] = y_{zs}[n] + y_{zi}[n] = [\frac{1}{3}(\frac{1}{4})^n + (\frac{1}{2})^n + \frac{2}{3}]u[n]$ (与全响应一致)

##  9  FT, LT, ZT 之间关系

### 9.1 常用信号分析变换图

该图展示了不同变换之间的联系：
- **连续时间信号**:
    - 周期信号 $\xrightarrow{FS}$ 离散频谱 (Fourier Series)
    - 非周期信号 $\xrightarrow{FT}$ 连续频谱 (Fourier Transform)
    - 一般信号 $\xrightarrow{LT}$ s 平面 (Laplace Transform)
- **离散时间信号**:
    - 周期序列 $\xrightarrow{DTFS}$ 周期离散频谱 (Discrete Time Fourier Series)
    - 非周期序列 $\xrightarrow{DTFT}$ 周期连续频谱 (Discrete Time Fourier Transform)
    - 一般序列 $\xrightarrow{ZT}$ z 平面 (Z Transform)
- **DFT/FFT**: 有限长序列 $\xrightarrow{DFT/FFT}$ 有限长离散频谱 (Discrete Fourier Transform / Fast Fourier Transform)

**关键概念：变换间转换**
- LT $\xrightarrow{s=j\omega}$ FT
- ZT $\xrightarrow{z=e^{j\Omega}}$ DTFT (PDF 中为 $z=e^{j\omega}$ 或 $z=e^{j\Omega T_s}$ )
- LT (连续) $\xrightarrow{\text{离散化}}$ ZT (离散) (via $z = e^{sT_s}$ or $s = \frac{1}{T_s} \ln z$ )
- FT (连续) $\xrightarrow{\text{离散化}}$ DTFT (离散)
- DTFT $\xrightarrow{\text{频谱离散化/周期延拓}}$ DFT
- DTFS 与 DFT 在计算上类似。

### 9.2 变换缩写表

| 缩写 | 中文全称             | 英文全称             |
| ---- | -------------------- | -------------------- |
| FS   | 傅里叶级数           | Fourier Series       |
| FT   | 傅里叶变换           | Fourier Transform    |
| LT   | 拉氏变换             | Laplace Transform    |
| ZT   | Z 变换                | Z Transform          |
| DTFT | 离散时间序列傅里叶变换 | Discrete Time Fourier Transform |
| DTFS | 周期序列傅里叶级数   | Discrete Time Fourier Series |
| DFT  | 离散傅里叶变换       | Discrete Fourier Transform |
| FFT  | 快速傅里叶变换       | Fast Fourier Transform |

##  10  FT 与 LT 之间关系

- **傅里叶变换 (FT)**: $F(j\omega) = \int_{-\infty}^{\infty}f(t)e^{-j\omega t}dt$
- **双边拉氏变换 (LT)**: $F(s) = \int_{-\infty}^{\infty}f(t)e^{-st}dt$ , where $s=\sigma+j\omega$
- **单边拉氏变换**: $F(s) = \int_{0_{-}}^{\infty}f(t)e^{-st}dt$

**关键概念：LT 与 FT 的转换**
- 如果 LT 的收敛域包含虚轴 ( $\sigma=0$ ), 则 FT 是 LT 在 $s=j\omega$ 时的特例: $F(j\omega) = F(s)|_{s=j\omega}$
- 对于因果信号 $f(t)u(t)$ , 其单边 LT 为 $F_L(s)$ 。若 $f(t)u(t)e^{-\sigma t}$ 绝对可积，则 $F_L(\sigma+j\omega) = FT\{f(t)u(t)e^{-\sigma t}\}$ 。

**收敛域与 FT 的存在性：**
1.  ** $\sigma_0 > 0$ **: LT 收敛域在右半 s-平面 ( $Re(s) > \sigma_0 > 0$ ) (PDF 中为 $\sigma > \sigma_0$ ) 。虚轴不包含在内，FT 一般不存在。例: $e^{at}u(t), a>0$ , $L(s)=\frac{1}{s-a}$ , ROC: $\sigma>a$ .
2.  ** $\sigma_0 < 0$ **: LT 收敛域包含虚轴 ( $Re(s) > \sigma_0$ , $\sigma_0<0$ )。FT 存在, $F(j\omega)=F(s)|_{s=j\omega}$ . 例: $e^{-at}u(t), a>0$ , $L(s)=\frac{1}{s+a}$ , ROC: $\sigma>-a$ . $FT = \frac{1}{j\omega+a}$ .
3.  ** $\sigma_0 = 0$ **: LT 收敛域边界是虚轴 ( $Re(s)>0$ )。FT 可能存在，但可能包含冲激函数。例: $u(t)$ , $L(s)=\frac{1}{s}$ , ROC: $\sigma>0$ . $FT = \frac{1}{j\omega}+\pi\delta(\omega)$ .

**图示 (s-平面收敛域描述)：**
- $e^{at}u(t)$ ( $a>0$ ): ROC 是 $\sigma > a$ (虚轴右侧，不含虚轴)。
- $e^{-at}u(t)$ ( $a>0$ ): ROC 是 $\sigma > -a$ (包含虚轴的右半平面)。

##  11  LT 与 ZT 之间关系

### 11.1 定义之间的推导
连续信号 $x(t)$ 经过理想采样得到脉冲序列信号 $x_s(t) = \sum_{n=-\infty}^{\infty}x(nT_s)\delta(t-nT_s)$ 。
$X_s(s) = L\{x_s(t)\} = \sum_{n=-\infty}^{\infty}x(nT_s)e^{-snT_s}$ 。
令 $x[n] = x(nT_s)$ (离散时间序列)，并进行变量代换 $z = e^{sT_s}$ ，则：
$X(z) = \sum_{n=-\infty}^{\infty}x[n]z^{-n}$
这是从 LT 到 ZT 的一种推导方式。
同时， $X_s(s)$ 也可以表示为 $X_s(s) = \frac{1}{T_s}\sum_{k=-\infty}^{\infty}X(s-jk\omega_s)$ ，其中 $\omega_s = 2\pi/T_s$ 。

### 11.2 LT 与 ZT 表达式之间的关系 (冲激响应不变法)
如果连续信号 $x(t)$ 的 LT 为 $X(s) = \sum_{i=1}^{N}\frac{A_{i}}{s-p_{i}}$ (即 $x(t)=\sum_{i=1}^{N}A_{i}e^{p_{i}t}u(t)$ )。
对应的离散序列 $x[n] = x(nT_s) = \sum_{i=1}^{N}A_{i}e^{p_{i}nT_s}u[n]$ 。
其 Z 变换为 $X(z) = \sum_{i=1}^{N}\frac{A_{i}}{1-e^{p_{i}T_s}z^{-1}}$ 。
这种从 s 域极点 $p_i$ 到 z 域极点 $e^{p_iT_s}$ 的映射称为冲激响应不变法。

**常用信号的拉氏变换与 Z 变换表：**

| 序号 | $x(t)$ (连续)             | $X(s)$ (LT)                             | $x[n]=x(nT_s)$ (离散)             | $X(z)$ (ZT)                                                                 |
| ---- | ------------------------- | --------------------------------------- | ------------------------------- | --------------------------------------------------------------------------- |
| ①    | $\delta(t)$               | $1$                                     | $\delta[n]$ (PDF 为 $\delta[nT]$ ) | $1$                                                                         |
| ②    | $u(t)$                    | $\frac{1}{s}$                           | $u[n]$ (PDF 为 $u[nT]$ )           | $\frac{z}{z-1}$                                                             |
| ③    | $t u(t)$                  | $\frac{1}{s^2}$                         | $nT_s u[n]$ (PDF 为 $t$ )         | $\frac{T_s z}{(z-1)^2}$ (PDF 为 $\frac{zT}{(z-1)^2}$ )                          |
| ④    | $e^{-at}u(t)$             | $\frac{1}{s+a}$                         | $e^{-anT_s}u[n]$                | $\frac{z}{z-e^{-aT_s}}$                                                     |
| ⑤    | $t^2 u(t)$                | $\frac{2}{s^3}$                         | $(nT_s)^2 u[n]$ (PDF 为 $t^2$ )   | $\frac{T_s^2 z(z+1)}{(z-1)^3}$                                              |
| ⑥    | $\sin(\omega_0 t)u(t)$    | $\frac{\omega_0}{s^2+\omega_0^2}$       | $\sin(n\omega_0 T_s)u[n]$       | $\frac{z\sin(\omega_0 T_s)}{z^2-2z\cos(\omega_0 T_s)+1}$                     |
| ⑦    | $\cos(\omega_0 t)u(t)$    | $\frac{s}{s^2+\omega_0^2}$        | $\cos(n\omega_0 T_s)u[n]$       | $\frac{z(z-\cos(\omega_0 T_s))}{z^2-2z\cos(\omega_0 T_s)+1}$                 |
| ⑧    | $te^{-at}u(t)$            | $\frac{1}{(s+a)^2}$                     | $nT_s e^{-anT_s}u[n]$           | $\frac{T_s z e^{-aT_s}}{(z-e^{-aT_s})^2}$                                   |
| ⑨    | $e^{-at}\sin(\omega_0 t)u(t)$ | $\frac{\omega_0}{(s+a)^2+\omega_0^2}$   | $e^{-anT_s}\sin(n\omega_0 T_s)u[n]$ | $\frac{z e^{-aT_s}\sin(\omega_0 T_s)}{z^2-2z e^{-aT_s}\cos(\omega_0 T_s)+e^{-2aT_s}}$ |
| ⑩    | $e^{-at}\cos(\omega_0 t)u(t)$ | $\frac{s+a}{(s+a)^2+\omega_0^2}$    | $e^{-anT_s}\cos(n\omega_0 T_s)u[n]$ | $\frac{z(z-e^{-aT_s}\cos(\omega_0 T_s))}{z^2-2z e^{-aT_s}\cos(\omega_0 T_s)+e^{-2aT_s}}$ |

### 11.3 LT 与 ZT 收敛域对应关系
**关键概念：s 平面到 z 平面的映射**
$z = e^{sT_s}$
令 $s = \sigma + j\omega$ and $z = re^{j\theta}$ (PDF 中为 $z=re^{j\Omega}$ 或 $z=re^{j\theta}$ ), $T_s$ 为采样周期。
则 $r = e^{\sigma T_s}$ and $\theta = \omega T_s = 2\pi \frac{\omega}{\omega_s}$, 其中 $\omega_s = \frac{2\pi}{T_s}$。

**映射关系表：**

| s-平面 (s-plane)          | z-平面 (z-plane)         |
| ------------------------- | ------------------------ |
| 虚轴 ($s=j\omega$, $\sigma=0$) | 单位圆 ($z=e^{j\omega T_s}$, $r=1$) |
| 右半平面 ($\sigma > 0$)   | 单位圆外部 ($r > 1$)     |
| 左半平面 ($\sigma < 0$)   | 单位圆内部 ($r < 1$)     |
| 平行于虚轴的直线 ($s=a+j\omega$) | 以原点为圆心的圆 ($r=e^{aT_s}$) |
| 实轴 ($s=\sigma$, $\omega=0$) | 正实轴 ($z=e^{\sigma T_s} > 0$) |
| 平行于实轴的直线 ($s=\sigma+j\omega_1$) | 过原点的射线 ($z=e^{\sigma T_s}e^{j\omega_1 T_s}$) |
| s 平面原点 ($s=0$)         | z 平面点 ($z=1$)          |
| s 平面无穷远点             | z 平面原点或无穷远点      |

**图示 (区域映射描述)：**
- s 平面的虚轴映射到 z 平面的单位圆。
- s 平面的右半平面 (Re[s] > 0) 映射到 z 平面的单位圆外部 (\|z\| > 1)。
- s 平面的左半平面 (Re[s] < 0) 映射到 z 平面的单位圆内部 (\|z\| < 1)。
- s 平面上平行于虚轴的直线 $s=a+j\omega$ 映射到 z 平面上半径为 $e^{aT_s}$ 的圆。
- s 平面上平行于实轴的直线 $s=\sigma+j\omega_1$ 映射到 z 平面上过原点角度为 $\omega_1 T_s$ 的射线。

##  12  ZT 与 DTFT 之间关系

**关键概念：DTFT 是 ZT 在单位圆上的表现**
离散时间傅里叶变换 (DTFT) $X (e^{j\Omega})$ (PDF 中用 $\Omega$ 或 $\omega$) 是 Z 变换 $X (z)$ 在 $z=e^{j\Omega}$ (即单位圆) 上的取值。
$DTFT\{x[n]\} = X (z)|_{z=e^{j\Omega}} = X (e^{j\Omega}) = \sum_{n=-\infty}^{\infty}x[n]e^{-j\Omega n}$
DTFT 存在的充分条件是 $\sum_{n=-\infty}^{\infty}|x[n]| < \infty$ (绝对可和)。
$X (e^{j\Omega})$ 是关于 $\Omega$ 的周期函数，周期为 $2\pi$。

**DTFT 基本性质 (汇总表)：**

| 性质名称         | 时域序列                               | DTFT                                                                 |
| ---------------- | -------------------------------------- | -------------------------------------------------------------------- |
| ① 线性性质       | $ax_1[n]+bx_2[n]$                      | $aX_1 (e^{j\Omega})+bX_2 (e^{j\Omega})$                                  |
| ② 序列位移       | $x[n-n_0]$                             | $e^{-j\Omega n_0}X (e^{j\Omega})$                                     |
| ③ 频域位移       | $e^{j\Omega_0 n}x[n]$                  | $X (e^{j (\Omega-\Omega_0)})$                                          |
| ④ 序列线性加权   | $nx[n]$                                | $j\frac{d}{d\Omega}X (e^{j\Omega})$                                   |
| ⑤ 奇偶虚实性     | $x[n]$ (实序列)                        | $X (e^{j\Omega})=X^*(e^{-j\Omega})$ (共轭对称) <br> $Re[X (e^{j\Omega})]$偶对称, $Im[X (e^{j\Omega})]$奇对称 <br> $|X (e^{j\Omega})|$偶对称, $\phi (\Omega)$奇对称 |
| ⑥ 时域卷积定理   | $x[n]*h[n]$                            | $X (e^{j\Omega}) \cdot H (e^{j\Omega})$                                |
| ⑦ 频域卷积定理   | $x[n] \cdot h[n]$                      | $\frac{1}{2\pi}X (e^{j\Omega}) * H (e^{j\Omega})$ (周期卷积) <br> $= \frac{1}{2\pi}\int_{-\pi}^{\pi}X (e^{j\theta}) H (e^{j (\Omega-\theta)}) d\theta$ |
| ⑧ 序列反褶       | $x[-n]$                                | $X (e^{-j\Omega})$                                                    |
| ⑨ 帕塞瓦尔定理   |                                        | $\sum_{n=-\infty}^{\infty}|x[n]|^{2}=\frac{1}{2\pi}\int_{-\pi}^{\pi}|X (e^{j\Omega})|^{2}d\Omega$ |
| ⑩ 序列扩展性质   | $x_{(k)}[n]=\begin{cases}x[n/k],& n=mk\\ 0,& \text{else}\end{cases}$ | $X (e^{jk\Omega})$                                                    |

**常见序列的 DTFT 表 (部分)：**

| 序号 | 时域序列 $x[n]$                                 | DTFT $X (e^{j\Omega})$                                                                    |
| ---- | ----------------------------------------------- | --------------------------------------------------------------------------------------- |
| (1)  | $\delta[n]$                                     | $1$                                                                                     |
| (2)  | $1$ (常数)                                      | $2\pi\sum_{k=-\infty}^{\infty}\delta (\Omega-2k\pi)$                                     |
| (3)  | $u[n]$                                          | $\frac{1}{1-e^{-j\Omega}}+\pi\sum_{k=-\infty}^{\infty}\delta (\Omega-2k\pi)$             |
| (4)  | $a^{n}u[n]$, $\|a\|<1$                          | $\frac{1}{1-ae^{-j\Omega}}$                                                             |
| (5)  | $a^{\|n\|}$, $\|a\|<1$                          | $\frac{1-a^{2}}{1-2a\cos\Omega+a^{2}}$                                                  |
| (6)  | $u[n+M]-u[n-M-1]$ (PDF 为 $u[n+M]-u[n-M]$) (矩形脉冲) | $\frac{\sin[\Omega (M+1/2)]}{\sin (\Omega/2)}$ (PDF 为 $\frac{\sin[\frac{\Omega}{2}(2M+1)]}{\sin (\frac{\Omega}{2})}$) |
| (8)  | $e^{j\Omega_0 n}$                               | $2\pi\sum_{k=-\infty}^{\infty}\delta (\Omega-\Omega_0-2k\pi)$                             |

##  13 从 FT 到 DFT

从连续傅里叶变换 (FT) 到离散傅里叶变换 (DFT) 涉及几个关键步骤和可能引入的误差：
1.  **截断 (Truncation)**: 实际信号是无限长的，计算时需要截断成有限长 $T_1$。
    -   $f_1 (t) = f (t) \cdot g (t)$, 其中 $g (t)$ 是窗函数。
    -   频域表现为 $F_1 (j\omega) = \frac{1}{2\pi}F (j\omega) * G (j\omega)$。
    -   **误差**: 频率泄露 (Frequency Leakage)。窗函数的旁瓣导致主谱线能量扩散到相邻频率。
    -   **补偿**: 选择具有良好主瓣窄、旁瓣低的窗函数 (如汉宁窗、海明窗)。增加截断长度 $T_1$。
2.  **采样 (Sampling)**: 对截断后的连续信号 $f_1 (t)$ 以采样周期 $T_s$ (采样频率 $f_s = 1/T_s$) 进行采样，得到离散序列 $f_s[n] = f_1 (nT_s)$。
    -   时域为 $f_s (t) = f_1 (t) \cdot \sum \delta (t-nT_s)$。
    -   频域表现为 $F_s (j\omega) = \frac{1}{T_s}\sum_{k=-\infty}^{\infty}F_1 (j (\omega-k\omega_s))$，即频谱周期延拓。
    -   **误差**: 频率混叠 (Aliasing)。如果采样频率 $f_s < 2f_{max}$ (奈奎斯特采样定理)，高频成分会混叠到低频。
    -   **补偿**: 提高采样频率 $f_s$。在采样前使用抗混叠滤波器 (低通滤波器) 滤除高于 $f_s/2$ 的频率成分。
3.  **频率离散化 (Frequency Discretization / DFT)**: 对采样后序列的 DTFT $F_s (e^{j\Omega})$ (或 $F_s (j\omega)$ 的一个周期) 在 $[0, 2\pi)$ (或 $[0, \omega_s)$) 上进行 N 点等间隔采样，得到 DFT 系数 $X[k]$。
    -   $X[k] = F_s (e^{j\frac{2\pi}{N}k})$。
    -   **误差**: 栅栏效应 (Picket-fence Effect)。DFT 只观察特定频率点，可能错过真实频谱峰值。
    -   **补偿**: 补零 (Zero-padding)。在时域序列尾部补零增加 N 值，从而增加频域采样点数，使频谱更平滑。

**总结图示变化：**

| 操作       | 时域信号形态         | 频域频谱形态                                     | 可能误差       | 补偿措施                               |
| ---------- | -------------------- | ------------------------------------------------ | -------------- | -------------------------------------- |
| 原始信号   | $f (t)$ (连续无限长)  | $F (j\omega)$ (连续非周期)                        | -              | -                                      |
| **截断** | $f_1 (t)$ (连续有限长)| $F_1 (j\omega)$ ($F (j\omega)$与窗函数频谱卷积)      | 频率泄露       | 优良窗函数, 增长 $T_1$                 |
| **采样** | $f_s[n]$ (离散有限长)| $F_s (e^{j\Omega})$ ($F_1 (j\omega)$周期延拓)        | 频率混叠       | 提高 $f_s$, 抗混叠滤波器               |
| **DFT** | $f_s[n]$ (N 点序列)   | $X[k]$ ($F_s (e^{j\Omega})$在 N 点上的采样)         | 栅栏效应       | 时域补零                               |

##  14 从 DFT 到 FFT

**DFT 计算复杂度：**
$X[k]=\sum_{n=0}^{N-1}x[n]W_{N}^{nk}$, 其中 $W_N = e^{-j\frac{2\pi}{N}}$。
- 复数乘法: $N^2$
- 复数加法: $N (N-1)$

**FFT (快速傅里叶变换):**
FFT 是一种高效计算 DFT 的算法。
- **Cooley-Tukey 算法 (DIT - 时域抽取)**: 将 N 点 DFT 分解为两个 N/2 点 DFT。
- **Sande-Tukey 算法 (DIF - 频域抽取)**:

**FFT 计算复杂度 (对于 $N=2^M$):**
- 复数乘法: $\frac{N}{2}\log_2 N$
- 复数加法: $N\log_2 N$
- 改善比 (乘法): $\frac{N^2}{(N/2)\log_2 N} = \frac{2N}{\log_2 N}$

**DFT 计算冗余分析 (FFT 原理基础)：**
1.  **简单系数**: $W_N^0 = 1$, $W_N^{N/2} = -1$
2.  **周期性**: $W_N^{nk+N/2} = -W_N^{nk}$, $W_N^{nk} = W_N^{(nk) \mod N}$
3.  **对称性**: $W_N^{n (N-k)} = W_N^{-nk} = (W_N^{nk})^*$ (共轭对称)
4.  **可约性**: $W_{aN}^{abk} = W_N^{bk}$

**DIT-FFT 算法核心 (蝶形运算)：**
将 N 点序列 $x[n]$ 按奇偶分成两组：
$x_1[p] = x[2p]$ (偶数项)
$x_2[p] = x[2p+1]$ (奇数项)
$X[k] = \sum_{p=0}^{N/2-1}x[2p]W_N^{2pk} + \sum_{p=0}^{N/2-1}x[2p+1]W_N^{(2p+1) k}$
$= \sum_{p=0}^{N/2-1}x_1[p]W_{N/2}^{pk} + W_N^k \sum_{p=0}^{N/2-1}x_2[p]W_{N/2}^{pk}$
$= X_1[k] + W_N^k X_2[k]$  (对于 $0 \le k < N/2$)
利用周期性：
$X[k+N/2] = X_1[k+N/2] + W_N^{k+N/2} X_2[k+N/2]$
$= X_1[k] - W_N^k X_2[k]$ (因为 $X_1[k], X_2[k]$ 是 $N/2$ 点 DFT，周期为 $N/2$； $W_N^{N/2}=-1$)

**蝶形运算单元：**
输入 $A=X_1[k]$ 和 $B=X_2[k]$，输出 $X[k]$ 和 $X[k+N/2]$。
$X[k] = A + W_N^k B$
$X[k+N/2] = A - W_N^k B$

**FFT 计算参数确定：**
1.  **最高分析频率 $f_m$**: 确定信号中感兴趣的最高频率。
2.  **采样频率 $f_s$**: 根据奈奎斯特采样定理，$f_s \ge 2f_m$。
3.  **采样点数 $N$**: 通常取 $2^M$ 以便使用 FFT。
4.  **采样时长 $T_{total} = N \cdot T_s = N/f_s$**。
5.  **频率分辨率 $\Delta f = f_s/N = 1/T_{total}$**: DFT 能分辨的最小频率间隔。

**DIT 算法图形说明 (Page 212 描述)：**
该图展示了 8 点 DIT-FFT 的信号流图。
- **时域抽取**: 输入序列 $x[n]$ 按比特反转顺序排列。
- **多级蝶形运算**:
    - 第一级: 2 点 DFT。
    - 第二级: 4 点 DFT (由两个 2 点 DFT 和旋转因子构成)。
    - 第三级: 8 点 DFT (由两个 4 点 DFT 和旋转因子构成)。
- **频域输出**: $X[k]$ 按自然顺序输出。
- **旋转因子**: $W_N^k$ 在蝶形运算中用于相位调整。

