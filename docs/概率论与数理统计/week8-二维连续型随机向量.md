---
title: week8-二维连续型随机向量
tags:
  - 概率论
categories: 
date: 2025-04-07T10:20:35+08:00
modify: 2025-04-07T10:20:35+08:00
dir: 
share: false
cdate: 2025-04-07T10
mdate: 2025-04-07T10
---
# week8-二维连续型随机向量

## §4. 二维连续型随机向量与相关性分析

### 4.1 定义与基本概念
- **定义**：设 $(X,Y)$ 为二维连续型随机变量，若存在非负可积函数 $f(x,y)$ ，使得对任意 $(x,y)\in\mathbb{R}^2$ ，有：
  $$
  F(x,y) = \int_{-\infty}^x \int_{-\infty}^y f(u,v) \, du \, dv
  $$
  或等价地，对于任意二维矩形区域 $C = \{(x,y): a \leq x < b, c \leq y < d\}$ ，满足：
  $$
  P((X,Y) \in C) = \iint_C f(x,y) \, dx \, dy
  $$
  称 $f(x,y)$ 为 $(X,Y)$ 的联合分布密度函数。

- **性质**：
  - $f(x,y) \geq 0$ 且 $\iint_{\mathbb{R}^2} f(x,y) \, dx \, dy = 1$ 。
  - 若 $f(x,y)$ 在点 $(x,y)$ 处连续，则：
    $$
    f(x,y) = \frac{\partial^2 F(x,y)}{\partial x \partial y}
    $$
  - 概率计算公式：
    $$
    P((X,Y) \in A) = \iint_A f(x,y) \, dx \, dy
    $$

### 4.2 边缘分布与数学期望
#### 4.2.1 边缘分布密度
- **边缘分布密度**的求法：
  $$
  f_X(x) = \int_{-\infty}^\infty f(x,y) \, dy, \quad f_Y(y) = \int_{-\infty}^\infty f(x,y) \, dx
  $$
  注意积分限的确定。

#### 4.2.2 数学期望
- **数学期望**的计算公式：
  $$
  E[g(X,Y)] = \iint_{\mathbb{R}^2} g(x,y) f(x,y) \, dx \, dy
  $$
  特别地：
  $$
  EX = \iint_{\mathbb{R}^2} x f(x,y) \, dx \, dy, \quad EX^2 = \iint_{\mathbb{R}^2} x^2 f(x,y) \, dx \, dy
  $$
  从而可以计算方差 $DX = EX^2 - (EX)^2$ 。

- **协方差与相关系数**：
  $$
  Cov(X,Y) = E[XY] - E[X]E[Y], \quad r_{X,Y} = \frac{Cov(X,Y)}{\sqrt{DX \cdot DY}}
  $$

### 4.3 独立性与条件分布
#### 4.3.1 独立性
- **独立性判定**：
  $$
  X \text{与} Y \text{独立} \iff F(x,y) = F_X(x)F_Y(y), \quad f(x,y) = f_X(x)f_Y(y)
  $$

#### 4.3.2 条件密度
- 在 $Y=y$ 的条件下， $X$ 的条件密度函数定义为：
  $$
  f_{X|Y}(x|y) = \frac{f(x,y)}{f_Y(y)}, \quad f_Y(y) > 0
  $$
  条件概率：
  $$
  P(X \in A | Y = y) = \int_A f_{X|Y}(x|y) \, dx
  $$

---

## §5. 条件分布与条件数学期望

### 5.1 条件分布
- 对于事件 $A \subset \mathbb{R}$ ，若 $P(X \in A) > 0$ ，则在已知 $X \in A$ 的条件下， $Y$ 的条件概率密度函数为：
  $$
  f_{Y|X \in A}(y) = \frac{P(Y \leq y, X \in A)}{P(X \in A)}
  $$

- **条件分布函数**：
  $$
  F_{Y|X \in A}(y) = P(Y \leq y | X \in A)
  $$

### 5.2 条件数学期望
- 在给定 $X \in A$ 的条件下， $Y$ 的条件期望定义为：
  $$
  E[Y | X \in A] = \int_{-\infty}^\infty y f_{Y|X \in A}(y) \, dy
  $$
  要求绝对收敛。

---

## 常见二维分布

### 5.1 二维均匀分布
- **定义**：称 $(X,Y) \sim U(D)$ ，若其联合概率密度函数为：
  $$
  f(x,y) = 
  \begin{cases} 
  \frac{1}{|D|}, & (x,y) \in D \\
  0, & \text{其它}
  \end{cases}
  $$
- 几何意义：落在子区域 $A \subset D$ 的概率为：
  $$
  P((X,Y) \in A) = \frac{|A|}{|D|}
  $$

### 5.2 二维正态分布
- **定义**： $(X,Y) \sim N(\mu_1, \mu_2, \sigma_1^2, \sigma_2^2, \rho)$ ，其联合密度函数为：
  $$
  f(x,y) = \frac{1}{2\pi\sigma_1\sigma_2\sqrt{1-\rho^2}} \exp\left(-\frac{Q(x,y)}{2(1-\rho^2)}\right)
  $$
  其中 $Q(x,y)$ 为二次型：
  $$
  Q(x,y) = \frac{(x-\mu_1)^2}{\sigma_1^2} - 2\rho\frac{(x-\mu_1)(y-\mu_2)}{\sigma_1\sigma_2} + \frac{(y-\mu_2)^2}{\sigma_2^2}
  $$

- **性质**：
  - $X \sim N(\mu_1, \sigma_1^2), Y \sim N(\mu_2, \sigma_2^2)$ 。
  - 相关系数 $\rho = \frac{Cov(X,Y)}{\sqrt{DX \cdot DY}}$ 。
  - $X$ 与 $Y$ 独立 $\iff \rho = 0$ 。

---

## 示例与推导

### 示例 1：联合分布密度
- 设 $(X,Y)$ 的概率密度为：
  $$
  f(x,y) = 
  \begin{cases} 
  6x, & 0 \leq y \leq x \leq 1 \\
  0, & \text{其它}
  \end{cases}
  $$
  则：
  $$
  P(X+Y \leq 1) = \int_0^1 \int_0^{1-x} 6x \, dy \, dx = \frac{1}{4}
  $$

### 示例 2：条件密度
- 设 $(X,Y)$ 的概率密度为：
  $$
  f(x,y) = 
  \begin{cases} 
  8xy, & 0 \leq x \leq y \leq 1 \\
  0, & \text{其它}
  \end{cases}
  $$
  则：
  - 边缘分布密度：
    $$
    f_X(x) = 4x(1-x^2), \quad f_Y(y) = 4y^3
    $$
  - 条件密度：
    $$
    f_{X|Y}(x|y) = \frac{8xy}{4y^3} = 2x/y^2, \quad 0 \leq x \leq y
    $$
