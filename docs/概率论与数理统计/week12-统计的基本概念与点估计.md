---
title: week12-统计的基本概念与点估计
tags:
  - 数理统计
categories: 
date: 2025-05-13T21:00:35+08:00
modify: 2025-05-13T21:00:35+08:00
dir: 
share: false
cdate: 2025-05-13T21
mdate: 2025-05-13T21
---


## week12-统计的基本概念与点估计

### 1.1 总体和样本

-   **研究对象**: 某个（某些）数量指标。
-   **总体 (Population)**: 研究对象的全体。
-   **个体 (Individual)**: 总体中的每个单元。
-   **样本 (Sample)**: 从总体中抽取的一部分个体 $X_{1},X_{2},\cdot\cdot\cdot,X_{n}$。
-   **简单随机样本 (Simple Random Sample)**: 满足随机性（抽取机会均等）和独立性（各次抽取相互独立）的样本。
    -   **十分之一原则**: 当样本量 $n$ 与总体容量 $N$ 相比，若 $n/N \le 0.1$，不放回抽样可近似看作放回抽样。
-   **样本的联合分布函数**: 若总体分布函数为 $F(x)$，则容量为 $n$ 的简单随机样本 $X_{1},X_{2},\cdot\cdot\cdot,X_{n}$ 的联合分布函数为 $F(x_{1},\cdot\cdot\cdot,x_{n})=\prod_{i=1}^{n}F(x_{i})$。

### 1.2 统计量和经验分布函数

-   **统计量 (Statistic)**: 样本 $X_{1},X_{2},\cdot\cdot\cdot,X_{n}$ 的不含任何未知参数的函数 $T=T(X_{1},X_{2},\cdot\cdot\cdot,X_{n})$。
-   **顺序统计量 (Order Statistics)**: 将样本观测值 $x_{1},\cdot\cdot\cdot,x_{n}$ 按从小到大的顺序排列为 $X_{(1)}\le X_{(2)}\le...\le X_{(n)}$。
    -   **样本极差 (Sample Range)**: $R=X_{(n)}-X_{(1)} = \max\{X_{1},\cdot\cdot\cdot,X_{n}\}-\min\{X_{1},\cdot\cdot\cdot,X_{n}\}$。
    -   **样本中位数 (Sample Median)**:
        $X_{med}=\begin{cases}X_{(\frac{n+1}{2})},& \text{n 为奇数}\\ \frac{1}{2}[X_{(\frac{n}{2})}+X_{(\frac{n}{2}+1)}],& \text{n 为偶数}\end{cases}$
        (注：PDF中此处条件表述不清，已按标准定义给出。)
-   **经验分布函数 (Empirical Distribution Function)**:
    $F_{n}(x)=\frac{V_{n}(x)}{n}=\frac{1}{n}\{\text{样本 } X_{1},\cdot\cdot\cdot,X_{n} \text{ 中小于或等于x的个数}\}$
    $F_{n}(x)=\begin{cases}0,& x < X_{(1)}\\ \frac{k}{n},& X_{(k)}\le x < X_{(k+1)}, k=1,2,\cdot\cdot\cdot,n-1\\ 1,& x \ge X_{(n)}\end{cases}$
    (注：PDF中 $X_{(k)}<x\le X_{(k+1)}$，此处为常见形式。)
    -   $V_{n}(x)$ 是样本中小于等于 $x$ 的个数， $V_{n}(x)\sim B(n,F(x))$ (二项分布)。
    -   $E(F_{n}(x))=F(x)$
    -   $D(F_{n}(x))=\frac{F(x)(1-F(x))}{n}$
    -   **中心极限定理**: $\sqrt{n}[F_{n}(x)-F(x)]\xrightarrow{d} N(0,F(x)(1-F(x)))$
    -   **Glivenko-Cantelli 定理**: $sup_{x\in R}|F_{n}(x)-F(x)|\xrightarrow{a.s.}0$ (依概率1收敛)。
