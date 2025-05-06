---
title: week-11-LT与ZT性质总结
tags:
  - 信号与系统
categories: 
date: 2025-05-06T00:36:35+08:00
modify: 2025-05-06T00:36:35+08:00
dir: 
share: false
cdate: 2025-05-06T00
mdate: 2025-05-06T00
---

# LT与ZT性质变换总结 2

## 1. Laplace变换（LT）性质总汇

### 关键性质列表
| 性质名称        | 数学表达式                                                                            |
| --------------- | ------------------------------------------------------------------------------------- |
| 线性性          | $x [f (t)+k_f (t)] =k_f(t)+k_f^*(t)$                                                  |
| 时域微分        | $x\left [\frac{df (t)}{dt}\right] =sF(s)-f(0)$                                        |
| 高阶时域微分    | $x\left [\frac{d^n f (t)}{dt^n}\right] =\sum_{i=1}^{n}s^{n-i}f^{(i)}(0)$              |
| 时域积分        | $x\left [\int_{-s}^s f (t) dt\right] =\frac{F(s)}{s}+\frac{f^{(-1)}(0)}{s}$           |
| 时移（延时）    | $x [f (t-t_0)\mu (t-t_0)] =e^{-s t_0}F(s)$                                            |
| 频移（s域平移） | $x [e^{at}f (t)] =F(s-a)$                                                             |
| 尺度变换        | $x [f (at)] =\frac{1}{a}F\left(\frac{s}{a}\right), \ a>0$                             |
| 初值定理        | $\lim_{t \to 0^+} f(t)=\lim_{s \to \infty} sF(s)$                                     |
| 终值定理        | $\lim_{t \to \infty} f(t)=\lim_{s \to 0} sF(s)$                                       |
| 时域卷积        | $x [f_1 (t)*f_2 (t)] =F_1(s)F_2(s)$                                                   |
| 频域卷积        | $x [f_1 (t) f_2 (t)] =\frac{1}{2\pi j} \int_{c-j\infty}^{c+j\infty} F_1(p)F_2(s-p)dp$ |

---

## 2. LT微分特性详解

### 定理
若 $x [f (t)]  = F(s)$，则：
$$
x\left( \frac{d f(t)}{d t} \right) = sF(s) - f(0^-)
$$

### 证明
通过分部积分法：
$$
\begin{aligned}
x\left( \frac{d f(t)}{d t} \right) &= \int_{0^-}^{\infty} f'(t) e^{-st} dt \\
&= \left. f(t)e^{-st} \right|_{0^-}^{\infty} + s \int_{0^-}^{\infty} f(t)e^{-st} dt \\
&= -f(0^-) + sF(s)
\end{aligned}
$$

### 应用示例
**电感电压计算**  
已知电流 $i_L(t)$ 的LT为 $I_L(s)$，则电感电压 $v_L(t)=L \frac{di_L(t)}{dt}$ 的LT为：
$$
V_L(s) = sL I_L(s) - L i_L(0^-)
$$

---

## 3. LT卷积特性

### 定理
若因果信号 $f_1(t)$ 和 $f_2(t)$ 的LT分别为 $F_1(s)$ 和 $F_2(s)$，则：
$$
x [f_1 (t)*f_2 (t)]  = F_1(s)F_2(s)
$$

### 证明
通过交换积分顺序：
$$
\begin{aligned}
x [f_1 (t)*f_2 (t)]  &= \int_{0}^{\infty} \left( \int_{0}^{t} f_1(\tau)f_2(t-\tau) d\tau \right) e^{-st} dt \\
&= \int_{0}^{\infty} f_1(\tau) \left( \int_{\tau}^{\infty} f_2(t-\tau) e^{-st} dt \right) d\tau \\
&= F_1(s)F_2(s)
\end{aligned}
$$

### 应用示例
**单边斜变信号变换**  
$t \cdot u(t) = u(t)*u(t)$，其LT为：
$$
x [t \cdot u (t)]  = \frac{1}{s^2}
$$

---

## 4. 重要结论
- **ROC**：性质应用时需注意收敛域的变化。
- **因果性**：单边LT默认信号为因果信号（$t<0$时$f(t)=0$）。
- **联系与对比**：LT与ZT（Z变换）性质高度相似，可通过类比学习。
