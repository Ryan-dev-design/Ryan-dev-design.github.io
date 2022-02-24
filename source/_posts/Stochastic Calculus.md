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

# Brownian Motion

## Scaled Random Walks

### Symmetric Random Walk

To build a **symmetric random walk** we repeatedly toss a fair coin.

$X_j=\begin{cases}1 \text{ if }\omega_j=H\\\\-1\text{ if }\omega_j=T\end{cases}$

$M_0=0$, $M_k=\sum_{j=1}^kX_j$

the process $M_k$ is a *symmetric random walk.*

### Increments of the Symmetric Random Walk

A random walk has independent increments(独立增量性）

if we choose nonnegative integers$0=k_0<k_1<\cdots<k_m$ , the random variables $M_{k_i}-M_{k_{i-1}}$ are independent.

Each of these random variables $M_{k_i}-M_{k_{i-1}}=\sum_{j=k_{i+1}}^{k_{i+1}}X_j$ is called an increment of the random walk. 

Each increment has expected value 0 and variance $k_{i+1}-k_i$ . The variance is obvious because $X_j$ are independent.

### Martingale Property for the Symmetric Random Walk

We choose nonnegative integers $k<l$ and compute:

$\mathbb{E}[M_l|\mathcal{F}_k]=\mathbb{E}[(M_l-M_k)+M_k|\mathcal{F}_k]=\mathbb{E}[M_l-M_k|\mathcal{F}_k]+\mathbb{E}[M_k|\mathcal{F}_k]=M_k$

### Quadratic Variation of the Symmetric Random Walk

the quadratic variation up to time $k$ is defined to be  $[M,M]_k=\sum\_{j=1}^k(M\_j-M\_{j-1})^2=k$

This is computed path-by-path. taking all the one step increments $M_j-M_{j-1}$ along that path, squaring these increments, and then summing them.

Note that $[M,M]_k$ is the same as $Var(M_k)$, but the computations of these two quantities are quite different. $Var$ is computed by taking an average over all paths, taking their probability into account. If the random walk is not symmetric, the probability distribution would affect $Var$. On the contrary, the probability up and down do not affect the quadratic variation computation.

### Scaled Symmetric Random Walk

We fix a positive integer $n$ and define the **scaled symmetric random walk** $W^{(n)}(t)=\frac{1}{\sqrt{n}}M_{nt}$. If $nt$ is not an integer, we define $W^{(n)}(t)$ by linear interpolation between its values at the nearest points $s$ and $u$ to the left and right of $t$ for which $ns$ and $nu$ are integers. 

A Brownian motion is a scaled symmetric random walk with $n\to \infty$

$\mathbb{E}(W^{(n)}(t)-W^{(n)}(s))=0,Var(W^{(n)}(t)-W^{(n)}(s))=t-s$

Let $0\le s\le t$ be given, and decompose $W^{(n)}(t)$ as: $W^{(n)}(t)=(W^{(n)}(t)-W^{(n)}(s))+W^{(n)}(s)$ 

$(W^{(n)}(t)-W^{(n)}(s))$ is independent of $\mathcal{F}(s)$, the $\sigma-algebra$ of information available at time s, and $W^{(n)}(s)$ is $\mathcal{F}(s)$ measurable. So $\mathbb{E}[W^{(n)}(t)|\mathcal{F}(s)]=W^{(n)}(s)$

The **quadratic variation** of the scaled random walk: 

$\[W^{(n)},W^{(n)}\]\(t\)=\sum\_{j=1}^{nt}[W^{(n)}(\frac{j}{n})-W^{(n)}(\frac{j-1}{n})]^2=\sum\_{j=1}^{nt}[W^{(n)}[\frac{1}{\sqrt{n}}X_j]^2=\sum\_{j=1}^{nt}\frac{1}{n}=t$

### Limiting Distribution of the Scaled Random Walk

**Theorem: Central limit** Fix $t\ge 0$. As $n\to \infty$, the distribution of the scaled random walk $W^{(n)}(t)$ evaluated at time $t$ converges to the normal distribution with mean zero and variance $t$.

PROOF

For the normal density $f(s)=\frac{1}{\sqrt{2\pi t}}e^{-\frac{x^2}{2t}}$, the moment-generating function is 

$\phi(u)=\frac{1}{\sqrt{2\pi t}}\int_{-\infty}^\infty \exp\{ux-\frac{x^2}{2t}\}dx=e^{\frac{1}{2}u^2t}$

If $t$ is such that $nt$ is an integer, then the moment-generating function for $W^{(n)}(t)$ is:

$\phi_n(u)=\mathbb{E}e^{uW^{(n)}(t)}=\mathbb{E}\exp\{\frac{u}{\sqrt{n}}M_{nt}\}=\mathbb{E}\exp\{\frac{u}{\sqrt{n}}\sum_{j=1}^{nt}X_j\}=\mathbb{E}\prod_{j=1}^{nt}\exp\{\frac{u}{\sqrt{n}}X_j\}\\\\=\prod_{j=1}^{nt}\mathbb{E}\exp\{\frac{u}{\sqrt{n}}X_j\}=\prod_{j=1}^{nt}(\frac{e^{\frac{u}{\sqrt{n}}}+e^{\frac{-u}{\sqrt{n}}}}{2})=(\frac{e^{\frac{u}{\sqrt{n}}}+e^{\frac{-u}{\sqrt{n}}}}{2})^{nt}$

when $n\to \infty$ , $\phi(u)=e^{\frac{1}{2}u^2t}$

### Log-Normal Distribution as the Limit of the Binomial Model

We build a model for a stock price on the time interval from $0$ to $t$ by choosing an integer $n$  and constructing a binomial model for the stock price that takes $n$ steps per unit time. Up factor $u_n=1+\frac{\sigma}{\sqrt{n}}$, down factor $u_d=1-\frac{\sigma}{\sqrt{n}}$. $r=0.$

The risk-neutral probabilities are then:

$\tilde{p}=\frac{1+r-d_n}{u_n-d_n}=\frac{1}{2}$, $\tilde{q}=\frac{u_n-1-r}{u_n-d_n}=\frac{\sigma/\sqrt{n}}{2\sigma/\sqrt{n}}=\frac{1}{2}$

Random walk $M_{nt}=H_{nt}-T_{nt}$, while $nt=H_{nt}+T_{nt}$

the stock price at time $t$ is $S_n(t)=S(0)u_n^{H_{nt}}d_n^{T_{nt}}=S(0)(1+\frac{\sigma}{\sqrt{n}})^{\frac{1}{2}(nt+M_{nt})}(1+\frac{\sigma}{\sqrt{n}})^{\frac{1}{2}(nt+M_{nt})}(1-\frac{\sigma}{\sqrt{n}})^{\frac{1}{2}(nt-M_{nt})}$

we need to identify the distribution of this random variable as $n\to \infty$

**Theorem** As $n\to \infty$ , the distribution of $S_n(t)$ converges to the distribution of

$S(t)=S(0)\exp\{\sigma W(t)-\frac{1}{2}\sigma^2t\}$ 

$W(t)$ is a normal random variable with mean zero and variance $t$

PROOF:

$\log S_n(t)\\\\=\log S(0)+\frac{1}{2}(nt+M_{nt})\log (1+\frac{\sigma}{\sqrt{n}})+\frac{1}{2}(nt-M_{nt})\log (1-\frac{\sigma}{\sqrt{n}})\\\\=\log S(0)+\frac{1}{2}(nt+M_{nt})(\frac{\sigma}{\sqrt{n}}-\frac{\sigma^2}{2n}+O(n^{-3/2}))+\frac{1}{2}(nt-M_{nt})(\frac{\sigma}{-\sqrt{n}}-\frac{\sigma^2}{2n}+O(n^{-3/2}))\\\\=\log S(0)+nt(-\frac{\sigma^2}{2n}+O(n^{-3/2}))+M_{nt}(\frac{\sigma}{\sqrt{n}}+O(n^{-3/2}))=\log S(0)-\frac{1}{2}\sigma^2t+\sigma W^{(n)}(t)$

By the **Central Limit Theorem,** we know that $\frac{1}{\sqrt{n}}M_{nt}=W^{(n)}(t)\to W(t), \text{when }n\to \infty$

## Brownian Motion

### Definition of Brownian Motion

**Definition** Let $(\Omega,\mathcal{F},\mathbb{P})$ be a probability space. For each $\omega\in\Omega$, suppose there is a continuous function $W(t)$ of $t\ge 0$ that satisfies $W(0)=0$ that depends on $\omega$. Then $W(t),t\ge 0$ is a Brownian motion if for all $t_i$ the increments $W(t_i)-W(t_{i-1})$ are independent and each of these increments is normally distributed with $\mathbb{E}[W(t_{i+1})-W(t_i)]=0,Var[W(t_{i+1})-W(t_i)]=t_{i+1}-t_i$

Difference between BM and a scaled random walk: the scaled random walk has a natural time step and is linear between these time steps, whereas the BM has no linear pieces.

### Distribution of Brownian Motion

For any two times, the covariance of $W(s)$ and $W(t)$  for $s\le t$ is

$\mathbb{E}[W(s)W(t)]=\mathbb{E}[W(s)(W(t)-W(s))+W^2(s)]=\mathbb{E}[W(s)]\mathbb{E}[(W(t)-W(s))]+\mathbb{E}[W^2(s)]=s$

We compute the moment-generating function of the random vector$(W(t_1),W(t_2),\dots,W(t_m))$

$\phi=\mathbb{E}\exp\{u_mW(t_m)+\dots+u_1W(t_1)\}=\mathbb{E}\exp\{u_m(W(t_m)-W(t_{m-1}))+\dots+(u_1+u_2+\dots+u_m)W(t_1)\}=\mathbb{E}\exp\{u_m(W(t_m)-W(t_{m-1}))\}\cdots \mathbb{E}\exp\{(u_1+u_2+\cdots+u_m)W(t_1)\}=\exp\{\frac{1}{2}u_m^2(t_m-t_{m-1})\}\cdots\exp\{(u_1+u_2+\cdots+u_m)^2t_1\}$

The distribution of the Brownian increments can be specified by specifying the joint density or the joint moment-generating function of the random variables

**Theorem** Let$(\Omega,\mathcal{F},\mathbb{P})$ be a probability space. For each $\omega\in\Omega$, suppose there is a continuous function $W(t)$ of $t\ge 0$ that satisfies $W(0)=0$ and that depends on $\omega$. 

1. For all $0< t_0< t_1\cdots <t_m$, the increments are independent and each of these increments is normally distributed with mean and variance given by$\mathbb{E}[W(t_{i+1})-W(t_i)]=0,Var[W(t_{i+1})-W(t_i)]=t_{i+1}-t_i$
2. For all $0< t_0< t_1\cdots <t_m$, the random variables $W(t_i)$ are jointly normally distributed with means equal to zero and covariance matrix
    
    $\begin{pmatrix}    t_{1} &t_1 \cdots & t_{1} \\\\  t_1&t_2\cdots &t_2\\\\  \vdots & \ddots & \vdots \\\\    t_{1} &t_2 \cdots & t_{m}  \end{pmatrix}$ 
    
3. the random variables have the joint moment-generating function mentioned before

### Filtration for Brownian Motion

**Definition** Let$(\Omega,\mathcal{F},\mathbb{P})$ be a probability space on which is defined a Brownian motion $W(t),t\ge 0$. A filtration for the Brownian motion is a collection of $\sigma$-algebra $\mathcal{F}(t),t\ge 0$, satisfying:

1. **Information accumulates**
2. **Adaptivity: $W(t)$** is **$\mathcal{F}(t)$**-measurable
3. **Independence of future increments**

$\Delta(t),t\ge0$, be a stochastic process. $\Delta(t)$ is adapted to the filtration $\mathcal{F}(t)$ if for each $t\ge 0$ the random variable $\Delta(t)$ if $\mathcal{F}(t)$-measurable.

There are two possibilities for the filtration $\mathcal{F}(t)$ for a Brownian motion. 

1. to let $\mathcal{F}(t)$ contain only the info obtained by observing the BM itself up to time $t$. 
2. to include in $\mathcal{F}(t)$ info obtained by observing the BM and one or more other processes. But if the info in $\mathcal{F}(t)$ includes observations of processes other than the BM $W$, this additional info is not allowed to give clues about the future increments because of property iii

### Martingale Property for Brownian Motion

**Theorem** Brownian motion is a martingale

## Quadratic Variation

For BM, there is no natural step size. If we are given $T>0$, we could simply choose a step size, say $\frac{T}{n}$ for some large $n$, and compute the quadratic variation up to time $T$ with this step size:

$\sum_{j=0}^{n-1}[W(\frac{(j+1)T}{n})-W(\frac{jT}{n})]^2$

The variation of paths of BM is not zero, which makes stochastic calculus different from ordinary calculus

### First-Order Variation

$FV_T(f)=|f(t_1)-f(0)|+|f(t_2)-f(t_1)|+\dots+|f(T)-f(t_2)|=\int_0^{t_1}f'(t)dt+\dots+\int_{t_2}^Tf'(t)dt=\int_0^T|f'(t)|dt$

We first choose a partition $\Pi=\{t_0,t_1,\dots,t_n\}$ of $[0,T]$, which is a set of times. These will serve to determine the step size. The maximum step size of the partition will be denoted $\Vert\Pi\Vert=\max_{j=0,\dots,n-1}(t_{j+1}-t_j)$. We then define:

$FV_T(f)=\lim_{\Vert\Pi\Vert\to0}\sum_{j=0}^{n-1}\vert f(t_{j+1})-f(t_j)\vert$

用中值定理可以证明与积分相等

### Quadratic Variation

**Definition** Let $f(t)$  be a function defined for $0\le t\le T$. The quadratic variation to $f$ up to time $T$ is 

$[f,f]\(T\)=\lim\_{\Vert\Pi\Vert\to0}\sum\_{j=0}^{n-1}\vert f(t\_{j+1})-f(t\_j)\vert$

if $f$ is derivative, then $[f,f](T)=0$

if $\int_0^T\vert f'(t^*_j)\vert ^2dt$ is infinite, then $[f,f]\(T\)$ lead to a $0\cdot\infty$ situation, which can be anything  between $0$ and $\infty$

**Theorem** Let $W$ be a Brownian motion. Then $[W,W]\(T\)=T$ for all $T\ge 0$ almost surely.

PROOF

Define the *sample quadratic variation* corresponding to the partition of $[0,T]$,  $\Pi =\{t_0,t_1,\dots,t_n\}$ to be

 $Q_\Pi=\sum_{j=0}^{n-1}(W(t_{j+1})-W(t_j))^2$

We can show that $Q_\Pi$ converges to $T$ as $\Vert\Pi\Vert\to0$

$\mathbb{E}[(W(t_{j+1})-W(t_j))^2]=Var[W(t_{j+1})-W(t_j)]=t_{j+1}-t_j$ implies:

$\mathbb{E}Q_\Pi=\sum\mathbb{E}[(W(t_{j+1})-W(t_j))^2]=\sum(t_{j+1}-t_j)=T$

$Var[(W(t_{j+1})-W(t_j))^2]=\mathbb{E}[(W(t_{j+1})-W(t_j))^4]-2(t_{j+1}-t_j)\mathbb{E}[(W(t_{j+1})-W(t_j))^2]+(t_{j+1}-t_j)^2$

$\mathbb{E}[(W(t_{j+1})-W(t_j))^4]=3(t_{j+1}-t_j)^2$,$\mathbb{E}[(W(t_{j+1})-W(t_j))^2]=t_{j+1}-t_j$

PROOF

By Ito’s formula, we have

$𝑊^4(t)=4\int^𝑡_0𝑊^3_s𝑑𝑊_s+6\int^𝑡_0𝑊^2_sds$

$M(t):=\int_0^tW_s^3dW_s=0$ is a martingale and $\mathbb{E}M(t)=\mathbb{E}M(0)=0$

$\mathbb{E}W^4(t)=6\int_0^t\mathbb{E}[W_s^2]ds=6\int_0^tsds=3t^2$

so $Var[(W(t_{j+1}-W(t_j))^4]=2(t_{j+1}-t_j)^2$

and $Var(Q_\Pi)=\sum 2(t_{j+1}-t_j)^2\le2\Vert\Pi\Vert T$

In particular,  $\lim_{\Vert\Pi\Vert\to 0}Var(Q_\Pi)=0,lim_{\Vert\Pi\Vert\to0}Q_\Pi=\mathbb{E}Q_\Pi=T$

$(W(t_{j+1})-W(t_j))^2\approx t_{j+1}-t_j$$(W(t_{j+1})-W(t_j))^2=t_{j+1}-t_j$ when $t_{j+1}-t_j$ is very small

$dW(t)dW(t)=dt$ is the informal write

$dWdt=0,dtdt=0$

### Volatility of Geometric Brownian Motion

geometric Brownian motion: $S(t)=S(0)\exp\{\sigma W(t)+(\alpha-\frac{1}{2}\sigma^2)t\}$

realized volatility: the sum of the squares of the log returns

for $T_1=t_0<t_1<\cdots<tm=T_2$,

$\sum (\log\frac{S(t_{j+1})}{S(t_j)})^2=\sigma^2\sum(W(t_{j+1})-W(t_j))^2+(\alpha-\frac{1}{2}\sigma^2)^2\sum(t_{j+1}-t_j)^2+2\sigma (\alpha-\frac{1}{2}\sigma^2)\sum(W(t_{j+1})-W(t_j))(t_{j+1}-t_j)$

When the maximum step size $\Vert\Pi\Vert=\max_{j=0,1,\dots,m-1}(t_{j+1}-t_j)$ is small, then the first term is approximately equal to its limit $\sigma^2(T_2-T_1)$,hence, we have:

$\frac{1}{T_2-T_1}\sum(\log\frac{S(t_{j+1})}{S(t_j)})^2\approx\sigma^2$

## Markov Property

**Theorem** Let$W(t),t\ge0$, be a Brownian motion and let $\mathcal{F}(t),t\ge0$ Be a filtration for this Brownian motion. Then $W(t)$ is a Markov process

PROOF

We need to show:  $\mathbb{E}[f(W(t))\vert \mathcal{F}(s)]=g(W(s))$ $g$ Exists whenever given $0\le s\le t,f$

$\mathbb{E}[f(W(t))\vert\mathcal{F}(s)]=\mathbb{E}[f((W(t)-W(s))+W(s))\vert\mathcal{F}(s)]$

$W(t)-W(s)$ is normally distributed with mean zero and variance $t-s$

Replace $W(s)$ with a dummy variable $x$
, define $g(x)=\mathbb{E}f(W(t)-W(s)+x)$, then 

$g(x)=\frac{1}{\sqrt{2\pi(t-s)}}\int f(w+x)\exp\{-\frac{w^2}{2(t-s)}\}dw=\frac{1}{\sqrt{2\pi\tau}}\int f(y)\exp\{-\frac{(y-x)^2}{2\tau}\}dy$

Define the *transition density $p(\tau,x,y):=\frac{1}{\sqrt{2\pi\tau}}e^{-\frac{(y-x)^2}{2\tau}},\tau=t-s$*

$g(x)=\int f(y)p(\tau,x,y)dy$ 

And $\mathbb{E}[f(W(t))\vert\mathcal{F}(s)]=\int f(y)p(\tau,W(s),y)dy$

Conditioned on the information in $\mathcal{F}(s)$, the conditional density of $W(t)$ is $p(\tau,W(s),y)$. This is a density in the variable $y$, normal with mean $W(s)$ and variance $\tau$. The only information from $\mathcal{F}(s)$ that is relevant is the value of $W(s)$

## First Passage Time Distribution

exponential martingale corresponding to $\sigma$: $Z(t)=\exp\{\sigma W(t)-\frac{1}{2}\sigma^2t\}$

**Theorem** Exponential martingale  Let $W(t),t\ge 0$, be a Brownian motion with a filtration $\mathcal{F}(t),t\ge 0$, and let $\sigma$ be a constant, thew process $Z(t)$ is a martingale

PROOF

$\mathbb{E}[Z(t)\vert\mathcal{F}(s)]=\mathbb{E}[\exp\{\sigma W(t)-\frac{1}{2}\sigma^2t\}\vert \mathcal{F}(s)]=\mathbb{E}[\exp\{\sigma (W(t)-W(s))\}\cdot\exp\{\sigma W(s)-\frac{1}{2}\sigma^2t\}\vert \mathcal{F}(s)]=\exp\{\sigma W(s)-\frac{1}{2}\sigma^2t\}\cdot\mathbb{E}[\exp\{\sigma (W(t)-W(s))\}]$

$W(t)-W(s)$ is a normal distribution with mean zero and variance $\sigma$ so $\mathbb{E}[\exp\{\sigma (W(t)-W(s))\}]=\frac{1}{2}\sigma^2(t-s)$

$\mathbb{E}[Z(t)\vert\mathcal{F}(s)]=Z(s)$

Let $m$ be a real number, and define the first passage time to level $m$: $\tau_m=\min\{t\ge 0;W(t)=m\}$ if the BM never reaches the level $m$, we set $\tau_m=\infty$. A martingale that is stopped at a stopping time is still martingale and thus must have constant expectation. So:

$1=Z(0)=\mathbb{E}Z(t\land\tau_m)=\mathbb{E}[\exp\{\sigma W(t\land\tau_m)-\frac{1}{2}\sigma^2(t\land\tau_m)\}]$ $t\land\tau_m$ means the minimum of $t$ and $\tau_m$

If $\tau_m<\infty$, the term $\exp\{-\frac{1}{2}\sigma^2(t\land\tau_m)\}$ is equal to $\exp\{-\frac{1}{2}\sigma^2\tau_m\}$ for large enough $t$. $\tau_m=\infty$, the result converges to zero. So: 

$\lim\_{t\to\infty\}\exp\{\sigma W\(t\land\tau_m\)-\frac{1}{2}\sigma^2(t\land\tau_m)\}=\mathbb{I}_\{\{\tau_m<\infty\}}\exp\{\sigma m-\frac{1}{2}\sigma^2\tau_m\\}$

now we can obtain:

$1=\mathbb{E}[\mathbb{I}_{\{\tau_m<\infty\}}\exp\{\sigma m-\frac{1}{2}\sigma^2\tau_m\}]$

$\mathbb{E}[\mathbb{I}_{\{\tau_m<\infty\}}\exp\{-\frac{1}{2}\sigma^2\tau_m\}]=e^{-\sigma m}$

when $\sigma\to0$, we get $\mathbb{P}\{\tau_m<\infty\}=1$

$\tau_m$ is finite almost surely, so we may drop the indicator to obtain:

$\mathbb{E}[\exp\{-\frac{1}{2}\sigma^2\tau_m\}]=e^{-\sigma m}$

**Theorem** For $m\in \mathbb{R}$, the first passage time of Brownian motion to level $m$ is finite almost surely, and the Laplace transform of its distribution is given by 

$\mathbb{E}e^{-\alpha \tau_m}=e^{-\vert m \vert\sqrt{2\alpha}}$  for all $\alpha>0$

differentiation: $\mathbb{E}[\tau_me^{-\alpha\tau_m}]=\frac{\vert m\vert}{\sqrt{2\alpha}}e^{-\vert m\vert\sqrt{2\alpha}}$ for all $\alpha>0$

let $\alpha\to 0$ get obtain $\mathbb{E}\tau_m=\infty$ so long as $m\neq0$

## Reflection Principle

### Reflection Equality

for each Brownian motion path that reaches level m prior to time t but is at a level w below m at time t, there is a "reflected path" that is at level $2m-w$ at time $t$. This reflected path is constructed by switching the up and down moves of the Brownian motion from time $\tau_m$onward.

**Reflection equality**

$\mathbb{P}\{\tau_m\le t,W(t)\le w\}=\mathbb{P}\{W(t)\ge 2m-w\},w\le m,m>0$

### First Passage Time Distribution

**Theorem** For all $m\neq0$, the random variable $\tau_m$ has cumulative distribution function:

$\mathbb{P}\{\tau_m\le t\}=\frac{2}{\sqrt{2\pi}}\int_{\frac{\vert m\vert}{\sqrt{t}}}^\infty e^{-\frac{y^2}{2}}dy$

$f_{\tau_m}(t)=\frac{d}{dt}\mathbb{P}=\frac{\vert m\vert}{t\sqrt{2\pi t}}e^{-\frac{m^2}{2t}}$

PROOF

Use the reflection equality, we obtain

$\mathbb{P}\{\tau_m\le t,W(t)\le m\}=\mathbb{P}\{W(t)\ge m\}$

if $W(t)\ge m$, then we are guaranteed that $\tau_m\le t$. 

$\mathbb{P}\{\tau_m\le t,W(t)\ge m\}=\mathbb{P}\{W(t)\ge m\}$

so,$\mathbb{P}\{\tau_m\le t\}=2\mathbb{P}\{W(t)\ge m\}=\frac{2}{\sqrt{2\pi t}}\int_{m}^\infty e^{-\frac{x^2}{2t}}dx=\frac{2}{\sqrt{2\pi}}\int_{\frac{\vert m\vert}{\sqrt{t}}}^\infty e^{-\frac{y^2}{2}}dy$

### Distribution of Brownian Motion and Its Maximum

define the **maximum to date** for Brownian motion

$M(t)=\max_{0\le s\le t}W(s)$

Use the reflection equality, we can obtain the joint distribution of $W(t)$
 and $M(t)$

**Theorem** For $t>0$, the joint density of $(M(t),W(t))$ is

$f_{M(t),W(t)}(m,w)=\frac{2(2m-w)}{t\sqrt{2\pi t}}e^{-\frac{(2m-w)^2}{2t}}$

PROOF

$\mathbb{P}\{M(t)\ge m,W(t)\le w\}=\int_m^\infty\int_{-\infty}^wf_{M(t),W(t)}(x,y)dydx$

$\mathbb{P}\{W(t)\ge 2m-w\}=\frac{1}{\sqrt{2\pi t}}\int_{2m-w}^\infty e^{-\frac{z^2}{2t}}dz$

From the reflection equality, 

$\frac{1}{\sqrt{2\pi t}}\int_{2m-w}^\infty e^{-\frac{z^2}{2t}}dz= \int_m^\infty\int_{-\infty}^wf_{M(t),W(t)}(x,y)dydx$

Differentiate with respect to $m$

$-\int_{-\infty}^wf_{M(t),W(t)}(m,y)dy=-\frac{2}{\sqrt{2\pi t}}e^{-\frac{(2m-w)^2}{2t}}$

With respect to $w$, then we obtain the distribution

**Corollary** 

The conditional distribution of $M(t)$ given $W(t)=w$ is $f_{M(t)\vert W(t)}(m\vert w)=\frac{2(2m-w)}{t}e^{-\frac{2m(m-w)}{t}}$