-   **常用统计量**:
    -   **样本均值 (Sample Mean)**: $\overline{X}=\frac{1}{n}\sum_{i=1}^{n}X_{i}$
    -   **样本方差 (Sample Variance)**: $S^{2}=\frac{1}{n-1}\sum_{i=1}^{n}(X_{i}-\overline{X})^{2}$
    -   **样本k阶原点矩 (Sample k-th Moment)**: $M_{k}=\frac{1}{n}\sum_{i=1}^{n}X_{i}^{k}$
    -   **样本修正方差 (Biased Sample Variance / MLE for variance under normality assumption)**: $S^{*^{2}}=\frac{1}{n}\sum_{i=1}^{n}(X_{i}-\overline{X})^{2}=M_{2}-M_{1}^{2}$

### 1.3 抽样分布 (Sampling Distribution)

统计量的概率分布称为抽样分布。

#### 顺序统计量的分布
假设总体的概率密度函数为 $f(x)$，分布函数为 $F(x)$。
1.  **第k顺序统计量 $X_{(k)}$ 的密度函数**:
    $f_{X_{(k)}}(x) = \frac{n!}{(k-1)!(n-k)!}[F(x)]^{k-1}[1-F(x)]^{n-k}f(x)$
2.  **$X_{(i)}$ 和 $X_{(j)}$ ($i<j$) 的联合密度函数 ($x \le y$)**:
    $f_{X_{(i)},X_{(j)}}(x,y) = \frac{n!}{(i-1)!(j-i-1)!(n-j)!}[F(x)]^{i-1}[F(y)-F(x)]^{j-i-1}[1-F(y)]^{n-j}f(x)f(y)$
    -   **特别地，$X_{(1)}$ 和 $X_{(n)}$ 的联合密度函数 ($x \le y$)**:
        $f_{X_{(1)},X_{(n)}}(x,y) = n(n-1)[F(y)-F(x)]^{n-2}f(x)f(y)$
    -   **样本极差 $R=X_{(n)}-X_{(1)}$ 的密度函数 ($r>0$)**:
        $f_{R}(r)=\int_{-\infty}^{\infty}n(n-1)[F(r+u)-F(u)]^{n-2}f(u)f(r+u)du$
        (注: PDF中使用积分下限0，这里给出更一般的形式，具体取决于 $u$ 的支撑域。)
3.  **所有顺序统计量 $(X_{(1)},X_{(2)},\cdot\cdot\cdot,X_{(n)})$ 的联合密度函数 ($x_{(1)}<x_{(2)}<\cdot\cdot\cdot<x_{(n)}$)**:
    $f_{X_{(1)},...,X_{(n)}}(x_{(1)},...,x_{(n)})=n!\prod_{i=1}^{n}f(x_{(i)})$

#### 样本中位数的渐近分布
若总体密度函数为 $f(x)$，中位数为 $x_{med}$，样本中位数为 $X_{med}$。
则 $X_{med}\dot{\sim}N(x_{med},\frac{1}{4n f^{2}(x_{med})})$ (当 $n \to \infty$)
(注: PDF中为 $1X_{med}$，应为 $X_{med}$。)

#### 样本分位数 (Sample Quantile)
样本 $p$-分位数 $X_p$ (例如 $X_{([np+1])}$ 当 $np$ 非整数时)。
则 $X_{p}\dot{\sim}N(x_{p},\frac{p(1-p)}{n f^{2}(x_{p})})$ (当 $n \to \infty$)
(注: PDF中 $X_p$ 的定义细节不完整，此处给出渐近分布。)

#### 常见统计量的性质
-   **样本均值 $\overline{X}$**:
    $E(\overline{X})=\mu$ (其中 $\mu=EX$)
    $D(\overline{X})=\frac{\sigma^{2}}{n}$ (其中 $\sigma^{2}=DX$) (注: PDF中为 $\sigma^2/2$，应为 $\sigma^2/n$)
-   **样本方差 $S^{2}$**:
    $ES^{2}=\sigma^{2}$
-   **样本k阶原点矩 $M_{k}$**:
    $EM_{k}=EX^{k}$
