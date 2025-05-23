---
title: week8-1-放大电路中的反馈1
tags:
  - 模拟电子基础
categories: 
date: 2025-04-07T09:53:24+08:00
modify: 2025-04-07T09:53:24+08:00
dir: 
share: false
cdate: 2025-04-07T09
mdate: 2025-04-07T09
---
##  week8-1-放大电路中的反馈1


### 5.1 反馈的基本概念及判断方法

#### 关键概念
- **反馈**：将输出信号的一部分或全部通过特定电路形式作用到输入回路，影响输入量的措施。
- **正反馈与负反馈**：
  - 正反馈：反馈使输出信号的变化增大， $\Delta X_o \uparrow$ 。
  - 负反馈：反馈使输出信号的变化减小， $\Delta X_o \downarrow$ 。
- **直流反馈与交流反馈**：
  - 直流反馈：反馈量包含直流量，存在于直流通路。
  - 交流反馈：反馈量包含交流量，存在于交流通路。
- **局部反馈与级间反馈**：
  - 局部反馈：仅影响某一级放大电路。
  - 级间反馈：影响两级或多级放大电路。

#### 判断反馈的方法
- **瞬时极性法**：
  - 若反馈量 $X_f$ 的极性使净输入量 $X_i' = X_i - |X_f|$ 减小，则为负反馈。
  - 若反馈量 $X_f$ 的极性使净输入量 $X_i' = X_i + |X_f|$ 增大，则为正反馈。
- **电容的作用**：判断反馈网络中电容对直流通路和交流通路的影响。

#### 示例分析

| 输入信号 | 输出信号 | 反馈类型   |
|----------|----------|------------|
| uI       | uO       | 负反馈     |
| uI       | uO       | 正反馈     |


---

### 5.2 负反馈放大电路的四种基本组态

#### 四种组态
1. **电压串联负反馈**：
   - 反馈信号为电压，串联于输入端。
   - 特点：稳定输出电压，提高输入阻抗。
2. **电压并联负反馈**：
   - 反馈信号为电压，并联于输入端。
   - 特点：稳定输出电压，降低输入阻抗。
3. **电流串联负反馈**：
   - 反馈信号为电流，串联于输入端。
   - 特点：稳定输出电流，提高输入阻抗。
4. **电流并联负反馈**：
   - 反馈信号为电流，并联于输入端。
   - 特点：稳定输出电流，降低输入阻抗。

---

### 5.3 负反馈放大电路的表示方法

#### 反馈网络的表示
- **反馈系数 $F$ **：定义为反馈量与输出量的比值，即 $F = \frac{X_f}{X_o}$ 。
- **闭环增益 $A_f$ **：考虑反馈后的增益，公式为：
  $$
  A_f = \frac{A}{1 + AF}
  $$
  其中， $A$ 为开环增益， $AF$ 为环路增益。

---

### 5.4 深度负反馈放大电路放大倍数的估算

#### 深度负反馈条件
- 当 $|AF| \gg 1$ 时，称为深度负反馈。
- 在深度负反馈条件下，闭环增益近似为：
  $$
  A_f \approx \frac{1}{F}
  $$

#### 计算示例
```markdown
假设反馈系数 F = 0.1，开环增益 A = 1000，则闭环增益为：

A_f ≈ 1 / F = 1 / 0.1 = 10
```

---

### 5.5 负反馈对放大电路性能的影响

#### 主要影响
- **增益稳定性**：负反馈降低增益的敏感性。
- **非线性失真**：负反馈减少输出信号的非线性失真。
- **输入与输出阻抗**：根据反馈组态的不同，输入阻抗可能增加或减少，输出阻抗通常降低。
- **带宽扩展**：负反馈扩展放大电路的带宽。

---

### 5.6 负反馈放大电路的稳定性

#### 稳定性分析
- **相位裕度与增益裕度**：
  - 相位裕度：在增益为 1 时，相位距离 -180° 的差值。
  - 增益裕度：在相位为 -180° 时，增益距离 0 dB 的差值。
- **稳定性条件**：相位裕度 > 0° 或增益裕度 > 0 dB。

#### 波特图示例

| 频率范围 | 增益变化 | 相位变化 |
|----------|----------|----------|
| fL       | 0 dB     | -90°     |
| fH       | -20 dB   | -180°    |

---

## 第四章：放大电路的频率响应

### 4.1 单管放大电路的频率响应

#### 关键概念
- **频率响应**：放大电路对不同频率信号的增益特性。
- **幅频特性**：增益随频率变化的关系。
- **相频特性**：相位随频率变化的关系。
- **上限频率 $f_H$ ** 和 **下限频率 $f_L$ **：分别定义为增益下降到中频增益的 0.707 倍时的频率。

#### 截止频率公式
$$
f_L = \frac{1}{2\pi (R_b + r_{be}) C_1}, \quad f_H = \frac{1}{2\pi R_L C_\pi'}
$$

---

### 4.2 多级放大电路的频率响应

#### 总体频率特性
- 总增益为各级增益的乘积：
  $$
  A_u = \prod_{k=1}^n A_{uk}
  $$
- 总截止频率为各级截止频率的叠加：
  $$
  f_L \approx 1.1 \sqrt{\sum_{k=1}^n f_{Lk}^2}, \quad f_H \approx \frac{1}{1.1} \sqrt{\sum_{k=1}^n \frac{1}{f_{Hk}^2}}
  $$

#### 波特图示例

| 频率范围 | 增益变化 | 相位变化 |
|----------|----------|----------|
| fL1      | 0 dB     | -90°     |
| fH1      | -20 dB   | -180°    |


---

### 数学推导与公式

#### 增益带宽积
- 定义：增益与带宽的乘积为常数。
- 公式：
  $$
  GBW = A \cdot BW
  $$

#### 多级放大电路的总增益
- 总增益为各级增益的叠加（以对数形式表示）：
  $$
  20 \log |A_u| = \sum_{k=1}^n 20 \log |A_{uk}|
  $$

---

### 图表与表格

#### 表格：单管与多级放大电路的波特图对比

| 类型           | 下限频率 $f_L$ | 上限频率 $f_H$ | 增益带宽积 $GBW$ |
|----------------|----------------|----------------|------------------|
| 单管放大电路   | 15.1 Hz        | 70.3 MHz       | 常数             |
| 多级放大电路   | 13.2 Hz        | 73 MHz         | 常数             |


#### 图表：典型波特图

| 频率范围 | 增益变化 | 相位变化 |
|----------|----------|----------|
| fL       | 0 dB     | -90°     |
| fH       | -20 dB   | -180°    |

