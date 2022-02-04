---
layout: posts
title: Stochastic Calculus for Finance
date: 2022-01-25
categories: 学习笔记
tags: [金融,数学]

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


# General Probability Theory

## infinite probability spaces

### $\sigma$-代数

$\sigma-algebra$, F is a collection of subsets of $\Omega$

1. empty set belongs to it
2. whenever a set belongs to it, its complement also belong to F
3. the union of a sequence of sets in F belongs to F

可以有推论：

1. $\Omega$ 一定在F中
2. 集合序列的交集也一定在F中

### 概率测量的定义 probability measure

一个函数，定义域是F中的任意集合，值域是[0,1]，满足：

1. $P(\Omega)=1$
2. $P(\cup^\infty_{n=1} A_n)=\sum^\infty_{n=1} P(A_n)$
    
    $triple(\Omega,F,P)$称为概率空间
    

uniform（Lebesgue）measure on [0,1]：在0，1之间选取一个数，定义：

$P(a,b)=P[a,b]=b-a,0\le a \le b\le 1$

可以用上述方式表述概率的集合的集合构成了sigma代数，从包含的所有闭区间出发，称为Borel sigma代数

$(a,b)=\cup_{n=1}^\infty[a+\frac{1}{n},b-\frac{1}{n}]$ ，所以sigma代数中包含了所有开区间，分别取补集可以导出包含开区间与闭区间的并，从而导出所有集合  

通过从闭区间出发，添加所有必要元素构成的sigma代数称之为$Borel \quad\sigma-algebra$ of subsets of [0,1] and is denoted B[0,1]

event A occurs almost surely if P(A)=1

## Random variables and distributions

definition: a random variable is a real-valued function X defined on $\Omega$  with the property that  for every Borel subset B of **R,** the subset of $\Omega$  given by:

$$
\begin{equation*}\{x\in B\}=\{\omega \in \Omega ; X(\omega )\in B\}\end{equation*}
$$

is in the $\sigma$-algebra F

本质是把事件映射为实数，同时为了保证可以拟映射，要求函数可测。

构造R的Borel子集？从所有的闭区间出发，闭区间的交——特别地，开区间也包含进来，从而开集包含进来 ，因为每个开集可以写成开区间序列的并。闭集也是Borel集合，因为是开集的补集。

关注X取值包含于某集合而不是具体的值

Definition: let X be a random variable on a probability space, the distribution measure of X is the probability measure $\mu _X$that assigns to each Borel subset B of R the mass $\mu _X(B)=P\{X\in B\}$ 

Random variable 有distribution 但两者不等同，两个不同的Random variable 可以有相同的distribution，一个单独的random variable 可以有两个不同的distribution

cdf：$F(x)=P\{X\le x\}$

$\mu_X(x,y]=F(y)-F(x)$

## Expectations

$E(X)=\sum X(\omega )P(\omega )$

$\{\Omega , F, P\}$ random variable $X(\omega )$ P是概率空间中的测度

$A_k=\{\omega \in \Omega ; y_k\le X(\omega ) < y_{k+1}\}$

lower Lebesgue sum $LS^-_{\Pi}=\sum y_k P(A_k)$

the maximal distance between the $y_k$ partition points approaches zero, we get Lebesgue integral$\int_{\Omega}X(\omega )dP(\omega)$

Lebesgue integral相当于把积分概念拓展到可测空间，而不是单纯的更换了求和方式。横坐标实际上是$\Omega$的测度。

if the random variables X can take both positive and negative values, we can define the positive and negative parts of X:

$X^+=max\{X,0\}$, $X^-=min\{-X,0\}$

$\int XdP=\int X^+dP-\int X^- dP$

**Comparison**

If $X\le Y$ almost surely, and if the Lebesgue integral are defined, then

$\int _{\Omega}X(\omega)dP(\omega)\le \int _{\Omega}Y(\omega)dP(\omega)$

If $X=Y$ almost surely, and if the Lebesgue integral are defined, then

$\int _{\Omega}X(\omega)dP(\omega)=\int _{\Omega}Y(\omega)dP(\omega)$

**Integrability, Linearity ...**

**Jensen’s inequality**

if $\phi$ is a convex, real-valued function defined on R and if $E|X|<\infty$ ,then

$\phi(EX)\le E\phi(X)$

