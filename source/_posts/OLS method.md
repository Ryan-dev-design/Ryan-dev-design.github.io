---
layout: posts
title: OLS 
date: 2022-04-18
categories: 学习笔记
tags: [经济,]

---

<head>
    <script src="https://cdn.mathjax.org/mathjax/latest/MathJax.js?config=TeX-AMS-MML_HTMLorMML" type="text/javascript"></script>
    <script type="text/x-mathjax-config">
        MathJax.Hub.Config({
            tex2jax: {
            skipTags: ['script', 'noscript', 'style', 'textarea', 'pre'],
            inlineMath: [['$','$']]
            }
        });
    </script>
</head>

# 简单回归模型

$y=\beta_0+\beta_1 x+u$

$x$ 和$u$ 的相关性？

关键假定是，$u$ 的平均值与$x$ 无关，即$\mathbb{E}[u\vert x]=\mathbb{E}u$，称之为**均值独立**

$\mathbb{E}[u\vert x]=\mathbb{E}u=0$ 称之为零条件均值假定，等于$0$定义了截距

$\mathbb{E}[y\vert x]=\beta_0+\beta_1x$ 总体回归函数

## 普通最小二乘法的推导

$$
\\mathbb{E}[y-\beta_1x-\beta_0]=0\\\\\mathbb{E}[x(y-\beta_1x-\beta_0)]=0
$$

利用零条件均值假定，以及矩估计，或者使残差平方和最小，即可获得OLS一阶条件

$$
\begin{align*}\sum y_i-\hat{\beta_0}-\hat{\beta_1}x_i=0\\\\\sum x_i(y_i-\hat{\beta_0}-\hat{\beta_1}x_i)=0\end{align*}
$$

OLS回归线/样本回归函数：$\hat{y}=\hat{\beta_0}+\hat{\beta_1}x$，是总体回归函数的一个样本估计，总体回归函数始终是未知的。

## 统计量的性质

$\sum \hat{u}_i=0$, $\sum x_i\hat{u}_i=0$ 这其实就是一阶条件

定义：

总平方和SST，解释平方和SSE，残差平方和SSR

$SST=\sum(y_i-\bar{y})^2$

$SSE=\sum (\hat{y}_i-\bar{y})^2$

$SSR=\sum \hat{u}_i^2$

SST=SSE+SSR

拟合优度$R^2=SSE/SST$，是可解释的波动与总波动之比

## OLS估计量的期望和方差

### OLS的无偏性

**SLR.1** 线性与参数

**SLR.2** 随机抽样，实践过程中，并不是所有横截面样本都可以看成是随机抽样的结果

$y_i=\beta_0+\beta_1x_i+u_i$，其中$u_i$是第$i$ 次观测的误差或干扰，与残差不同 

**SLR.3** 解释变量的样本有波动

$x$ 的样本结果不是完全相同的数值

**SLR.4** 零条件均值

**下面证明OLS的无偏性**

$\hat{\beta}_1=\frac{\sum(x_i-\bar{x})y_i}{\sum(x_i-\bar{x})^2}=\frac{\sum(x_i-\bar{x})y_i}{SST_x}=\frac{\sum(x_i-\bar{x})(\beta_0+\beta_1x_i+u_i)}{SST_x}=\beta_1+\frac{\sum d_iu_i}{SST_x}$，其中$d_i=x_i-\bar{x}$

因此，$\mathbb{E}\hat{\beta}_1=\beta_1,\mathbb{E}\hat{\beta}_0=\beta_0$

无偏性是抽样分布的性质，并不能确定从特定样本中得到的估计值

时序分析中将会放松SLR.2

**SLR.5** 同方差性

$Var(u\vert x)=\sigma^2$

$\sigma^2=\mathbb{E}[u^2\vert x]$，即$\sigma^2$是$u$的无条件方差，也经常被成为误差方差或干扰方差

若$Var(u\vert x)$取决于$x$，则误差项表现出异方差性

