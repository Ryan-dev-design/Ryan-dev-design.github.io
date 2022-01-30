---
layout: posts
title: Stochastic Calculus for Finance
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