$\mathcal{B} (\mathbb{R})$ be the sigma-algebra of Borel subsets of $\mathbb{R}$, the Lebesgue measure $\mathcal{L}$ on R assigns to each set $B\in \mathcal{B}(\mathbb{R})$ a number in $[0,\infty)$ or the value $\infty$ so that:

1. $\mathcal{L}[a,b] =b-a$ 
2. if $B_1,B_2,B_3 \dots$  is a sequence of disjoint sets in $\mathcal{B}$ ,then we have the countable additivity property: $\mathcal{L} (\cup_{n=1}^\infty B_n)=\sum_{n=1}^\infty \mathcal{L} (B_n)$

黎曼积分有且只有在区间中非连续点的集合的Lebesgue测度为零时有定义，即f在区间上几乎处处连续

若f的Riemann积分在区间上存在，则f是Borel可测的，而且Riemann积分和Lebesgue积分一致。

### convergence of integrals

**definition**

$X_1,X_2,X_3\dots$ be a sequence of random variables on the same probability space$(\Omega, \mathcal{F},\mathbb{P})$, $X$ be another random variable. $X_1,X_2,X_3\dots$  converges to $X$ almost surely $lim_{n\to \infty}X_n=X$  almost surely. if the set of $\omega \in \Omega$ for the sequence has limit $X(\omega)$ is a set with probability one. 

Strong law of Large Numbers: 

实的Borel可测的函数列$f_1,f_2,f_3\dots$ defined on$\mathbb{R}$, $f$ 也是实的Borel可测函数，the sequence converges to f almost every-where if 序列极限不为f的点的集合的 Lebesgue measure为零

$lim_{n\to \infty}f_n=f \textit{      almost everywhere}$

当随机变量几乎趋于一致，他们的期望值趋于极限的期望。类似地，当函数几乎处处converge，通常情况下，他们的lebesgue积分收敛到极限的积分。特殊的情况，就是

$lim_{n\to \infty}\int f_n(x)dx\ne \int lim_{n\to \infty} f_n(x)dx$

例如f是正态分布，左边为1，右边lebesgue积分为0

**theorem** *Monotone convergence* $X_1,X_2,X_3\dots$ be a sequence of random variables converging almost surely to another random variable $X$ if 序列几乎单调不减，期望的极限是EX

$lim_{n \to \infty}\mathbb{E}X_n=\mathbb{E} X$

把这里的随机变量换成Borel可测实值函数，也是成立的

$lim_{n\to \infty}\int_{-\infty}^{\infty}f_n(x)dx=\int_{-\infty}^{\infty}f(x)dx$

即使随机变量几乎不发散，但期望可能发散

**theorem Dominated convergence** 如果随机变量序列几乎趋于一致于$X$,且满足 $|X_n|\le Y$ almost surely for every n, $\mathbb{E}Y<\infty$, then $lim_{n\to \infty}EX_n=EX$

对于Borel可测实值函数也一样成立：若$f_n(x)\le g$ almost surely for every n, and $\int_{-\infty}^\infty g(x)dx<\infty$

若$f_n(x)\le g$ almost surely for every n, and $\int_{-\infty}^\infty g(x)dx<\infty$

$lim_{n\to \infty}\int_{-\infty}^\infty f_n(x)dx=\int_{-\infty}^\infty f(x)dx$

## Computation of Expectations

**theorem** $g$ is a Borel measurable function on $\mathbb{R}$ Then:

$\mathbb{E} |g(X)|=\int_\mathbb{R} |g(x)|d\mu_X(x)$ , if this quantity is finite, then$\mathbb{E} g(X)=\int_\mathbb{R} g(x)d\mu_X(x)$

PROOF

1. $\mathbb{EI}_B(X)=\mathbb{P}\{X\in B\}=\mu_X(B)=\int_\mathbb{R}\mathbb{I}_B(x)d\mu_X(x)$
2. nonnegative simple functions. A simple function is a finite sum of indicator functions times constants  
    
    $$g(x)=\sum\alpha_k \mathbb{I}_{B_k}(x)$$
    
    so 
    
    $$\mathbb{E}g(X)=\mathbb{E}\sum \alpha_k \mathbb{I}\_{B\_k}(X)=\sum \alpha_k\int_R\mathbb{I}\_{B\_k}d\mu_X(x)=\int_R(\sum \alpha_k\mathbb{I}\_{B\_k}(x))d\mu_X(x)=\int_R g(x)d\mu_X(x)$$
    