**定理 OLS估计量的抽样方差**

在SLR.1-SLR.5条件下，对于样本值：

$Var(\hat{\beta}_1)=\frac{\sigma^2}{SST_x}$

$Var(\hat{\beta}_0)=\frac{\sigma^2\bar{x}}{SST_x}$

从$\hat{\beta}_1=\beta_1+\frac{\sum d_iu_i}{SST_x}$出发，$Var(\hat{\beta}_1)=\frac{\sum d_i^2\sigma^2}{SST_x^2}=\sigma^2/SST_x$

一个小结论：

$\sum x_i^2\ge\sum(x_i-\bar{x})^2$

**误差方差的估计**

$\hat{u}_i=u_i-(\hat{\beta}_0-\beta_0)-(\hat{\beta}_1-\beta_1)x_i$

$\sigma^2$的一个无偏“估计量”是$\sum u_i^2/n$ 但$u_i$不可观测

OLS有两个约束条件，因此：

$\hat{\sigma}^2=SSR/(n-2)$ 是一个无偏估计，有时记为$s^2$

$$
0=\bar{u}-(\hat{\beta}_0-\beta_0)-(\hat{\beta}_1-\beta_1)\bar{x}\\\\\sum\hat{u}_i^2=\sum(u_i-（\hat{\beta}_0-\beta_0)-(\hat{\beta}_1-\beta_1)x_i)^2\\\\=\sum(u_i-\bar{u}-(\hat{\beta}_1-\beta_1)(x_i-\bar{x}))^2
$$

$sd(\hat{\beta}_1)=\sigma/\sqrt{SST}$它的一个比较自然的估计量就是$se(\hat{\beta}_1)=\hat{\sigma}/\sqrt{SST}$，被称之为标准误(standard error)

# 多元回归分析：估计

## 如何得到OLS估计值

一阶条件：

$$
\sum(y\_i-\hat{\beta}\_0-\hat{\beta}\_1x\_{i1}-\cdots)=0\\\\\sum x\_{i1}(y\_i-\hat{\beta}_0-\hat{\beta}\_1x\_{i1}-\cdots)=0\\\\\vdots\\\\\sum x\_{ik}(y\_i-\hat{\beta}\_0-\hat{\beta}\_1x\_{i1}-\cdots)=0
$$

回归线或样本回归函数由截距估计值与斜率估计值组成

估计值$\hat{\beta}_i$具有偏效应，因此多元回归使我们在对自变量的值不加限制的时候有效模拟施加限制的情况

## 拟合值和残差的重要性质

1. 残差样本平均值为零
2. OLS拟合值和OLS残差之间的样本协方差为零
3. 样本平均在回归线上

考虑$\hat{y}=\hat{\beta}\_0+\hat{\beta}\_1x_1+\hat{\beta}\_2x\_2$，$\hat{\beta}\_1$的一种表达形式是：$\hat{\beta}\_1=\frac{\sum\hat{r}\_{i1}y\_i}{\sum\hat{r}\_{i1}^2}$

其中$\hat{r}\_{i1} $是$x\_1$对$x\_2$的回归得到的OLS残差，即$x_{i1}$与$x_{i2}$中不相关的部分，所以$\hat{\beta}\_1$就是排除了$x\_2$影响后$y$与$x\_1$之间的关系

### 简单回归与多元回归

$\tilde{y}=\tilde{\beta}_0+\tilde{\beta}_1x_1$和$\hat{y}=\hat{\beta}_0+\hat{\beta}_1x_1+\hat{\beta}_2x_2$的结果会有什么关系？

令$\bar{\delta}$是$x_2$对$x_1$的简单回归斜率，则$\tilde{\beta}_1=\hat{\beta}_1+\hat{\beta}_2\bar{\delta}$

**拟合优度相关的内容和简单线性回归一致**

增加一个自变量之后$R^2$不会减小，而且通常会增大

## OLS估计量的期望