-   **样本修正方差 $S^{*^{2}}$**:
    $E(S^{*^{2}})=\frac{n-1}{n}\sigma^{2}$

### 1.4 三大抽样分布: $\chi^{2}$ 分布、$t$ 分布和 $F$ 分布

#### $\chi^2$ 分布 ($\chi^2(n)$)
-   **定义**: 若 $X_{1},X_{2},\cdot\cdot\cdot,X_{n}$ 独立同分布于 $N(0,1)$，则 $U=\sum_{i=1}^{n}X_{i}^{2} \sim \chi^{2}(n)$。
-   **与Gamma分布关系**: $\chi^{2}(n) = G(\frac{n}{2},\frac{1}{2})$ (形状参数 $n/2$，尺度参数 $1/2$ 或速率参数 $2$)
-   **性质**:
    -   $E(U)=n$
    -   $D(U)=2n$
    -   **可加性**: 若 $U_1 \sim \chi^2(n_1)$, $U_2 \sim \chi^2(n_2)$，且 $U_1, U_2$ 独立，则 $U_1+U_2 \sim \chi^2(n_1+n_2)$。

#### $t$ 分布 ($t(n)$)
-   **定义**: 若 $X\sim N(0,1)$, $Y\sim\chi^{2}(n)$，且 $X,Y$ 相互独立，则 $T=\frac{X}{\sqrt{Y/n}} \sim t(n)$。
-   **密度函数**: $f_{T}(x)=\frac{\Gamma(\frac{n+1}{2})}{\sqrt{n\pi}\Gamma(\frac{n}{2})}(1+\frac{x^{2}}{n})^{-\frac{n+1}{2}}, -\infty<x<+\infty$
    (注: PDF中指数项为正，应为负。)
-   **性质**:
    -   $n=1$: $t(1)$ 为标准柯西分布 $C(0,1)$，期望不存在。
    -   $n>1$: $ET=0$。
    -   $n>2$: $DT=\frac{n}{n-2}$。

#### $F$ 分布 ($F(m,n)$)
-   **定义**: 若 $X\sim\chi^{2}(m)$, $Y\sim\chi^{2}(n)$，且 $X,Y$ 相互独立，则 $F=\frac{X/m}{Y/n} \sim F(m,n)$。
-   **密度函数 ($x>0$)**: $f_{F}(x)=\frac{\Gamma(\frac{m+n}{2})(\frac{m}{n})^{\frac{m}{2}}}{\Gamma(\frac{m}{2})\Gamma(\frac{n}{2})}x^{\frac{m}{2}-1}(1+\frac{m}{n}x)^{-\frac{m+n}{2}}$
-   **性质**: 若 $W \sim F(m,n)$, 则 $\frac{1}{W} \sim F(n,m)$。

#### 分位数 (Quantile)
对随机变量 $X$，其 $\alpha$ 分位数 $v_{\alpha}$ 定义为 $P(X\le v_{\alpha})=F(v_{\alpha})=\alpha$。
常用 $\chi^2_{\alpha}(n)$, $t_{\alpha}(n)$, $F_{\alpha}(m,n)$ 分别表示相应分布的上 $\alpha$ 分位数，即 $P(X > v_{\alpha})=\alpha$。 (注：PDF中为下分位数定义，统计表中常用上分位数。)

### 1.5 正态总体样本均值和样本方差的分布

设 $X_{1},X_{2},\cdot\cdot\cdot,X_{n}$ 是来自正态总体 $N(\mu,\sigma^{2})$ 的简单随机样本。
$\overline{X}=\frac{1}{n}\sum_{i=1}^{n}X_{i}$， $S^{2}=\frac{1}{n-1}\sum_{i=1}^{n}(X_{i}-\overline{X})^{2}$。

#### 主要定理和性质
1.  $\overline{X}\sim N(\mu, \frac{\sigma^{2}}{n})$。
    -   标准化: $Z=\frac{\overline{X}-\mu}{\sigma/\sqrt{n}}\sim N(0,1)$。