3. when g is nonnegative Borel-measurable functions. 
    
    $$B_{k,n}=\{x;\frac{k}{2^n}\le g(x)\le \frac{k+1}{2^n}\},k=0,1,2,\dots,4^n-1$$
    
    $$g_n(x)=\sum \frac{k}{2^n}\mathbb{I}\_{B\_{k,n}}(x)$$
    
    $$\mathbb{E}g(X)=\lim \mathbb{E}g_n(X)=\lim \int_R g_n(x)d\mu_X(x)=\int_R g(x)d\mu_X(x)$$
    
4. when g is general Borel-measurable function.
    
    $g^+(x)=\max\{g(x),0\},g^-(x)\min\{-g(x),0\}$
    

**Theorem** $X$ is a random variable on a probability space $(\Omega,\mathcal{F},\mathbb{P})$, and let g be a Borel measurable function on $\mathbb{R}$. $X$ has a density $f$ 

$\mathbb{E}|g(X)|=\int|g(x)|f(x)dx$

if quantity is finite, then 

$\mathbb{E}g(X)=\int g(x)f(x)dx$

PROOF

simple functions

$$\mathbb{E}g(X)=\mathbb{E}(\sum \alpha_k \mathbb{I}\_{B\_k}(X))=\sum \alpha_k \mathbb{E}\mathbb{I}\_{B_k}(X)=\sum \alpha_k \int \mathbb{I}\_{B\_k}f(x)dx\\\\=\int \sum \alpha
\_k\mathbb{I}\_{B\_k}(x)f(x)dx=\int g(x)f(x)dx$$

nonnegative Borel measurable functions

$$\mathbb{E}g_n(X)=\int g_n(x)f(x)dx$$

## Change of Measure

We can use a positive random variable $Z$ to change probability measures on a space $\Omega$. We need to do this when we change from the actual probability measure $\mathbb{P}$ to the risk-neutral probability measure $\widetilde{\mathbb{P}}$ in models of financial markets.

$$Z(\omega)\mathbb{P}(\omega)=\widetilde{\mathbb{P}}(\omega)$$

to change from $\mathbb{P}$ to $\widetilde{\mathbb{P}}$, we need to reassign probabilities in $\Omega$ using $Z$ to tell us where in $\Omega$ we should revise the probability upward and where downward. 

*we should do this set-by-set, but not $\omega$-by-$\omega$. According to following theorem*

**Theorem** let $(\Omega,\mathcal{F},\mathbb{P})$ be a probability space and let $Z$ be an almost surely nonnegative random variable with $\mathbb{E}Z=1$. for $A\in\mathcal{F}$, define $\widetilde{\mathbb{P}}(A)=\int_AZ(\omega)d\mathbb{P}(\omega)$. Then $\widetilde{\mathbb{P}}$ is a probability measure. If $X$ is a nonnegative random variable, then$\widetilde{\mathbb{E}}X=\mathbb{E}[XZ]$. If $Z$ is almost surely strictly positive, we also have $\mathbb{E}Y=\widetilde{\mathbb{E}}[\frac{Y}{Z}]$ for every nonnegative random variable $Y$.

PROOF

$\widetilde{\mathbb{P}}(\Omega)=1$, and countably additive. 

countably additive

let $A_1,A_2,A_3,\dots$ be a sequence of disjoint sets in $\mathcal{F}$, and define $B_n=\cup_{k=1}^n A_k$

we can use the monotone convergence theorem, to write

$$\widetilde{\mathbb{P}}(\cup \_{k=1}^\infty A\_k)=\widetilde{\mathbb{P}}(B\_\infty)=\int\_\Omega \mathbb{I}\_{B\_\infty}(\omega)Z(\omega)d\mathbb{P}(\omega)\\\\=\lim\_{n\to \infty}\int\_\Omega \mathbb{I}\_{B\_n}(\omega)Z(\omega)d\mathbb{P}(\omega)\\\\=\lim\_{n\to \infty}\sum\int\_\Omega\mathbb{I}\_{A\_k}(\omega)Z(\omega)d\mathbb{P}(\omega)=\sum\_{k=1}^\infty\widetilde{\mathbb{P}}(A\_k)$$

**Definition** 如果两个概率测度下sigma代数中零概率的集合相同，那么称两个概率测度为equivalent

在金融中，实际概率测度和风险中性概率测度就是equivalent的，在risk neutral world中almost work的hedge在actual world中一定也almost surely work

