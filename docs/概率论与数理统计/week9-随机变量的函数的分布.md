---
title: week9-随机变量的函数的分布
tags:
  - 概率论
categories: 
date: 2025-04-15T22:47:26+08:00
modify: 2025-04-15T22:47:26+08:00
dir: 
share: false
cdate: 2025-04-15T22
mdate: 2025-04-15T22
---


##  随机变量的函数的分布

### 一维情形
- **定义**  
  设随机变量 $X$ 的概率密度函数为 $f(x)$，计算其函数 $Y = g(X)$ 的概率密度函数时，首先考虑 $Y$ 的分布函数：
  $$
  P(Y \leq y) = P(g(X) \leq y) = \int_{g^{-1}(-\infty, y]} f(x) dx
  $$
  然后对 $y$ 求导即可得到 $Y$ 的密度函数。

- **关键推导**  
  - 示例：若 $X \sim N(0,1)$，且 $g(x) = x^2$，则 $Y = X^2$ 的分布函数为：
    $$
    P(Y \leq y) = P(X^2 \leq y) = P(-\sqrt{y} \leq X \leq \sqrt{y}) = \Phi(\sqrt{y}) - \Phi(-\sqrt{y})
    $$
    其中 $\Phi(x)$ 是标准正态分布的累积分布函数。
  - 对 $y$ 求导可得 $Y$ 的密度函数：
    $$
    f_Y(y) = \frac{d}{dy} P(Y \leq y) = \frac{1}{\sqrt{2\pi}} e^{-y/2}, \quad y \geq 0
    $$

- **结论**  
  $Y$ 的密度函数在实数轴上可以写为：
  $$
  f_Y(y) = I_{ [0,\infty)}(y) \cdot \frac{1}{\sqrt{2\pi}} e^{-y/2}
  $$

---

### 二维情形
#### 单个函数
- **定义**  
  若 $(X, Y)$ 的联合密度函数为 $f(x, y)$，计算 $Z = g(X, Y)$ 的密度函数时，先求分布函数：
  $$
  P(Z \leq z) = P(g(X, Y) \leq z) = \iint_{g(x, y) \leq z} f(x, y) dx dy
  $$
  再对 $z$ 求导。

#### 两个函数
- **定理**  
  若 $X_1$ 和 $X_2$ 的联合密度函数为 $f(x_1, x_2)$，通过双射变换 $T: (x_1, x_2) \to (y_1, y_2)$，则 $Y_1$ 和 $Y_2$ 的联合密度函数为：
  $$
  f_{Y_1, Y_2}(y_1, y_2) = f_{X_1, X_2}(x_1, x_2) \cdot |J|
  $$
  其中 $J$ 是雅可比行列式：
  $$
  J = \begin{vmatrix}
  \frac{\partial x_1}{\partial y_1} & \frac{\partial x_1}{\partial y_2} \\
  \frac{\partial x_2}{\partial y_1} & \frac{\partial x_2}{\partial y_2}
  \end{vmatrix}
  $$

- **示例**  
  设 $Z = aX + bY$，可以通过以下两种方法求解：
  1. **原理法**：直接积分：
     $$
     P(Z \leq z) = \iint_{ax + by \leq z} f(x, y) dx dy
     $$
  2. **变换公式法**：引入辅助变量 $W$，利用雅可比行列式计算。

---

### 特殊公式
- **和差积商公式**  
  若 $X$ 和 $Y$ 的联合密度为 $f(x, y)$，则：
  $$
  f_{aX+bY}(z) = \int_{-\infty}^\infty f\left(x, \frac{z - ax}{b}\right) \frac{1}{|b|} dx
  $$
  特别地，若 $X$ 和 $Y$ 独立，则卷积公式为：
  $$
  f_{X+Y}(z) = \int_{-\infty}^\infty f_X(x) f_Y(z-x) dx
  $$

- **最大值与最小值分布**  
  设 $M = \max(X_1, X_2, \dots, X_n)$，$N = \min(X_1, X_2, \dots, X_n)$，则可通过联合分布推导其分布函数。

---

##  特征函数及其性质

### 定义
- **特征函数**  
  对于任意随机变量 $X$，其特征函数定义为：
  $$
  \phi_X(\theta) = E [e^{i\theta X}]  = \int_{-\infty}^\infty e^{i\theta x} f(x) dx
  $$
  其中 $i = \sqrt{-1}$。

- **离散型随机变量**  
  若 $X$ 的分布为 $P(X = x_k) = p_k$，则：
  $$
  \phi_X(\theta) = \sum_k e^{i\theta x_k} p_k
  $$

- **连续型随机变量**  
  若 $X$ 的密度函数为 $f(x)$，则：
  $$
  \phi_X(\theta) = \int_{-\infty}^\infty e^{i\theta x} f(x) dx
  $$

- **示例**
  - $0$-$1$ 分布：$\phi_X(\theta) = pe^{i\theta} + q$
  - 正态分布 $N(\mu, \sigma^2)$：$\phi_X(\theta) = e^{i\mu\theta - \frac{1}{2}\sigma^2\theta^2}$

---

### 性质
- **简单性质**
  1. $|\phi_X(\theta)| \leq 1$，且 $\phi_X(0) = 1$。
  2. $\phi_X(\theta)$ 在 $\mathbb{R}$ 上一致连续。
  3. $\phi_X(-\theta) = \overline{\phi_X(\theta)}$（复共轭）。
  4. 若 $Y = aX + b$，则 $\phi_Y(\theta) = e^{i\theta b} \phi_X(a\theta)$。