**MLR.1** 线性于参数

**MLR.2** 随机抽样

**MLR.3** 不存在完全共线性

**MLR.4** 条件均值为零

当MLR.4成立时，我们说具有外生解释变量，如果$x_j$与$u$相关，那么$x_j$称之为内生解释变量

限制了无法观测的因素与解释变量之间的关系

在MLR1-4条件下，可以证明OLS的无偏性$\mathbb{E}\hat{\beta}_i=\beta_i$

包含无关变量一般不会对OLS的无偏性产生影响，但是会对方差产生不利影响

**遗漏变量偏误**

总体模型：$y=\beta_0+\beta_1x_1+\beta_2x_2+\beta_3x_3+u$

遗漏变量后的估计模型：$\tilde{y}=\tilde{\beta}_0+\tilde{\beta}_1x_1+\tilde{\beta}_2x_2$

**假设$x_2$和$x_3$无关，$x_1$和$x_3$相关**

$$
\mathbb{E}\tilde{\beta}\_1=\beta\_1+\beta\_3\frac{\sum x\_{i3}(x\_{i1}-\bar{x}\_1)}{\sum (x\_{i1}-\bar{x}\_1)^2}
$$

**MLR.5** 同方差性 $Var[u\vert x_1,x_2,\dots,x_k]=\sigma^2$

即以解释变量为条件，不管解释变量出现怎样的组合，误差项的方差都是一样的。如果不成立称之为异方差性

MLR1-5称之为横截面回归的**高斯-马尔可夫**假定

$Var\hat{\beta}_i=\frac{\sigma^2}{SST_j(1-R_j^2)}$，其中$R_j$来自于$x_j$对其他变量回归得到的$R^2$，需要MLR.5的的成立

两个或多个自变量之间高度但不完全相关称之为**多重共线性**，即$R_j^2$接近于1，但这并不违反MLR.3，最终的问题还是要看$\hat{\beta}_j$与自身的标准差的大小关系

很小的$SST_j$也可以导致大方差，即小样本容量会导致很大的抽样方差

如果存在相关性的自变量和我们关注的自变量没有高度相关，其实没有直接影响，就不必关心这种共线性

误设模型中的方差

$Var\hat{\beta}_i=\frac{\sigma^2}{SST_j(1-R_j^2)}$，和$Var\tilde{\beta}_i=\frac{\sigma^2}{SST_j}$

若$\beta_2\neq0$，则简单模型给出方差更小的有偏估计；若$\beta_2=0$，则简单模型给出方差更小的无偏估计。

直觉上讲，如果$x_2$对$y$没有偏效应，在回归中加入$x_2$只会加剧多重共线性。如果$\beta_2\neq0$，则偏误不会随着样本容量扩大而减小，但是Var会随着样本容量增大而趋于零，因此增加自变量导致的多重共线性就会变得没那么重要，大样本情况下倾向使用更复杂的模型

### OLS估计的标准误

$$
\hat{\sigma}^2=\frac{\sum u_i^2}{n-k-1}=\frac{SSR}{n-k-1}
$$

自由度$df=n-k-1$

可以证明，$\mathbb{E}\hat{\sigma}^2=\sigma^2$

$\hat{\sigma}=\sqrt{\hat{\sigma}^2}$称之为回归标准误SER，是误差项的标准差的估计量，还被称之为估计值标准误和均方误差

$se(\hat{\beta}_i)=\frac{\hat{\sigma}^2}{\sqrt{SST_j(1-R_j)^2}}$

异方差性质不会导致参数估计偏误，但是会导致$Var(\hat{\beta}_j)$出现问题，导致标准误无效

## OLS的有效性

在MLR1-5的假定下，OKS估计量是最优线性无偏估计量BLUE，即具有最小的方差。尤其是MLR.5，保证了OLS在线性无偏估计量中具有最小的方差

# 多元回归分析：推断

## OLS估计量的抽样分布