**Definition** 对于equivalent的两个概率测度以及它们之间的almost surely positive random variable, 这个随机变量$Z$称之为Radon-Nikodym derivative of$\widetilde{\mathbb{P}}$ with respect to $\mathbb{P}$ and we write $Z=\frac{d\widetilde{\mathbb{P}}}{d\mathbb{P}}$, $Z$ 的存在性成为Radon-Nikodym Theorem

# Information and Conditioning

## Information and $\sigma$-algebras

The hedge must specify what position we will take in the underlying security at each future time contingent on how the uncertainty between the present time and that future time is resolved.

**resolve sets by information**

$\Omega$ is the set of 8 possible outcomes of 3 coin tosses,

$A_H=\{HHH,HHT,HTH,HTT\},A_T=\{THH,THT,TTH,TTT\}$

if we are told the first coin toss only. the four sets that are resolved by the first coin toss form the $\sigma$-algebra

$\mathcal{F}_1=\{\phi,\Omega,A_H,A_T\}$

this $\sigma$-algebra contains the information learned by observing the first coin toss.

如果某几个集合是resolved，那么他们的并，以及各自的补也是resolved，符合$\sigma$-algebra

**Definition** let $\Omega$ be a nonempty set. Let $T$ be a fixed positive number and assume that for each $t\in [0,T]$ there is a $\sigma-algebra$  $\mathcal{F}(t)$. Assume further that if $s\le t$, then every set in $\mathcal{F}(s)$ is also in $\mathcal{F}(t)$. Then we call the collection of $\sigma-algebra$ $\mathcal{F}(t)$ a filtration.

At time $t$ we can know whether the true $\omega$  lies in a set in $\mathcal{F}(t)$

Let $\Omega=C_0[0,T]$, and assign probability to the sets in $\mathcal{F}=\mathcal{F}(T)$, then the paths $\omega\in C_0[0,T]$ will be the paths of the **Brownian motion**.

**Definition** Let $X$ be a random variable defined on a nonempty sample space $\Omega$. The $\sigma-algebra$ generated by $X$, denoted $\sigma(X)$, is the collection of all subsets of $\Omega$ of the form $\{X\in B\}$, $B$
  **ranges over** the Borel subsets of $\mathbb{R}$

这里的区别和简并有点像，随机变量是本征值，Filtration是量子态

**Definition**  Let $X$ be a random variable defined on a nonempty sample space $\Omega$. Let  $\mathcal{G}$ be a $\sigma-algebra$ of subsets of $\Omega$. If every set in $\sigma(X)$ is also in $\mathcal{G}$, we say that $X$ is $\mathcal{G}-measurable$

意味着$\mathcal{G}$ 中的信息足够决定$X$ 的值。对于borel可测函数$f$，$f(X)$也是$\mathcal{G}-measurable$的。对于多元函数同样成立

**Definition** Let  $\Omega$ be a nonempty sample space equipped with a filtration $\mathcal{F}(t)$. Let 

$X(t)$ be a collection of random variables indexed by $t\in [0,T]$, We say this collection of random variables is an adapted stochastic process if, for each $t$, the random variable $X(t)$ is $\mathcal{F}(t)-measurable$ 

## Independence

对于一个随机变量和一个$\sigma-algebra$ $\mathcal{G}$, measurable 和 independent 是两种极端，但大部分情况下，$\mathcal{G}$中但信息可以估计$X$， 但不足以确定$X$的值。

Independence会受到概率度量的影响，但measurability不会。

probability space $(\Omega,\mathcal{F},\mathbb{P})$,$\mathcal{G}\in \mathcal{F}, \mathcal{H}\in \mathcal{F}$, $\Omega$ 中的两个$\sigma-algebra$$A$和$B$独立如果$\mathbb{P}(A\cap B)=\mathbb{P}(A)\cdot\mathbb{P}(B)$, for all $A\in \mathcal{G},B\in \mathcal{H}$

独立的定义可以拓展到随机变量($\sigma-algebra$ they generate are independent)之间，随机变量与$\sigma-algebra$之间。

**Definition**  $(\Omega,\mathcal{F},\mathbb{P})$ is a probability space and let $\mathcal{G}_1,\mathcal{G}_2,\mathcal{G}_3\dots$ be a sequence of $sub-\sigma-algebra$ of $\mathcal{F}$. For a fixed positive integer n, we say that the n $\sigma-algebra$s $\mathcal{G}_1,\mathcal{G}_2,\mathcal{G}_3\dots\mathcal{G}_n$ are independent if$\mathbb{P}(A_1\cap A_2\cap \dots\cap A_n)=\mathbb{P}
(A_1)\mathbb{P}
(A_2)\dots \mathbb{P}
(A_n)$ for all $A_i\in \mathcal{G}_i$