- **重要性质**
  1. **独立和**：若 $X$ 和 $Y$ 独立，则：
     $$
     \phi_{X+Y}(\theta) = \phi_X(\theta) \phi_Y(\theta)
     $$
  2. **矩性质**：若 $E [|X|^k]  < \infty$，则：
     $$
     \phi_X(\theta) = \sum_{j=0}^k \frac{(i\theta)^j}{j!} E [X^j]  + o(\theta^k)
     $$
  3. **唯一性定理**：分布函数由特征函数唯一决定。
  4. **连续性定理**：分布收敛等价于特征函数点点收敛。

| 变量类型       | 特征函数公式                                                                 |
|----------------|------------------------------------------------------------------------------|
| 离散型         | $\phi_X(\theta) = \sum_k e^{i\theta x_k} p_k$                               |
| 连续型         | $\phi_X(\theta) = \int_{-\infty}^\infty e^{i\theta x} f(x) dx$              |
| 正态分布       | $\phi_X(\theta) = e^{i\mu\theta - \frac{1}{2}\sigma^2\theta^2}$             |

## 唯一性定理与连续性定理的应用

###  标准化随机变量的极限分布
- **关键概念**：标准化随机变量的极限分布。
    - 对于依赖于参数 $\lambda$ 的随机变量族 $X_\lambda \sim P(\lambda)$，其标准化随机变量为：
      $$
      \frac{X_\lambda - \lambda}{\sqrt{\lambda}}
      $$
    - 当 $\lambda \to \infty$，该标准化随机变量依分布收敛于标准正态分布 $N(0,1)$。

- **推导过程**：
    - 特征函数为：
      $$
      \phi_{\lambda}(\theta) = e^{-i\theta \lambda} \exp\left(\lambda (e^{i\theta / \sqrt{\lambda}} - 1)\right)
      $$
    - 展开后得：
      $$
      \phi_{\lambda}(\theta) \to \exp\left(-\frac{\theta^2}{2}\right), \quad \lambda \to \infty
      $$
    - 由唯一性定理和连续性定理可知：
      $$
      P\left(\frac{X_\lambda - \lambda}{\sqrt{\lambda}} \leq x\right) \to \Phi(x)
      $$
      其中 $\Phi(x)$ 是标准正态分布的分布函数。

###  线性组合的正态分布性质
- **关键概念**：独立正态随机变量的线性组合仍是正态分布。
    - 设 $X_1, X_2, \dots, X_n$ 独立且 $X_i \sim N(\mu_i, \sigma_i^2)$，则：
      $$
      X = a_1 X_1 + a_2 X_2 + \dots + a_n X_n + b \sim N\left(\sum_{i=1}^n a_i \mu_i + b, \sum_{i=1}^n a_i^2 \sigma_i^2\right)
      $$

---

##  随机向量的特征函数

###  定义与性质
- **定义**：设 $X = (X_1, X_2, \dots, X_m)^T$ 是一个 $m$ 维随机向量，$\theta = (\theta_1, \theta_2, \dots, \theta_m)^T$ 表示 $\mathbb{R}^m$ 中的实向量，则其特征函数为：
  $$
  \phi(\theta) = E [e^{i \theta^T X}]
  $$

- **性质**：
    - **混合矩公式**：
      若 $E [|X_1^{k_1} X_2^{k_2} \dots X_m^{k_m}|]  < \infty$，则：
      $$
      E [X_1^{k_1} X_2^{k_2} \dots X_m^{k_m}]  = (-i)^{k_1 + k_2 + \dots + k_m} \frac{\partial^{k_1 + k_2 + \dots + k_m} \phi(\theta)}{\partial \theta_1^{k_1} \partial \theta_2^{k_2} \dots \partial \theta_m^{k_m}} \bigg|_{\theta = 0}
      $$
    - **线性变换公式**：
      若 $Y = BX + b$，则：
      $$
      \phi_Y(\theta) = e^{i \theta^T b} \phi_X(B^T \theta)
      $$
    - **独立性判断**：
      随机向量 $X_1, X_2, \dots, X_m$ 相互独立的充要条件是：
      $$
      \phi_{X_1, X_2, \dots, X_m}(\theta_1, \theta_2, \dots, \theta_m) = \phi_{X_1}(\theta_1) \phi_{X_2}(\theta_2) \dots \phi_{X_m}(\theta_m)
      $$

---

##  多维 Gauss 分布

###  定义
- **多维 Gauss 分布的定义**：
    - 设 $Z_1, Z_2, \dots, Z_n$ 是独立的标准正态随机变量，若存在常数 $a_{ij}$ 和 $\mu_i$，使得：
      $$
      X_i = \sum_{j=1}^n a_{ij} Z_j + \mu_i, \quad i = 1, 2, \dots, m
      $$
      则称 $X = (X_1, X_2, \dots, X_m)^T$ 服从 $m$ 维 Gauss 分布。

- **等价定义**：
    - $m$ 维随机向量 $X$ 服从 Gauss 分布，当且仅当对于任意 $m$ 维向量 $a = (a_1, a_2, \dots, a_m)^T$，一维随机变量 $a^T X$ 要么是正态分布，要么是常数。

###  性质
- **特征函数**：
    - 若 $X \sim N(\mu, \Sigma)$，则其特征函数为：
      $$
      \phi(\theta) = \exp\left(i \theta^T \mu - \frac{1}{2} \theta^T \Sigma \theta\right)
      $$
    - 反之亦成立。

- **独立性条件**：
    - $X_1, X_2, \dots, X_m$ 相互独立的充要条件是协方差矩阵 $\Sigma$ 是对角型的。

- **联合概率密度**：
    - 若 $\det(\Sigma) > 0$，则 $X$ 的联合概率密度为：
      $$
      f(x) = \frac{1}{(2\pi)^{m/2} |\Sigma|^{1/2}} \exp\left(-\frac{1}{2} (x - \mu)^T \Sigma^{-1} (x - \mu)\right)
      $$