**MLR.6** 正态性 总体误差$u$独立于解释变量，并且服从均值为零，方差为$\sigma^2$的正态分布

MLR1-6整治违经典线性模型（CLM）假定。在CLM下，OLS是最小方差的无偏估计，不必限制在线性估计中

由千于$u$ 是影响着 $y$ 而又观测不到的许多因素之和，所以我们可借助中心极限定理断定 $u$ 具有近似正态分布

通常我们可以利用某种变换得到一个$u$接近于正态的分布

误差项的正态性导致了OLS估计量的正态抽样分布

$$
\frac{\hat{\beta}_j-\beta_j}{sd(\hat{\beta}_j)}\sim Normal(0,1)
$$

## 对单个总体参数的检验：t检验

在CLM假定下，$\frac{\hat{\beta}\_j-\beta\_j}{se(\hat{\beta}\_j)}\sim t\_{n-k-1}$

多数应用中，主要兴趣在于检验原假设$H_0:\beta_j=0$

为什么不反过来写？因为$x_j$对$y$有偏效应的表述对$\beta_j$不为零对任何一个值都成立

$t_{\hat{\beta}_j}=\hat{\beta}_j/se(\hat{\beta}_j)$称之为t统计量

**单侧/双侧备择假设，t检验p值 ，置信区间**

参考概统知识，此处不表

## 检验关于参数的一个线性组合假设

$H_0:\beta_1=\beta_2$ 如何检验？

$t=\frac{\hat{\beta}_1-\hat{\beta}_2}{se(\hat{\beta}_1-\hat{\beta}_2)}$，关键是求解标准误，即要求解$Cov(\hat{\beta}_1,\hat{\beta}_2)$的一个估计值，这在数学上是复杂的

但我们可以改写模型$\beta_1=\theta_1+\beta_2$

$y=\beta_0+(\theta_1+\beta_2)x_1+\beta_2x_2+u=\beta_0+\theta_1x_1+\beta_2(x_1+x_2)+u$

直接检验$\theta_1$即可

## 对多个线性约束对检验：F检验

原假设：$H_0:\beta_{k-q+1}=0,\dots\beta_k=0$

不含$\beta_{\dots}$的模型是受约束模型，原始模型称之为不受约束模型

受约束模型增加了$q$个排除性约束，定义$F$统计量

$$
F=\frac{(SSR_r-SSR_{ur})/q}{SSR_{ur}/(n-k-1)}=\frac{(R_{ur}^2-R_r^2)/q}{(1-R_{ur}^2)/df_{ur}}\sim F_{q,n-k-1}
$$

其中$SSR_r$是受约束模型的残差平方和，$SSR_{ur}$是不受约束的残差平方和，$q=df_r-df_{ur}$

如果拒绝原假设，那么就说$x_{k-q+1},\dots x_k$ 在适当的显著性水平上是联合统计显著的

**对于一般的线性约束**

如指定了$\beta_1=1$，则将$x_1$挪到回归方程左边

由于两次的因变量不同，不能采用$R^2$形式的统计量

# 多元回归分析：OLS的渐进性

## 一致性

直观的理解：当样本量趋于无穷时，收敛到真值

**Theory OLS**的一致性

在MLR1-4下，$\hat{\beta}_j$是$\hat{\beta}_j$的一致估计

*PROOF*

$$
X\beta+u=y\\\\\hat{\beta}=(X^TX)^{-1}X^Ty=(X^TX)^{-1}X^T(X\beta+u)\\\\=\beta+(X^TX)^{-1}X^Tu=\beta+(\frac{1}{n}\sum_{i=1}^n x_i^Tx_i)^{-1}(\frac{1}{n}\sum _{i=1}^nx_i^Tu)
$$

according to the large number law:

$$
\frac{1}{n}\sum x_i^Tx_i\xrightarrow{p}\mathbb{E}x_i^Tx_i=A,\quad \frac{1}{n}\sum x_i^T u\xrightarrow{p}\mathbb{E}x_iu=0
$$

