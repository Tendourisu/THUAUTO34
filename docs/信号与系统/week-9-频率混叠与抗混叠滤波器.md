---
title: week-9-频率混叠与抗混叠滤波器
tags:
  - 信号与系统
categories: 
date: 2025-05-06T00:32:47+08:00
modify: 2025-05-06T00:32:47+08:00
dir: 
share: false
cdate: 2025-05-06T00
mdate: 2025-05-06T00
---

## week-9-频率混叠与抗混叠滤波器

### 关键概念
- **频率混叠**：当采样频率低于信号最高频率的2倍时，高频信号会“混叠”到低频区域，导致失真。数学表示为：  
  $f_s < 2f_{max}$（$f_s$为采样频率，$f_{max}$为信号最高频率）。  
- **抗混叠滤波器**：低通滤波器，用于在采样前限制信号带宽，确保$f_{max} \leq \frac{f_s}{2}$。

### 数学公式推导
- 采样信号的频谱是原始信号频谱的周期性重复：  
  $$F_r(\omega) = \frac{1}{T_s} \sum_{k=-\infty}^{\infty} F(\omega - k\omega_s)$$  
  其中$T_s$为采样间隔，$\omega_s = 2\pi f_s$为采样角频率。  
- 混叠条件：若$\omega_2 > \frac{\omega_s}{2}$，则$\omega_1 = \omega_s - \omega_2$会出现在基带中。

### 图表信息
| 符号       | 说明                   |
|------------|------------------------|
| $F_r(\omega)$ | 采样后信号的频谱       |
| $\omega_1$ | 基带频率分量           |
| $\omega_2$ | 高频混叠分量           |

### 代码示例（抗混叠滤波实现）
```python
import numpy as np
from scipy.signal import butter, lfilter

def antialiasing_filter(signal, cutoff, fs, order=5):
    nyquist = 0.5 * fs
    normal_cutoff = cutoff / nyquist
    b, a = butter(order, normal_cutoff, btype='low', analog=False)
    filtered_signal = lfilter(b, a, signal)
    return filtered_signal
```
**说明**：使用巴特沃斯低通滤波器限制信号带宽，避免混叠。

---

## 其他注意事项
- 实际工程中需权衡滤波器阶数（抑制混叠 vs. 相位延迟）。
- 采样定理（奈奎斯特准则）是信号处理的基础理论，需严格满足。