2.  $\sum_{i=1}^{n}(\frac{X_{i}-\mu}{\sigma})^{2}\sim\chi^{2}(n)$。
3.  $\frac{(n-1)S^{2}}{\sigma^{2}}\sim\chi^{2}(n-1)$。
4.  $\overline{X}$ 与 $S^{2}$ 相互独立 (Cochran定理的特例)。
5.  $T=\frac{\overline{X}-\mu}{S/\sqrt{n}}\sim t(n-1)$。
6.  若有两独立正态总体 $N(\mu_1, \sigma_1^2)$ 和 $N(\mu_2, \sigma_2^2)$，样本量分别为 $n_1, n_2$，样本方差 $S_1^2, S_2^2$。
    -   若 $\sigma_1^2 = \sigma_2^2 = \sigma^2$ (未知)，则 $\frac{(\overline{X_1}-\overline{X_2})-(\mu_{1}-\mu_{2})}{S_{w}\sqrt{\frac{1}{n_{1}}+\frac{1}{n_{2}}}}\sim t(n_{1}+n_{2}-2)$，其中 $S_{w}^{2}=\frac{(n_{1}-1)S_{1}^{2}+(n_{2}-1)S_{2}^{2}}{n_{1}+n_{2}-2}$ (合并方差)。
    -   $\frac{S_{1}^{2}/\sigma_{1}^{2}}{S_{2}^{2}/\sigma_{2}^{2}} = \frac{\sigma_{2}^{2}S_{1}^{2}}{\sigma_{1}^{2}S_{2}^{2}}\sim F(n_{1}-1,n_{2}-1)$。

#### 重要推论和性质证明摘要

-   **$\overline{X}$ 与 $S^{2}$ 的独立性证明思路**:
    构造 $n+1$ 维向量 $(\overline{X},X_{1}-\overline{X},X_{2}-\overline{X},\cdot\cdot\cdot,X_{n}-\overline{X})^{T}$，其服从多元正态分布。
    计算协方差 $Cov(\overline{X},X_{i}-\overline{X})=Cov(\overline{X},X_{i})-D(\overline{X})=\frac{\sigma^{2}}{n}-\frac{\sigma^{2}}{n}=0$。
    由于 $\overline{X}$ 与每个 $X_i - \overline{X}$ 不相关，且是正态分布，所以它们独立。 $S^2$ 是 $X_i - \overline{X}$ 的函数，因此 $\overline{X}$ 与 $S^2$ 独立。

-   **$\frac{(n-1)S^{2}}{\sigma^{2}}\sim\chi^{2}(n-1)$ 的推导 (Cochran 定理思路)**:
    $\sum_{i=1}^{n}(\frac{X_{i}-\mu}{\sigma})^{2} = \sum_{i=1}^{n}(\frac{X_{i}-\overline{X}+\overline{X}-\mu}{\sigma})^{2} = \sum_{i=1}^{n}(\frac{X_{i}-\overline{X}}{\sigma})^{2} + n(\frac{\overline{X}-\mu}{\sigma})^{2}$
    即 $\sum_{i=1}^{n}(\frac{X_{i}-\mu}{\sigma})^{2} = \frac{(n-1)S^{2}}{\sigma^{2}} + (\frac{\overline{X}-\mu}{\sigma/\sqrt{n}})^{2}$。
    左边 $\sim \chi^2(n)$。右边第二项 $(\frac{\overline{X}-\mu}{\sigma/\sqrt{n}})^{2} \sim \chi^2(1)$。
    由于 $\overline{X}$ 和 $S^2$ 独立，则 $\frac{(n-1)S^{2}}{\sigma^{2}}$ 和 $(\frac{\overline{X}-\mu}{\sigma/\sqrt{n}})^{2}$ 独立。
    根据 $\chi^2$ 分布的可加性逆定理 (若 $U_1 \sim \chi^2(k_1)$, $U_1+U_2 \sim \chi^2(k)$ 且 $U_1, U_2$ 独立, $k>k_1$, 则 $U_2 \sim \chi^2(k-k_1)$)。
    故 $\frac{(n-1)S^{2}}{\sigma^{2}}\sim\chi^{2}(n-1)$。
    -   **可加性逆定理证明**: 利用特征函数。若 $X\sim\chi^{2}(m), X+Y\sim\chi^{2}(m+n)$ 且 $X,Y$ 独立。
        $\varphi_{X}(\theta)=(\frac{1/2}{1/2-i\theta})^{m/2}$, $\varphi_{X+Y}(\theta)=(\frac{1/2}{1/2-i\theta})^{(m+n)/2}$。
        因独立性, $\varphi_{X+Y}(\theta)=\varphi_{X}(\theta)\varphi_{Y}(\theta)$, 故 $\varphi_{Y}(\theta)=(\frac{1/2}{1/2-i\theta})^{n/2}$, 此为 $\chi^2(n)$ 的特征函数。