because $A$ is a nonsingular matrix, so$(\frac{1}{n}\sum x_i^Tx_i)^{-1}\xrightarrow{p}A^{-1}$

$$
plim \hat{\beta}=\beta+A^{-1}\cdot0=\beta
$$

**假设MLR.4’ 零均值和零相关**

对所有的$j$，都有$\mathbb{E}u=0$和$Cov(x_j,u)=0$

这是一个比MLR.4更弱的假定，它只要求每个$x_j$与$u$无关。

这导致$x_j$的非线性函数可能与误差相关

**OLS的不一致性**

如果误差与任何一个自变量相关，那么OLS就是有偏而不一致的估计。随着样本容量的增大，偏误将持续存在。

$$
plim \hat{\beta_1}-\beta_1=\frac{Cov(x_1,u)}{Var(x_1)}
$$

不一致性用总体的性质表示，而偏误则基于样本的对应量表示

## 渐近正态和大样本推断

**Theory** OLS的渐进正态性

在MLR1-5下，

1. 
$\sqrt{n}(\hat{\beta}\_j-\beta\_j)\xrightarrow x N(0,\sigma^2/a\_j^2),a\_j^2=plim(n^{-1}\sum_{i=1}^n \hat{r\_{ij}}^2)$，其中$\hat{r}\_{ij}$是$x\_j$对其余自变量回归得到的残差，即不能被其他变量解释的部分，我们称$\hat{\beta}\_j$是渐进正态分布的
2. $\hat{\sigma}^2$是$\sigma^2=Var(u)$的一个一致估计
3. 对于每个$j$都有$(\hat{\beta}_j-\beta_j)/sd(\hat{\beta}_j)\xrightarrow x N(0,1)$，且$(\hat{\beta}_j-\beta_j)/se(\hat{\beta}_j)\xrightarrow x N(0,1)$

去掉了MLR.6，只需要有限方差且零均值与同方差性质

总体分布恒定，与样本数量大小没有关系

$\hat{\beta}_j$的估计方差：$\hat{Var(\hat{\beta}_j)}=\frac{\hat{\sigma}^2}{SST_j(1-R_j^2)}$，以$1/n$的速度收缩至零

### 拉格朗日乘数LM统计量

1. 将$y$对施加限制后的自变量集回归，保存残差$\tilde{u}$
2. 将$\tilde{u}$对所有自变量进行回归，得到$R_u^2$
3. 计算$LM=nR_u^2$
4. 将LM与$\chi_q^2$分布中适当的临界值$c$比较，如果$LM>c$，则拒绝原假设，说明后$q$个变量的系数不为零

## OLS的渐近有效性

在模型$y=\beta_0+\beta_1x_1+u$中，在MLR.4假设下，$\mathbb{E}[u\vert x]=0$，我们关注斜率

令$z_i=g(x_i)$，$g$为任意函数，那么$u$就与$g(x)$无关。假定$Cov(z,x)\neq 0$，那么，估计量

$$
\tilde{\beta}_1=\sum(z_i-\bar{z})y_i/\sum (z_i-\bar{z})x_i
$$

是对$\beta_1$的一致估计。（证明：在分子分母分别除n并使用大数定律）

$$
plim \tilde{\beta_1}=\beta_1+Cov(z,u)/Cov(z,x)=\beta_1
$$

**Theory** OlS的渐近有效性

高斯-马尔可夫假设下，OLS估计量具有最小的渐近方差，

$$
Avar \sqrt{n}(\hat{\beta}_j-\beta_j)\le Avar\sqrt{n}(\tilde{\beta}_j-\beta_j)
$$

# 深入专题

## 数据测度单位对 OLS 统计量的影晌

度量单位对系数、标准误、置信区间、t统计量、F统计量的影响不会影响结果。

**$\beta$系数**

将所有变量都标准化后的回归结果得到的系数称为标准化系数或$\beta$系数 $\hat{b}_j=(\delta_j/\delta_y)\hat{\beta}_j$

