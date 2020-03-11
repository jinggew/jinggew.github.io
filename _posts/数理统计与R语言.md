---
title: 数理统计与R语言
date: 2020-03-07 16:08:33
tags:
categories:
description:
typora-root-url:
---

数理统计与R语言课堂回顾的概率论和统计相关的基础知识备查。

<!-- more --> 



# 概率统计

## 0 几个常见分布

| Distribution                                                 | pdf/pmf                                   | cdf                               | $E[X]$均值          | $D[X]$方差             |
| ------------------------------------------------------------ | ----------------------------------------- | --------------------------------- | ------------------- | ---------------------- |
| 几何分布：得到一次成功所需要的试验次数$geometric(p)=G(p)$    | $P(X=k)=p(1-p)^{k-1}$                     |                                   | $\frac{1}{p}$       | $\frac{1-p}{p ^2}$     |
| 指数分布：独立随机事件发生的时间间隔$exponential(\lambda)=Exp(\lambda)$ | $f_X(x)=\lambda e^{-\lambda x},x\geq 0$   | $F_X(x)=1-e^{-\lambda x},x\geq 0$ | $\frac{1}{\lambda}$ | $\frac{1}{\lambda ^2}$ |
| 泊松分布：单位时间内随机事件发生的次数$Poisson(\lambda)=P(\lambda)$ | $P(X=k)=\frac{e^{-\lambda}\lambda^k}{k!}$ |                                   | $\lambda$           | $\lambda$              |



## 1 Moment generating function

### definition

$M_X(t)=E(e^{tX})$

### moments or all orders

- $E(X^r)=\frac{d^rM_X(t)}{dt^r}|_{t\rightarrow 0}=M_X^{(r)}(0)$
- $M_x(t)=\sum_{r=0}^{\infty}\frac{E(X^r)t^r}{r!}$

### theorems

- $M_Y(t)=M_{aX+b}(t)=e^{bt}M_x(at)$
- $X_i$ independent $\Rightarrow M_{ \sum_\limits{i=1}^n {X_i} }(t)=\prod\limits_{i=1}^n {M_{X_i}(t)}$

## 2 Random sample随机抽样

$x_1,x_2,...,x_n$ random sample from $f_X(x)$,  $E[X]=\mu$, $Var(X)=\sigma ^2$

### sample mean

- $E[\bar{x}]=\mu$
- $Var(\bar{x})=\frac{\sigma ^2}{n}$

### sample variance

$S^2(n)=Var(\bar{x})=\frac{\sum_{i=1}^n(x_i-\bar{x})^2}{n-1}$

- $E[S^2(n)]=\sigma ^2$



## 3 $\Gamma$ 分布

### $\Gamma$ function

$\Gamma(\alpha)=$

### MGF



## 4 $\chi^2$分布



### MGF

## F分布

## t分布

##  几个分布互相的转换关系

### 正态分布$\Rightarrow$$\chi ^2$分布

- $Z \sim \mathcal{N}(0,1) \Rightarrow Z^2 \sim \chi^2_1$
- $X_i \sim \mathcal{N}(\mu,\sigma^2) \Rightarrow \frac {(n-1)S^2}{\sigma^2} \sim \chi^2_{n-1}$

### gamma分布$\Rightarrow$$\chi ^2$分布

- $X\sim \Gamma(\alpha,\beta) \Rightarrow \frac{2}{\beta}X\sim \chi ^2_{2\alpha}$
- $X\sim \Gamma(\frac{\nu} {2},2) \Rightarrow X\sim \chi ^2_{\nu}$

### gamma分布$\Rightarrow$指数分布

- $X\sim \Gamma(1,\beta)=exp(\beta)$



### $\chi ^2$分布到$\Rightarrow F$分布

- $X_1 \sim \chi ^2_{\nu _1}, X_2 \sim \chi ^2_{\nu _2}  \Rightarrow F=\frac{X_1 /\nu_1}{X_2 /\nu_2}\sim F_{\nu_1, \nu_2}$

### 正态分布、$\chi ^2$分布$\Rightarrow$ $t$分布

- $Z \sim \mathcal{N}(0,1),V \sim \chi ^2_{\nu } \Rightarrow T=\frac{Z}{\sqrt{V/\nu}} \sim t(\nu)$

### 正态分布$\Rightarrow$ $t$分布

- $X_i \sim \mathcal{N}(\mu,\sigma^2)\Rightarrow T=\frac{\bar X -\mu}{S/\sqrt{n}} \sim t(n-1)$

### gamma分布$\Rightarrow $ Beta分布

- $X_1 \sim \Gamma(\alpha _1,\beta), X_2\sim \Gamma(\alpha _2,\beta),independent  \Rightarrow \frac{X_1}{X_1 + X_2}\sim Beta (\alpha _1,\alpha _2)$

### $F$分布$\Rightarrow $ Beta分布

- $F\sim F_{\nu_1, \nu_2}  \Rightarrow Y=\frac{\frac{\nu_1}{\nu_2}X}{1 + \frac{\nu_1}{\nu_2}X}\sim Beta (\frac{\nu_1}{2},\frac{\nu_1}{2})$

### $t$分布到$\Rightarrow F$分布

- $X \sim t_n \Rightarrow X^2 \sim F_{1,n}$



