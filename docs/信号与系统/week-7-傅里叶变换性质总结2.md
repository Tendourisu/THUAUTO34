---
title: week-7-傅里叶变换性质总结2
tags:
  - 傅里叶变换
  - 信号与系统
categories: 
date: 2025-04-07T09:58:37+08:00
modify: 2025-04-07T09:58:37+08:00
dir: 
share: false
cdate: 2025-04-07T09
mdate: 2025-04-07T09
---
# 傅里叶变换性质总结

## 1. 傅里叶变换的基本性质
傅里叶变换的性质揭示了信号在时域和频域之间的关系。这些性质不仅简化了傅里叶变换及其逆变换的求解，还对信号分析提供了深刻的物理意义。

### 1.1 核心思想
- **时域与频域的对称性**：信号经过某种运算（如时移、尺度变换、卷积等）后，其频谱会发生相应变化。
- **核心内容**：
  - 时域运算 → 频域变化
  - 频域运算 → 时域影响

数学公式推导的核心工具包括：
$$
F(\omega) = \int_{-\infty}^{\infty} f(t)e^{-j\omega t} dt
$$
$$
f(t) = \frac{1}{2\pi} \int_{-\infty}^{\infty} F(\omega)e^{j\omega t} d\omega
$$

---

## 2. 傅里叶变换的主要性质

### 2.1 线性性质
#### 定义
若 $ \mathcal{F}[f_1 (t)] = F_1 (\omega) $ 和 $ \mathcal{F}[f_2 (t)] = F_2 (\omega) $，则：
$$
\mathcal{F}[a f_1(t) + b f_2(t)] = a F_1(\omega) + b F_2(\omega)
$$

#### 示例
- 单位阶跃信号 $ u (t) $ 的频谱：
$$
\mathcal{F}[u(t)] = \frac{1}{j\omega} + \pi \delta(\omega)
$$

---

### 2.2 尺度变换性质
#### 定义
若 $\mathcal{F}[f (t)] = F (\omega)$，则：
$$
\mathcal{F}[f(at)] = \frac{1}{|a|} F\left(\frac{\omega}{a}\right), \quad a \neq 0
$$

#### 物理意义
- 时间轴压缩 → 频率轴扩展
- 时间轴拉伸 → 频率轴压缩

#### 公式推导
通过变量替换 $x = at$，可得：
$$
\mathcal{F}[f(at)] = \int_{-\infty}^{\infty} f(at)e^{-j\omega t} dt = \frac{1}{|a|} \int_{-\infty}^{\infty} f(x)e^{-j\omega x/a} dx
$$

---

### 2.3 时移性质
#### 定义
若 $\mathcal{F}[f (t)] = F (\omega)$，则：
$$
\mathcal{F}[f(t-t_0)] = F(\omega)e^{-j\omega t_0}
$$

#### 特点
- 幅度谱不变
- 相位谱增加线性相位因子 $e^{-j\omega t_0}$

---

### 2.4 频移性质
#### 定义
若 $\mathcal{F}[f (t)] = F (\omega)$，则：
$$
\mathcal{F}[f(t)e^{j\omega_0 t}] = F(\omega - \omega_0)
$$

#### 示例
- 调制信号 $f (t)\cos (\omega_0 t)$ 的频谱：
$$
\mathcal{F}[f(t)\cos(\omega_0 t)] = \frac{1}{2}[F(\omega+\omega_0) + F(\omega-\omega_0)]
$$

---

### 2.5 微分性质
#### 定义
若 $\mathcal{F}[f (t)] = F (\omega)$，则：
$$
\mathcal{F}\left[\frac{d^n f(t)}{dt^n}\right] = (j\omega)^n F(\omega)
$$

#### 推广
频域微分：
$$
\mathcal{F}[-jt f(t)] = \frac{dF(\omega)}{d\omega}
$$

---

### 2.6 积分性质
#### 定义
若 $\mathcal{F}[f (t)] = F (\omega)$，则：
$$
\mathcal{F}\left[\int_{-\infty}^{t} f(\tau)d\tau\right] = \frac{F(\omega)}{j\omega} + \pi F(0)\delta(\omega)
$$

---

### 2.7 卷积定理
#### 定义
若 $\mathcal{F}[f_1 (t)] = F_1 (\omega)$ 和 $\mathcal{F}[f_2 (t)] = F_2 (\omega)$，则：
$$
\mathcal{F}[f_1(t) * f_2(t)] = F_1(\omega)F_2(\omega)
$$

#### 应用
- 系统输出 $y (t) = x (t) * h (t)$ 的频域表示：
$$
Y(\omega) = X(\omega)H(\omega)
$$

---

## 3. 傅里叶变换的应用

### 3.1 信号的能量守恒（Parseval 定理）
$$
\int_{-\infty}^{\infty} |f(t)|^2 dt = \frac{1}{2\pi} \int_{-\infty}^{\infty} |F(\omega)|^2 d\omega
$$

### 3.2 周期信号的傅里叶变换
周期信号 $f_p (t)$ 可以表示为：
$$
f_p(t) = \sum_{n=-\infty}^{\infty} c_n e^{jn\omega_0 t}
$$
其傅里叶变换为：
$$
F(\omega) = 2\pi \sum_{n=-\infty}^{\infty} c_n \delta(\omega - n\omega_0)
$$

---

## 4. 示例与图表

### 4.1 示例代码
```python
# 计算单位阶跃信号的傅里叶变换
from sympy import symbols, fourier_transform, Heaviside

t, w = symbols('t w')
u_t = Heaviside(t)
F_w = fourier_transform(u_t, t, w)
print(F_w)
```

### 4.2 表格示例
| 信号运算 | 时域表达式                   | 频域表达式                         |
| ---- | ----------------------- | ----------------------------- |
| 时移   | $f (t-t_0)$             | $F (\omega) e^{-j\omega t_0}$ |
| 频移   | $f (t) e^{j\omega_0 t}$ | $F (\omega-\omega_0)$         |
| 卷积   | $f_1 (t)*f_2 (t)$       | $F_1 (\omega) F_2 (\omega)$   |

---