由此得到的$\beta$系数大小更具有说服力

## 函数形式的进一步讨论

### 对数函数

$\log(y)=\hat{\beta}_0+\hat{\beta}_1\log x_1+\hat{\beta}_2x_2$

固定$x_1$不变，有$\Delta \hat{\log y}=\hat{\beta}_2 \Delta x_2$，即$\%\Delta\hat{y}=100\cdot[\exp(\hat{\beta}_2\Delta x_2)-1]$是精确的预测变化百分比，它是一致的，但却不是无偏的，因为指数函数的非线性

**对数的好处：**

1. 斜率系数不随测度单位而变化，所以我们可以忽略以对数形式出现的变量的度量单位
2. 严格为正的变量，条件分布常常具有异方差性或偏态性，取对数后可以降低
3. 对数通常可以缩小变量的取值范围，对极端值也没有那么敏感

**问题：**

1. 变量在0、1之间时，会导致变换后的数据绝对值很大
2. 更加难以预测原变量的值。两者的$R^2$也不具有可比性

### 含二次式的模型

一次项导致的变化表达式要重写，和变量本身也有关

### 含有交互项的模型

$y=\beta_0+\beta_1x_1+\beta_2x_2+\beta_3x_1x_2+u$$y=\beta_0+\beta_1x_1+\beta_2x_2+\beta_2x_1x_2+u$

此时$\beta_2$是$x_1=0$时$x_2$对$y$的偏效应，没什么意义

$y=\beta_0+\beta_1x_1+\beta_2x_2+\beta_3(x_1-\mu_1)(x_2-\mu_2)+u$

这样就是在均值处的偏效应了

## 拟合优度和回归元选择的进一步探讨

较小的$R^2$意味着误差方差相对$y$的方差太大了，以及我们很难精确地估计$\beta_j$，但大样本容量可以抵消较大的误差方差。

### 调整$R^2$

$R^2=1-\frac{SSR/n}{SST/n}$

总体$R^2$定义为$1-\sigma_u^2/\sigma_y^2$，这是$y$的变化在总体中可以用自变量解释的部分比例，是我们希望用$R^2$估计的值

但是用$SSR/n$估计$\sigma_u^2$是有偏的，用$\hat{\sigma}^2=SSR/(n-k-1)$显然更好，同理，用$SST/(n-1)$代替$SST/n$

由此，得到调整$R^2$：

$\bar{R^2}=1-\hat{\sigma}^2/[SST/(n-1)]=1-(1-R^2)\frac{n-1}{n-k-1}$

虽然两个无偏估计的比不是无偏估计，但是$\bar{R^2}$在模型中额外增加自变量时施加了惩罚，在回归中增加一个变量时，只有新变量的t统计量大于1，$\bar{R^2}$才会提高，增加一组变量时，联合检验显著的F统计量大于1才会提高

### 利用调整$R^2$在两个非嵌套模型 (nonnested) 中进行选择

Definition: 两个方程没有哪一个是另一个的特殊情形，所以它们是非嵌套模型

在这种情况下，使用普通$R^2$对自变量较少的模型不公平

当自变量组对应着不同的函数形式时，调整$R^2$也是有价值的

遗憾的是，**不能**通过拟合优度决定不同的因变量形式，因为它们的总变化是不同的，拟合的是两个完全不同的因变量

**回归分析中控制过多的因素**

注重对回归做其他条件不变的解释即可

**增加回归元以减少误差方差**

增加适当的无关变量可以减小误差方差，在大样本容量的情况下，所有OLS估计量对标准误都会减小

## 预测和残差分析

### 预测的置信区间

估计方程：$\hat{y}=\hat{\beta}_0+\hat{\beta}_1x_1+\hat{\beta}_2x_2+\dots$

$\theta_0=\beta_0+\beta_1c_1+\beta_2c_2+\dots$ 的估计量是：

