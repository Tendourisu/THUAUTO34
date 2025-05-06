---
title: week10-Brown运动的简单特性
tags:
  - 概率论
categories: 
date: 2025-05-06T00:28:52+08:00
modify: 2025-05-06T00:28:52+08:00
dir: 
share: false
cdate: 2025-05-06T00
mdate: 2025-05-06T00
---

##  Brown运动的简单特性

### 性质1：Brown运动的等价定义
- **定理**：随机过程 $\{B_t : t \geq 0\}$ 满足 $B_0 = 0$，则它是Brown运动当且仅当：
  - 是Gauss过程；
  - $EB_t = 0$；
  - $E(B_s B_t) = \min(s,t)$。
- **证明**：
  - **必要性**：若为Brown运动，则 $B_t \sim N(0,t)$，协方差计算：
    $$Cov(B_s, B_t) = E(B_s B_t) = s \land t.$$
  - **充分性**：验证独立增量与 $B_t - B_s \sim N(0, |t-s|)$。

### 性质2：不变性
1. **平移不变性**：$\{B_{t+a} - B_a, t \geq 0\}$ 是Brown运动。
   - 证明：$E [(B_{t+a} - B_a)(B_{s+a} - B_a)]  = \min(s,t)$。
1. **尺度不变性**：$\{\frac{B_{ct}}{\sqrt{c}}, t \geq 0\}$ 是Brown运动。
2. **时间反转**：$\{t B_{1/t}, t \geq 0\}$ 是Brown运动。

### Brown运动的轨道性质
- **性质3**：轨道处处连续但不可导。
- **性质4（镜面对称性）**：
  $$P(\text{到达过 } x, B_t \leq x) = P(\text{到达过 } x, B_t \geq x).$$
- **性质5（首达时分布）**：
  $$P(T_a \leq t) = 2(1 - \Phi(|a|/\sqrt{t})).$$

### 其他性质
- **性质6**：$\max_{0 \leq s \leq t} B_s$ 的密度为 $f(a) = \frac{2}{\sqrt{2\pi t}} e^{-a^2/(2t)}$。
- **性质7**：始于 $x$ 的Brown运动在 $(0,t)$ 有零点的概率：
  $$\int_0^t \frac{|x|}{u^{3/2}} e^{-x^2/(2u)} du.$$
- **性质8（反正弦律）**：
  $$P(\text{在 } (a,b) \text{无零点}) = \frac{2}{\pi} \arcsin \sqrt{a/b}.$$

---

## §1 大数定律与依概率收敛

### 1. 依概率收敛
- **定义**：$X_n \overset{P}{\to} X$ 若 $\forall \varepsilon > 0$，$\lim_{n \to \infty} P(|X_n - X| \geq \varepsilon) = 0$。
- **性质**：
  - 连续性：若 $X_n \overset{P}{\to} X$，$g$ 连续，则 $g(X_n) \overset{P}{\to} g(X)$。
  - Slutsky定理：若 $X_n \overset{D}{\to} X$，$Y_n \overset{P}{\to} a$，则：
    $$X_n + Y_n \overset{D}{\to} X + a, \quad X_n Y_n \overset{D}{\to} aX.$$

### 2. 大数定律（LLN）
- **定义**：$\frac{1}{n} \sum_{i=1}^n X_i - \frac{1}{n} \sum_{i=1}^n EX_i \overset{P}{\to} 0$。
- **Chebyshev大数定律**：若 $\{X_n\}$ 两两不相关且方差有界，则服从LLN。
- **Khintchine大数定律**：i.i.d.序列 $\{X_n\}$ 满足 $\frac{1}{n} \sum_{i=1}^n X_i \overset{P}{\to} \mu$。
- **Bernoulli大数定律**：$\frac{\mu_n}{n} \overset{P}{\to} p$（$\mu_n$为成功次数）。

---

## §2 中心极限定理（CLT）

### 1. Levy-Lindeberg CLT
- **定理**：i.i.d.序列 $\{X_n\}$ 满足 $EX_i = \mu$，$DX_i = \sigma^2$，则：
  $$\frac{\sum_{i=1}^n X_i - n\mu}{\sigma \sqrt{n}} \overset{D}{\to} N(0,1).$$

### 2. De Moivre-Laplace定理
- **推论**：$\mu_n \sim B(n,p)$，则：
  $$\frac{\mu_n - np}{\sqrt{np(1-p)}} \overset{D}{\to} N(0,1).$$
- **应用示例**：求试验次数 $n$ 使得频率在 $ [0.74, 0.76] $ 的概率 $\geq 0.95$：
  $$n \approx 7203 \quad (\text{解方程 } 0.01 \sqrt{n/(0.1875)} \approx 1.96).$$

### 3. Liapunov定理
- **条件**：$\lim_{n \to \infty} \frac{1}{B_n^{2+\delta}} \sum_{i=1}^n E|X_i - \mu_i|^{2+\delta} = 0$。
- **结论**：$\frac{1}{B_n} \sum_{i=1}^n (X_i - \mu_i) \overset{D}{\to} N(0,1)$。

---

## 关键公式总结
| 概念 | 公式 |
|------|------|
| Brown运动协方差 | $E(B_s B_t) = \min(s,t)$ |
| 首达时分布 | $P(T_a \leq t) = 2(1 - \Phi(|a|/\sqrt{t}))$ |
| De Moivre-Laplace | $\frac{\mu_n - np}{\sqrt{np(1-p)}} \approx N(0,1)$ |
