---
title: week1-概率与概率空间
tags:
  - 概率论
date: " 2025-03-08T19:32:02+08:00 "
modify: " 2025-03-08T19:32:02+08:00 "
share: false
cdate: " 2025-03-08 "
mdate: " 2025-03-08 "
math: "true"
---

# week1-概率与概率空间

## §1 引言
### 1.1 研究对象
- **确定性现象**：结果可预测（如自由落体运动）
- **随机现象**：结果不确定（如掷骰子）
- **核心目标**：研究随机现象的统计规律性

### 1.2 发展简史
| 时期      | 关键人物与贡献                                                   |
| --------- | ---------------------------------------------------------------- |
| 16-17世纪 | Pascal/Fermat研究赌博问题（得分问题、破产问题）                  |
| 1713年    | Bernoulli提出大数定律                                            |
| 1733年    | De Moivre推导正态分布公式：$\frac{n!}{n^n e^{-n} \sqrt{2\pi n}}$ |
| 1812年    | Laplace《概率的分析理论》完成概率论公理化过渡                    |
| 20世纪    | Kolmogorov建立概率公理化体系（1933年）                           |

---

## §2 随机事件及其概率
### 2.1 基本概念
#### 样本空间与事件
- **样本空间**（Ω）：所有可能结果的集合
- **事件**：Ω的子集，满足：
  ```text
  # 事件A发生当且仅当试验结果ω ∈ A
  ω ∈ A ⇨ 事件A发生
  ```

#### 事件运算关系表
| 关系 | 符号          | 概率论意义       | 集合论意义 |
| ---- | ------------- | ---------------- | ---------- |
| 包含 | $B \subset A$ | A发生则B必发生   | A是B的子集 |
| 对立 | $A^c$         | A不发生的事件    | 余集       |
| 互斥 | $AB = \phi$   | A与B不能同时发生 | 无公共元素 |

#### 事件运算律
- **对偶律**（De Morgan律）：
  $$
  (A \cup B)^c = A^c \cap B^c \\
  (A \cap B)^c = A^c \cup B^c
  $$

### 2.2 等可能概型
#### 古典概型
- **定义**：$P(A) = \frac{\#A}{\#\Omega}$
- **例1（摸球问题）**：

  $$
  袋中有α白球、β黑球，取a+b球，恰含a白b黑的概率：
  P = \frac{C_\alpha^a C_\beta^b}{C_{\alpha +\beta}^{a+b}}
  $$

#### 几何概型
- **定义**：$P(A) = \frac{L(A)}{L(\Omega)}$（L为测度）
- **例2（约会问题）**：

  两人在1小时内随机到达，会面成功的概率：
  
$$P=1-\frac{2 \times \frac{1}{2} \times 40^2}{60^2} = \frac{5}{9}$$  

### 2.3 悖论与问题
- **Bertrand悖论**：圆内随机弦长超过内接正三角形边长的概率存在多解（因"随机"定义不同）
- **Buffon投针问题**：
  针长l，平行线间距a(l < a)：
  $$
  P = \frac{2l}{\pi a}
  $$

---

## §3 概率空间及计算
### 3.1 事件域（σ-域）
- **定义**：满足：
  1. Ω ∈ ℱ
  2. $A \in ℱ \Rightarrow A^c \in ℱ$
  3. $A_1,A_2,... \in ℱ \Rightarrow \bigcup_{i=1}^\infty A_i \in ℱ$

### 3.2 概率公理化定义
- **Kolmogorov公理**：
  (Ω, ℱ, P) 满足：
  1. 非负性：P(A) ≥ 0
  2. 规范性：P(Ω) = 1
  3. 可数可加性：A_i 互斥时 $P(\bigcup A_i) = \sum P(A_i)$


### 3.3 概率性质
| 性质         | 公式                                                                           |
| ------------ | ------------------------------------------------------------------------------ |
| 逆事件概率   | $P(A^c) = 1 - P(A)$                                                            |
| 加法公式     | $P(A \cup B) = P(A) + P(B) - P(AB)$                                            |
| 一般加法公式 | $P(\bigcup A_i) = \sum P(A_i) - \sum P(A_iA_j) + ... + (-1)^{n+1}P(A_1...A_n)$ |

### 3.4 典型问题
**匹配数问题**：
$$
n个人随机取作业，无人匹配的概率：
q_0 = 1 - \frac{1}{1!} + \frac{1}{2!} - ... + (-1)^n \frac{1}{n!} \to \frac{1}{e}
$$

### 3.5 连续性定理
- **上/下极限**：
  $$
  \limsup A_n = \bigcap_{n=1}^\infty \bigcup_{k=n}^\infty A_k \\
  \liminf A_n = \bigcup_{n=1}^\infty \bigcap_{k=n}^\infty A_k
  $$
- **连续性**：若$A_n \uparrow A$，则$\lim_{n\to\infty} P(A_n) = P(A)$

---

## 附录：关键公式推导
### 古典概型组合数公式
$$
C(n, k) = \frac{n!}{k!(n-k)!} \\
P = \frac{\text{有利事件数}}{\text{总事件数}}
$$

### 几何概型面积计算
$$
平面区域Ω，事件A对应区域：
P(A) = \frac{\iint_A dxdy}{\iint_\Omega dxdy}
$$

### 事件序列极限
$$
\lim_{n\to\infty} P(A_n) = P(\lim_{n\to\infty} A_n) \quad \text{（当极限存在时）}
$$