这个同样也可以拓展到随机变量之间以及随机变量与$\sigma-algebra$之间。

**Theorem** Let $X$ and $Y$ be independent random variables, and let $f$  and $g$ be Borel measurable functions on $\mathbb{R}$. Then$f(X)$ and $g(Y)$ are independent random variables.

PROOF

Let $A$ be in the $\sigma-algebra$ generated by $f(X)$. This $\sigma-algebra$ is a $sub-\sigma -algebra$ of $\sigma(X)$. 

这很自然，every set in $A$ is of the form$\{\omega \in \Omega;f(X(\omega))\in C\}\text{,where }C\text{ is a Borel subset of }\mathbb{R}$. 只需要定义$D=\{x\in \mathbb{R};f(x)\in C\}$. Then we know$A\in \sigma(X)$. Let $B$ be the $\sigma-algebra$ gnenerated by $g(Y)$, then $B\in \sigma(Y)$. 由于$X,Y$独立，所以$A,B$独立。

**Definition** Let$X$ and $Y$ be random variables. The pair of random variables$(X,Y)$ takes values in the plane$\mathbb{R}^2$, and the joint distribution measure of $(X,Y)$ is given by$\mu_{X,Y}(C)=\mathbb{P}\{(X,Y)\in C\}$ for all Borel sets $C\in \mathbb{R}^2$

同样满足概率度量的两个条件：全空间测度为1，以及countable additivity preperty

**Theorem** Let $X$ and $Y$ be random variables. The following conditions and equivalent.

1. $X$ and  $Y$ are independent
2. the joint distribution measure factors:
    
    $\mu_{X,Y}(A\times B)=\mu_X(A)\mu_Y(B)$ for all Borel subsets$A\in \mathbb{R},B\in\mathbb{R}$
    
3. the joint cumulative distribution function factors
    
    $F_{X,Y}(a,b)=F_X(a)F_Y(b)$ for all $a\in \mathbb{R},b\in \mathbb{R}$
    