-   **注**: 若总体为对称分布（方差存在），则 $\overline{X}$ 和 $S^{2}$ 不相关。对于正态总体，它们不仅不相关，而且独立。

#### 示例

1.  设总体 $X\sim N(\mu,\sigma^{2})$, 则 $E(S^{2})=\sigma^{2}$, $D(S^{2})=\frac{2\sigma^{4}}{n-1}$。

2.  设随机变量 $X\sim t(n) (n>1), Y=\frac{1}{X^{2}}$ , 则 $Y\sim F(1,n)$。
    * **解**: $X = \frac{Z_0}{\sqrt{Z_n/n}}$ 其中 $Z_0 \sim N(0,1)$, $Z_n \sim \chi^2(n)$ 独立。
        $Y = \frac{1}{X^2} = \frac{Z_n/n}{Z_0^2}$. 由于 $Z_0^2 \sim \chi^2(1)$,
        所以 $Y = \frac{Z_n/n}{Z_1/1}$ (令 $Z_1 = Z_0^2 \sim \chi^2(1)$)。此为 $F(n,1)$ 分布的定义。
        (注：PDF答案为 (D) $F(1,n)$。$F(1,n) = \frac{\chi^2(1)/1}{\chi^2(n)/n}$.
        $X^2 = \frac{Z_0^2}{Z_n/n} = \frac{\chi^2(1)/1}{\chi^2(n)/n} \cdot n = n \cdot F(1,n)$.
        So $Y = \frac{1}{X^2} = \frac{1}{n F(1,n)}$. This is not directly $F(1,n)$ or $F(n,1)$.
        Let's recheck: $X \sim t(n) \Rightarrow X^2 \sim F(1,n)$.
        If $X \sim t(n)$, then $X^2 = \frac{(N(0,1))^2}{(\chi^2(n)/n)} = \frac{\chi^2(1)}{\chi^2(n)/n} = n \cdot \frac{\chi^2(1)/1}{\chi^2(n)/n} = n \cdot F(1,n)$.
        So $Y = 1/X^2 = 1/(n F(1,n))$.
        However, a known property is: If $X \sim t(n)$, then $X^2 \sim F(1,n)$.
        Thus $Y = 1/X^2 = 1/F(1,n)$. Since $1/F(m,n) \sim F(n,m)$, then $Y \sim F(n,1)$.
        PDF 选项 (C) $Y\sim F(n,1)$ (D) $Y\sim F(1,n)$.
        The PDF example states: 设随机变量 $X\sim t(n)(n>1),Y=\frac{1}{X^{2}}$ ,则 (D) $Y\sim F(1,n)$
        This means $1/X^2 \sim F(1,n)$. This implies $X^2 \sim F(n,1)$.
        Standard result: If $T \sim t_k$, then $T^2 \sim F_{1,k}$. So $X^2 \sim F(1,n)$.
        Then $Y = 1/X^2 = 1/F(1,n) \sim F(n,1)$.
        The PDF's answer is (D) $Y \sim F(1,n)$, which means $1/X^2 \sim F(1,n)$. This is incorrect. The correct answer should be $Y \sim F(n,1)$. I will list the PDF's answer and note the discrepancy.
        **PDF Answer: (D) $Y\sim F(1,n)$ (Note: Standard result implies $X^2 \sim F(1,n)$, so $Y=1/X^2 \sim F(n,1)$.)**

3.  设 $X_{1},X_{2},\cdot\cdot\cdot,X_{20}$ 是来自总体 $X\sim N(0,\sigma^{2})$ 的简单随机样本,则统计量 $T = \sum_{i=1}^{10}(-1)^{i}X_{i}/\sqrt{\sum_{i=1}^{20}{X_{i}}^{2}}$ 服从的分布是 $t(10)$。
    * **PDF Answer: $t(10)$ (【C】 in PDF seems to refer to an option not fully transcribed here).**
        (注: 此题结论不标准，分子 $U = \sum_{i=1}^{10}(-1)^{i}X_{i} \sim N(0, 10\sigma^2)$. 分母的平方根 $V = \sqrt{\sum_{i=1}^{20}{X_{i}}^{2}} = \sigma \sqrt{W}$ where $W \sim \chi^2(20)$. $T = U/(\sigma\sqrt{W}) = (U/\sigma)/\sqrt{W}$. $U/\sigma \sim N(0,10)$. This is not $N(0,1)$. The result $t(10)$ would require specific structure not immediately apparent.)

4.  设总体X服从正态分布 $N(0,2^{2})$, 而 $X_{1},X_{2},\cdot\cdot\cdot,X_{n}$ 是来自总体X的简单随机样本,则随机变量 $Y=\frac{X_{1}^{2}+\cdot\cdot\cdot+X_{10}^{2}}{2(X_{11}^{2}+\cdot\cdot\cdot+X_{15}^{2})}$ 服从分布 $F(10,5)$。
    * **解**: $X_i \sim N(0, 2^2)$, so $X_i/2 \sim N(0,1)$, $(X_i/2)^2 = X_i^2/4 \sim \chi^2(1)$.
        Numerator $N_0 = \sum_{i=1}^{10}X_{i}^{2}$. $\sum_{i=1}^{10}(X_i/2)^2 = \frac{N_0}{4} \sim \chi^2(10)$, so $N_0 \sim 4\chi^2(10)$.
        Denominator $D_0 = \sum_{i=11}^{15}X_{i}^{2}$. $\sum_{i=11}^{15}(X_i/2)^2 = \frac{D_0}{4} \sim \chi^2(5)$, so $D_0 \sim 4\chi^2(5)$.
        $Y = \frac{4\chi^2_A(10)}{2 \cdot 4\chi^2_B(5)} = \frac{4 U_1}{8 U_2} = \frac{1}{2} \frac{U_1}{U_2}$ where $U_1 \sim \chi^2(10), U_2 \sim \chi^2(5)$.
        $Y = \frac{1}{2} \frac{\chi^2(10)/10 \cdot 10}{\chi^2(5)/5 \cdot 5} = \frac{1}{2} \frac{10 \cdot F_{num}}{5 \cdot F_{den}} = \frac{1}{2} \frac{10}{5} F(10,5) = F(10,5)$.
    * **PDF Answer: $[F(10,5)]$**

5.  设 $X_{1},X_{2},\cdot\cdot\cdot,X_{n+1}$ 是正态总体 $N(\mu,\sigma^{2})$ 的简单样本, $\overline{X}=\frac{1}{n}\sum_{i=1}^{n}X_{i}$ 和 ${S_{n}}^{2}=\frac{1}{n}\sum_{i=1}^{n}(X_{i}-\overline{X})^{2}$ (注意 $S_n^2$ 是分母为 $n$ 的样本方差)。
    1.  求 $(n-1)(X_{1}-\mu)^{2}/[\sum_{i=2}^{n}(X_{i}-\mu)^{2}]$ 的分布。
        * **解**: $(X_1-\mu)^2/\sigma^2 \sim \chi^2(1)$. $\sum_{i=2}^{n}(X_{i}-\mu)^{2}/\sigma^2 \sim \chi^2(n-1)$ (共 $n-1$ 项).
            假设 $X_1, ..., X_n$ 独立。
            Statistic = $\frac{(n-1)\sigma^2 (\chi^2(1)/1)}{\sigma^2 (\chi^2(n-1)/(n-1)) \cdot (n-1)} = \frac{(n-1) \chi^2_A(1)}{\chi^2_B(n-1)}$.
            This is $\frac{\chi^2_A(1)/1}{\chi^2_B(n-1)/(n-1)} = F(1,n-1)$.
        * **PDF Answer: $[F(1,n-1)]$**
    2.  求 $\frac{X_{n+1}-\overline{X}}{S_{n}}\sqrt{\frac{n-1}{n+1}}$ 的分布。
        * **解**: $X_{n+1}-\overline{X} \sim N(0, \sigma^2(1+\frac{1}{n})) = N(0, \sigma^2\frac{n+1}{n})$.
            $\frac{X_{n+1}-\overline{X}}{\sigma\sqrt{(n+1)/n}} \sim N(0,1)$.
            $S_n^2 = \frac{n-1}{n}S^2$, where $S^2 = \frac{1}{n-1}\sum_{i=1}^n (X_i-\overline{X})^2$.
            $\frac{(n-1)S^2}{\sigma^2} = \frac{n S_n^2}{\sigma^2} \sim \chi^2(n-1)$.
            Statistic $T = \frac{X_{n+1}-\overline{X}}{S_n \sqrt{\frac{n+1}{n-1}}} = \frac{(X_{n+1}-\overline{X}) / (\sigma\sqrt{\frac{n+1}{n}})}{\sqrt{(nS_n^2/\sigma^2)/(n-1)} \cdot \sqrt{n/(n-1)} \cdot S_n / (\sigma\sqrt{\frac{n+1}{n}})}$
            $T = \frac{(X_{n+1}-\overline{X})/(\sigma\sqrt{\frac{n+1}{n}})}{\sqrt{\frac{nS_n^2/\sigma^2}{n-1}}} = \frac{N(0,1)}{\sqrt{\chi^2(n-1)/(n-1)}} \sim t(n-1)$.
        * **PDF Answer: $[t(n-1)]$**

6.  设 $X_{1},X_{2},\cdot\cdot\cdot,X_{9}$ 是正态总体的简单样本,令 $Y_{1}=\frac{1}{6}\sum_{i=1}^{6}X_{i}$ , $Y_{2}=\frac{1}{3}\sum_{i=7}^{9}X_{i}$ (PDF: $\sum_{i=1}^{3}X_{6+i}$), $S^{2}=\frac{1}{2}\sum_{i=7}^{9}(X_{i}-Y_{2})^{2}$ 和 $Z=\sqrt{2}(Y_{1}-Y_{2})/S$. 试证 $Z\sim t(2)$.
    * **证明**: $Y_1 \sim N(\mu, \sigma^2/6)$, $Y_2 \sim N(\mu, \sigma^2/3)$.
        $Y_1 - Y_2 \sim N(0, \sigma^2/6 + \sigma^2/3) = N(0, \sigma^2/2)$.
        So $\frac{Y_1-Y_2}{\sigma/\sqrt{2}} \sim N(0,1)$.
        $S^2$ 是基于样本 $X_7, X_8, X_9$ (容量 $n_2=3$) 的样本方差。
        $\frac{(3-1)S^2}{\sigma^2} = \frac{2S^2}{\sigma^2} \sim \chi^2(3-1) = \chi^2(2)$.
        $Z = \frac{\sqrt{2}(Y_1-Y_2)}{S} = \frac{(Y_1-Y_2)/(\sigma/\sqrt{2})}{S/\sigma} = \frac{N(0,1)}{\sqrt{(2S^2/\sigma^2)/2}} = \frac{N(0,1)}{\sqrt{\chi^2(2)/2}} \sim t(2)$.
        Q.E.D.

