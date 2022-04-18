---
layout: posts
title: Managing cash-in risk embedded in Portfolio Insurance strategies
date: 2022-04-18
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

# Managing cash-in risk embedded in Portfolio
Insurance strategies: a review

the presence of an insurance could have convinced the investors to not leave the market, and **take risk**

Perold and Sharpe: 3 different insurance strategies: option-based \ option-duplicating \ derivative independent 

option-based: buy zero-coupon bond maturity equals investment time horizon + risky option

option-duplicating: replicate option with a self-financing strategy (overcome the lack of liquidity)

low interest rate level reduce the available risk budgets. both a sustainable equity & capital protection? **dynamically allocating both in risky and riskless assets** mostly used—CPPI

**the problem of CPPI:**

after a severe market draw-down, the risk budget **erases** — cash-in risk

1. the remaining portfolio value shifted into the riskless asset, might not guarantee
2. subsequent rises of the risky asset

# OBPI

key: ensuring a minimal terminal portfolio value

$V_t^{OBPI}=qB_t+pC(t,S_t,K)$

the strategy is static, no trading occurs in $(0,T)$

if the option whose strike price equal to the wealth to be immunized are not traded on the market, investors must replicate the option using hedge strategies. But the incompleteness...

# CPPI

the value of the portfolio at maturity $V_T^{CPPI}$ is higher than a guaranteed amount $G$ a proportion (PL) of the initially invested amount $V_0^{CPPI}$

floor $F_t=F_T(1+r)^{-(T-t)},F_T=G$

*cushion $C_t$*, the difference between $V_t$ and $F_t$. exposure to risky asset $E_t=m\times C_t$， $m$  is the multiplier. the strategy is self-financed, so the rest of the portfolio $V_t-E_t$ is invested into risk-free asset.

to avoid excessive equity exposure, $E_t$ is bounded to be at most $LEV\cdot V_t^{CPPI}$

the proportion of wealth invested to the risky asset:

$$
\alpha_t^{CPPI}=\min\{\frac{m(V_t^{CPPI}-F_t)}{V_t^{CPPI}},LEV\}\\\\\beta_t=1-\alpha_t
$$

## CPPI with continuous rebalancing

floor process $F=\{F_t\}_{t\in[0,T]}$, the dynamic is $dF_t=rF_tdt,F_0=G\cdot e^{-rT}$, $W_t$ is a standard Brownian motion in real world measure $\mathbb{P}$

$$
dV_t=mC_t\frac{dS_t}{S_t}+(V_t-mC_t)rdt\\\dS_t=r S_tdt+\sigma S_tdW_t^\mathbb{P}\\\\\frac{dC_t}{C_t}=((1-m)r+\mu m)dt+m\sigma dW_t^\mathbb{P}\\\C_t=C_0\exp(rt+m(\mu-r)t+m\sigma W_t^\mathbb{P}-\frac{m^2\sigma^2t}{2})\\\\=C_0\exp(r(1-m)t+\frac{m(1-m)\sigma^2t}{2})(\frac{S_t}{S_0})^m\\\V_0=C_0+F_0\to C_0=G/PL-Ge^{-rT}\\\V_T=C_T+G=G+\frac{G}{PL}(1-PLe^{-rT})\exp((rT+\frac{m\sigma^2T}{2})(1-m))(\frac{S_T}{S_0})^m
$$

the CPPI strategy is equivalent to taking a long position in a zero-coupon bond with nominal $G$ to guarantee the capital at maturity and investing the remaining sum into a risky asset which has $m$ times the excess return and $m$ times the volatility of $S$ and is perfectly correlated with $S$.

there is non zero probability that during a sudden downside movement of the underlying asset, the fund manager will have no time to readjust the portfolio. then it goes crashing through the floor.

## CPPI with discrete time rebalancing

discrete time CPPI:

$$
\tau=\{t_0=0<t_1<\cdots<t_{n-1}=T\}\\\C_{t_{k+1}}^\tau=C_{t_0}^\tau\prod_{i=1}^{min(\nu,k+1)}(m\frac{S_{t_i}}{S_{t_{i-1}}}-(m-1))\\\nu:=min(t_k\in\tau\vert V_{t_K}^\tau-G),\infty \text{if not attained}\\\phi_t^{(S),\tau}:=max(\frac{mC_{t_k}^\tau}{S_{t_k}},0)
$$

local shortfall probability

shortfall probability

expected shortfall

how to ensure the effectiveness of CPPI strategy?

1. given an estimate for $\mu$ and $\sigma$, determine the value of multiplier and the number of rebalances $n$ to let the probability of falling below the guarantee above a confidence level
2. base on large deviations methods, estimate the possible losses between two consecutive trading dates

## CPPI in presence of jump in asset price

no relax on continuous trading assumptions, we introduce jumps in the risky asset

the cash-in risk cannot be attributed exclusively to trading restriction

$$
dB_t=rB_tdt,B_0=b\\\\dS_t=S_{t-}dZ_t
$$

$Z$ is a possible discontinuous driving process, modeled as semi-martingale, to ensure the positivity of the price, we assume that $\Delta Z_t>-1$, and $\nu=\inf(t\ge 0,V_t\le F_t)$, when $t<\nu$:

$$
dV_t=m(V_{t-}-F_t)\frac{dS_t-}{S_{t-}}+(V_{t-}-m(V_{t-}-F_t))\frac{dB_t}{B_t}\\\frac{dC_t}{C_t-}=mdZ_t+(1-m)rdt
$$

introduce the discounted cushion $C_t^*=C_t/B_t$