4. the joint moment-generating function factor:(矩母函数）
    
    $\mathbb{E}e^{uX+vY}=\mathbb{E}e^{uX}\cdot\mathbb{E}e^{vY}$
    
5. the joint density factors(if there is one)
    
    $f_{X,Y}(x,y)=f_X(x)f_Y(y)$ for almost every$x\in\mathbb{R},y\in\mathbb{R}$
    

conditions above imply but are not equivalent to:

1. $\mathbb{E}[XY]=\mathbb{E}X\cdot\mathbb{E}Y$ provided $\mathbb{E}|XY|<\infty$

**Definition** Let $X$ be a random variable whose expected value is defined. The variance of $X$, denoted $Var(X)$ is $Var(X)=\mathbb{E}[(X-\mathbb{E}X)^2]=\mathbb{E}[X^2]-(\mathbb{E}X)^2$

covariance of $X$ and $Y$ is $Cov(X,Y)=\mathbb{E}[(X-\mathbb{E}X)(Y-\mathbb{E}Y)]=\mathbb{E}[XY]-\mathbb{E}X\cdot\mathbb{E}Y$

correlation coefficient of $X$and $Y$ is $\rho(X,Y)=\frac{Cov(X,Y)}{\sqrt{Var(X)Var(Y)}}$

if $\rho(X,Y)=0$, we say that $X$ and $Y$ are uncorrelated

## General Conditional Expectations

**Definition** Let$(\Omega,\mathcal{F},\mathbb{P})$ be a probability space, let $\mathcal{G}$ be a sub-$\sigma$-algebra of $\mathcal{F}$, and let $X$ be a random variable that is either nonnegative or integrable. The conditional expectation of $X$ given $\mathcal{G}$, denoted$\mathbb{E}[X|\mathcal{G}]$, is any random variable that satisfies

1. **Measurability $\mathbb{E}[X|\mathcal{G}]$**  is $\mathcal{G}$ measurable
2. **Partial averaging $\int_A\mathbb{E}[X|\mathcal{G}(\omega)]=\int_AX(\omega)d\mathbb{P}(\omega)$** for all $A\in \mathcal{G}$

If $\mathcal{G}$ is generated by some other random variable $W$, then we can write$\mathbb{E}[X|W]$

(1) means although the estimate of $X$based on the information in $\mathcal{G}$ is itself a random variable, the value of the estimate $\mathbb{E}[X|\mathcal{G}]$ can be determined from the information in $\mathcal{G}$

存在性可以由Radon-Nikodym Theorem证明

唯一性的证明如下：If $Y$ and $Z$ both satisfy conditions, then their difference $Y-Z$ is as well, and thus the set $A=\{Y-Z>0\}$ is in $\mathcal{G}$. 根据(2),$\int_AY(\omega)d\mathbb{P}(\omega)=\int_AX(\omega)d\mathbb{P}(\omega)=\int_AZ(\omega)d\mathbb{P}(\omega)$

Hence $Y=Z$ almost surely.

**Theorem** Let $(\Omega,\mathcal{F},\mathbb{P})$ be a probability space and let $\mathcal{G}$ be a sub-$\sigma$-algebra of $\mathcal{F}$

1. linearity of conditional expectations
$\mathbb{E}[c_1X+c_2Y|\mathcal{G}]=c_1\mathbb{E}[X|\mathcal{G}]+c_2\mathbb{E}[Y|\mathcal{G}]$
2. taking out what is known. 
    
    If $X$ is $\mathcal{G}$-measurable
    
    $\mathbb{E}[XY|\mathcal{G}]=X\mathbb{E}[Y|\mathcal{G}]$
    
3. iterated conditioning.
    
    If $\mathcal{H}$ is a sub-$\sigma$-algebra of $\mathcal{G}$ and $X$ is an integrable random variable, then
    
    $\mathbb{E}[\mathbb{E}[X|\mathcal{G}]|\mathcal{H}]=\mathbb{E}[X|\mathcal{H}]$
    
4. independence
    
    If $X$ is independent of $\mathcal{G}$, then $\mathbb{E}[X|\mathcal{G}]=\mathbb{E}X$
    
5. conditional Jensen’s inequality
    
    $\mathbb{E}[\phi(X)|\mathcal{G}]\ge\phi(\mathbb{E}[X|\mathcal{G}])$
    

**Lemma** Let $(\Omega,\mathcal{F},\mathbb{P})$ be a probability space, and let $\mathcal{G}$ be a sub-$\sigma$-algebra of $\mathcal{F}$. Suppose the random variables $X_1,\dots,X_K$ are $\mathcal{G}$-measurable and the random variables$Y_1,\dots,Y_L$ are independent of $\mathcal{G}$. Let $f(x_1,\dots,x_K,y_1,\dots,y_L)$ be a function of the dummy variables, and define: 

$g(x_1,\dots,x_K)=\mathbb{E}f(x1,\dots,x_K,Y_1,\dots,Y_L)$

This means holding $X_i$ constant and integrate out $Y_i$.

Then,$\mathbb{E}[f(X_1,\dots,X_K,Y_1,\dots,Y_L)|\mathcal{G}]=g(X_1,\dots,X_K)$

**Definition** Let $(\Omega,\mathcal{F},\mathbb{P})$  be a probability space, let $T$ be a fixed positive number, and let $\mathcal{F}(t)$, $0\le t\le T$, be a filtration of $sub-\sigma-algebra$ of $\mathcal{F}$. Consider an adapted stochastic process $M(t)$:

1. If $\mathbb{E}[M(t)|\mathcal{F}(s)]=M(s)$ for all $0\le s\le t \le T$, this process is a ***martingale***. It has no tendency to rise or fall.
2. If $\mathbb{E}[M(t)|\mathcal{F}(s)]\le M(s)$ for all $0\le s\le t \le T$, this process is a ***supermartingale***. It has no tendency to rise, it may have a tendency to fall.
3. If $\mathbb{E}[M(t)|\mathcal{F}(s)]\ge M(s)$ for all $0\le s\le t \le T$, this process is a ***submartingale***. It has no tendency to fall, it may have a tendency to rise.

**Definition** Let $(\Omega,\mathcal{F},\mathbb{P})$ be a probability space, let $T$ be a fixed positive number, and let  $\mathcal{F}(t)$, $0\le t\le T$, be a filtration of $sub-\sigma-algebra$ of $\mathcal{F}$. Consider an adapted stochastic process $X(t)$. Assume that for all $0\le s\le t\le T$ and for every nonnegative, Borel-measuable function $f$, there is another Borel-measuable function $g$ such that:

$\mathbb{E}[f(X(t))|\mathcal{F}(s)]=g(X(s))$

Then we say that the X is a Markov process