$\hat{\theta}_0=\hat{\beta}_0+\hat{\beta}_1c_1+\hat{\beta}_2c_2+\dots$ 我们关注它的置信区间

在$df$较大的情况下，我们可以利用经验法则$\hat{\theta}_0\pm2\cdot se(\hat{\theta}_0)$构造95%置信区间

求$se(\hat{\theta}_0)$:

$\theta_0$表达式代入方程：$y=\theta_0+\beta_1(x_1-c_1)+\beta_2(x_2-c_2)+\dots$

用样本回归一下就可以了，截距项是预测值，还可以得到标准误

由于每个解释变量的样本均值都为零时，截距估计量的方差最小，所以当$x_j$都取均值时，预测值的方差最小。随着$c_j$的值离中心越来越远，误差越来越大

令$y^0$表示我们构造一个置信区间（预测区间）的估计值

$$
\hat{y}^0=\hat{\beta}_0+\hat{\beta}_1x_1^0+\cdots+\\\\\hat{e}^0=y^0-\hat{y}^0=\beta_0+\beta_1x_1^0+\cdots+u^0-\hat{y}^0\\\\\mathbb{E}\hat{e}^0=0
$$

所以预测误差的期望值为零

$u^0$与用来得到$\hat{\beta}_j$的样本方差不相关，$u^0$与每个$\hat{\beta}_j$都不相关，所以$u^0$与$\hat{y}^0$不相关

$$
Var(\hat{e}^0)=Var(\hat{y}^0)+Var(u^0)=Var(\hat{y}^0)+\sigma^2
$$

第一项来自抽样误差，即对$\beta_j$的估计误差

$se(\hat{e}^0)=\sqrt{se(\hat{y}^0)^2+\hat{\sigma}^2}$

### 残差分析

计算剔除某些因素后样本的水平

### 因变量为$\log y$时对$y$的预测

$\hat{y}=\exp(\hat{\log y})?$ 会系统地**低估**$y$的预测值

$\mathbb{E}[y\vert x]=\exp(\sigma^2/2)\cdot \exp(\beta_0+\beta_1x_1+\beta_2x_2+\dots)$

$\hat{y}=\exp(\hat{\sigma}^2/2)\exp(\hat{\log y})$，虽然不是无偏的，但是是一致的。它依赖于$u$的正态性

一般的情况，$\mathbb{E}[y\vert x]=\alpha_0\cdot \exp(\beta_0+\beta_1x_1+\beta_2x_2+\dots)$，$\alpha_0$是$\exp(u)$的期望值，且是大于一的，所以我们要求$\hat{\alpha}_0$

矩估计$\hat{\alpha}\_0=\frac{1}{n}\sum\exp(\hat{u}\_i)$，是一个一致有偏的估计量，这是所谓的污染估计值的一种特殊形式。或者我们可以通过一个过原点的简单回归：$m\_i=\exp(\beta\_0+\beta\_1x\_{i1}+\beta\_2x\_{i2}+\dots),\mathbb{E}[y\_i\vert m\_i]=\alpha\_0m\_i$，这样，我们就能从$y_i$对$\hat{m}_i$的回归中得到一个$\alpha_0$的无偏估计：

$$
\tilde{\alpha}_0=\frac{\sum\hat{m}_iy_i}{\sum\hat{m}_i^2}
$$

**拟合优度**

在普通最小二乘中，$R^2$就是$\hat{y}_i$与$y_i$之间的相关系数的平方，如果我们对所有观测量都计算$\hat{y}_i=\hat{\alpha}_0m_i$，由于是在变量上乘了一个常数$\hat{\alpha}_0$，所以对$\alpha_0$的估计不会影响到结果。我们还是计算$y
_i$和$\hat{y}
_i$的相关系数，这样就可以在不同的因变量模型之间对比拟合优度

# 含有定性信息的多元回归分析： 二值（或虚拟）变量

本部分在劳动经济学中较多涉及，不再赘述