$$
\frac{dC_t^*}{C_{t-}^*}=m(dZ_t-rdt)=mdL_t,L_t=L_0+\int_0^tdZ_s-rds\\\\C_t^*=C_0\mathcal{E}(mL)_t
$$

at time $\nu$, all the portfolio is invested into risk-free asset and when $t\ge \nu$, the value of $C_t^*$ remains constant. Define $\tilde{C}\_t=C_{t\wedge\nu}^*=C\_0^*\mathcal{E}(mL)\_{t\wedge \nu}$

it can become negative in presence of negative jumps of sufficient size of stock price.

# Some extensions of CPPI allocation strategy

## Time-Invariant Portfolio Protection (TIPP)

modifies the floor:

$$
\tilde{F}\_t=max(F\_t,PL\cdot \sup_{s\le t} V\_s)
$$

$PL$ is the protection level. the floor will jump up with the portfolio value in  order to reduce the risky asset allocation when the market peaks

the growth rate of the TIPP floor can be considered comparable to the portfolio in each instant of time

less exposure to the risky asset, change more smoothly over time, the overall return will be generally lower

## Variable Proportion Portfolio Insurance (VPPI)

make the multiplier dynamic

EPPI: the multiplier changes like this:

at $t=0$ the investor fix a reference price for the risky asset rebalancing $S^{(0)}$,

$$
m_t=\eta+\exp(aln(\frac{S^{(1)}}{S^{(0)}}))
$$

$\eta>1$ is an arbitrary constant, and the rest is the dynamic multiple adjustment factor (DMAF)

when the stock price goes up, the mechanism of the EPPI strategy creates more number of holding shares to perform an upside capture

ﬁx the multiplier at each rebalancing date by considering a local quantile guarantee condition posed by $\mathbb{P}\_{t\_k}(C\_{t\_{K+1}}>0\vert C\_{t\_k}>0)=\\\\\mathbb{P}\_{t\_k}(m\_{t\_k}\frac{S\_{t\_{k+1}}}{S\_{t\_k}}-(m\_{t\_k}-1)>0)\ge 1-\epsilon$

it implies an upper bound $\bar{m}_{t_k}$, the precise number is determined by the distribution

# Hedging gap risk embedded through options

another way to hedge gap risk embedded in portfolio insurance strategies is to use **options**

take a long position on an at-the-money put option on the CPPI portfolio with a strike price at least equal to the minimum value that the investor requires at maturity

or take a long position on an at-the-money call option on the CPPI portfolio

key: model option on CPPI

## Modeling option on CPPI

the discrete time process describing the evolution of the risky asset under the risk neutral probability measure $\mathbb{Q}$ is:

$$
\frac{S
\_{t\_k}}{S\_{t\_{k+1}}}=\exp((r-\frac{\sigma}{2})\Delta t+\sigma W\_{t\_k})
$$

$W_{t_k}\sim N(0,\Delta t),\Delta t=\frac{T}{n},\tau=\{t_0=0<t_1<\cdots<t_{N-1}<t_N=T\}$

the value of the CPPI portfolio is 

$$
V\_{t\_{k+1}}^\tau=e^{r(t\_{k+1}-min(\nu,k+1)}((V\_0-F\_0)\prod_{i=1}^{min(\nu,k+1)}(m\frac{S\_{t\_i}}{S\_{t\_{i-1}}}-(m-1)e^{r\Delta t})+F\_{t\_{min(\nu,k+1)}})
$$

in this framework, we consider the interest rate between the adjustments

self-financed, so the expected the portfolio terminal value under the risk neutral probability measure is $e^{rT}V_0$. the CPPI is sold as a product with a capital guarantee, so for the investors the value of the CPPI is not equal to $V_0$

the payoff at maturity of the discrete CPPI is $CPPI_T=max\{V_T,F_T\}$

the expected value of the portfolio at maturity is composed of two parts:

$$
\mathbb{E}^Q[CPPI]=\mathbb{E}^Q[CPPI_T\vert C_1]+\mathbb{E}^Q[CPPI_T\vert C_2]
$$

$C_1$ means the portfolio at maturity does not fall below the floor over $[0,T]$

1. when the strike price $K$ is equal to the value of the guarantee at maturity $F_T$, the option ends up in the money if $C_{t_{k+1}}^\tau>0$, then a portfolio composed by the option on a CPPI with $K=F_T$ and a zero coupon bond with nominal value $K$ is **exactly equal** to a CPPI with floor $F$
2. when the strike price is higher than the guarantee amount at maturity $K\ge F_T$, the option ends up in the money if the CPPI has not fallen below the floor, and if the value is greater than the strike price $K$.

## Structured product written on GMEE-CPPI

the options linked to portfolio insurance strategies can be a suitable way to obtain a downside protection, by it is unable to offer an equity market participation in the event that after draw down, the risky asset recover nicely.

define a minimum threshold which is always invested in the risky asset — *guaranteed minimum equity exposure* (GMEE-CPPI)

GMEE $\alpha_{min}$ 

$$
\alpha_t:=max\{min\{\frac{m(V_t^{CPPI}-F_t)}{V_t^{CPPI}},L\},\alpha_{min}\}
$$

the equity participation will never go below $\alpha_{min}$, but it means the CPPI allocation implemented in a real portfolio might not be able to protect the invested capital

combination of CPPI and OBPI:

1. a proportion of the initial portfolio value invested in time-congruent zero-coupon bond following the OBPI
2. the remaining part of the portfolio put into an exotic call option linked to a GMEE-CPPI where the CPPI  has an equity index as risky asset
