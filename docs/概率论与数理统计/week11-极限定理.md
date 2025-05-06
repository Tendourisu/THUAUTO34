---
title: week11-极限定理
tags:
  - 概率论
categories: 
date: 2025-05-06T00:39:37+08:00
modify: 2025-05-06T00:39:37+08:00
dir: 
share: false
cdate: 2025-05-06T00
mdate: 2025-05-06T00
---

## 第六章 极限定理

### §1 大数定律与依概率收敛

#### 1. 依概率收敛
- **定义**：随机变量序列 $\{X_n\}$ 依概率收敛于 $X$（记为 $X_n \overset{P}{\to} X$），若对任意 $\varepsilon > 0$：
  $$\lim_{n \to \infty} P(|X_n - X| \geq \varepsilon) = 0$$
- **示例**：独立同分布的 $\{\xi_n\} \sim U [0, a] $，则 $\max(\xi_1, \cdots, \xi_n) \overset{P}{\to} a$。

#### 2. 性质
- **性质1**（连续映射定理）：
  - 若 $X_n \overset{P}{\to} X$，$g(x)$ 连续，则 $g(X_n) \overset{P}{\to} g(X)$。
  - 线性运算：$aX_n + bY_n \overset{P}{\to} aX + bY$，$X_nY_n \overset{P}{\to} XY$。
- **性质2**：依概率收敛蕴含依分布收敛（$X_n \overset{P}{\to} X \Rightarrow X_n \overset{D}{\to} X$）。
- **性质3**：$X_n \overset{P}{\to} a$（常数）当且仅当 $X_n \overset{D}{\to} a$。

#### 3. 大数定律
- **定义**：$\{X_n\}$ 满足大数定律若：
  $$\frac{1}{n}\sum_{i=1}^n X_i - \frac{1}{n}\sum_{i=1}^n E X_i \overset{P}{\to} 0$$
- **Chebyshev大数定律**：
  - 条件：$\{X_n\}$ 两两不相关，方差一致有界（$D(X_i) \leq C$）。
  - **Chebyshev不等式**：对任意 $\varepsilon > 0$，$P(|X - E X| \geq \varepsilon) \leq \frac{D X}{\varepsilon^2}$。
  - **示例**：设 $E(X)=-2$，$E(Y)=2$，$D(X)=1$，$D(Y)=4$，$\rho_{XY}=-0.5$，则：
    $$P(|X + Y| \geq 6) \leq \frac{1 + 4 + 2 \times (-0.5) \times 2}{36} = \frac{1}{12}$$

- **Khintchine大数定律**：
  - 独立同分布序列 $\{X_n\}$ 满足 $\frac{1}{n}\sum_{i=1}^n X_i \overset{P}{\to} \mu$（$E X_i = \mu$）。
- **Bernoulli大数定律**：
  - $n$ 次独立试验中事件 $A$ 的频率 $\frac{\mu_n}{n} \overset{P}{\to} p$（$P(A)=p$）。

---

### §2 中心极限定理

#### 1. 核心概念
- **定义**：$\{X_n\}$ 满足中心极限定理若：
  $$\lim_{n \to \infty} P\left(\frac{\sum_{i=1}^n X_i - n\mu}{\sigma\sqrt{n}} \leq x\right) = \Phi(x)$$

#### 2. 主要定理
- **Levy-Lindeberg定理**：
  - 独立同分布 $\{X_n\}$ 满足 $E X_i = \mu$，$D X_i = \sigma^2 \neq 0$，则：
    $$S_n^* = \frac{\sum_{i=1}^n X_i - n\mu}{\sigma\sqrt{n}} \overset{D}{\to} N(0,1)$$
- **De Moivre-Laplace定理**：
  - 二项分布 $B(n,p)$ 的标准化形式收敛于标准正态分布：
    $$\lim_{n \to \infty} P\left(\frac{\mu_n - np}{\sqrt{np(1-p)}} \leq x\right) = \Phi(x)$$
  - **示例**：求 $n$ 使得 $P(0.74 < \frac{\mu_n}{n} < 0.76) \geq 0.95$（$p=0.75$）：
    - 解得 $n \approx 7203$（利用 $\Phi^{-1}(0.975) \approx 1.96$）。

- **Liapunov定理**：
  - 独立序列 $\{X_n\}$ 满足 Liapunov 条件时，标准化和收敛于 $N(0,1)$。

---

### 关键公式与表格
#### 1. 收敛类型对比
| 收敛类型       | 定义式                                                                 | 关系               |
|----------------|-----------------------------------------------------------------------|--------------------|
| 依概率收敛     | $\lim_{n \to \infty} P(|X_n - X| \geq \varepsilon) = 0$              | $\Rightarrow$ 依分布收敛 |
| 依分布收敛     | $\lim_{n \to \infty} F_{X_n}(x) = F_X(x)$（连续点）                  | 与常数收敛等价     |

#### 2. 大数定律对比
| 定理名称       | 条件                               | 结论                               |
|----------------|------------------------------------|------------------------------------|
| Chebyshev      | 两两不相关，方差有界               | $\frac{1}{n}\sum X_i - E X_i \overset{P}{\to} 0$ |
| Khintchine     | 独立同分布，$E X_i = \mu$          | $\frac{1}{n}\sum X_i \overset{P}{\to} \mu$      |
| Bernoulli      | 二项试验，$P(A)=p$                 | $\frac{\mu_n}{n} \overset{P}{\to} p$           |
