---
title: Robust Hypothesis Testing Using Wasserstein Uncertainty Sets
date: 2020-01-07 13:42:37
tags: 
- Domain Adaptation
- Hypothesis Testing
categories: Paper Reading
description: 本文是2020/1/6与老师讨论后推荐阅读的文章，关于假设检验怎样由两个假设，拓展到两个假设族。In this paper, we present a novel computationally efficient framework for developing data-driven
robust minimax detectors for non-parametric hypothesis testing based on the Wasserstein distance, in which the robust uncertainty set is chosen as all distributions that are close to the empirical distributions in Wasserstein distance.
---

<!-- more --> 

#  Abstract

We develop a novel computationally efficient and general framework for robust hypothesis testing. 

- The new framework features a new way to construct uncertainty sets under the null and the alternative distributions, which are sets centered around the empirical distribution defined via Wasserstein metric, thus our approach is data-driven and free of distributional assumptions. 

- We develop a convex safe approximation of the minimax formulation and show that such approximation renders a nearly-optimal detector among the family of all possible tests.

# 1 Introduction

Hypothesis Testing:

ratio test formulation= decision rule = detector to discriminate between hypothesis ( of distribution )

## 1.1 Motivation

真实分布和假设的分布可能有偏差 Using given hypothesis of distribution, if the true distribution deviates from the assumed nominal distribution ( outliers), the performance of likelihood ratio detector is no longer optimal.



## 1.2 Related work

- 引入分布球，一个分布变为多个分布 introduce/construct uncertainty sets for distributions:
  - [12] $\epsilon$-contamination sets : sets of distributions close to the nominal ones in terms of total variation metric.
  - [16, 9] use K-L divergence to construct uncertainty

- 选取分布球中最难搞定的分布 least-favorable distributions (LFD)

## 1.3 Proposed method

（1）构造分布球 a new way to construct uncertainty sets

经验分布作为球心，用Wasserstein距离作为分布距离的度量，构造分布球 use empirical distributions as the nominal distributions and the sets are defined using Wasserstein metrics

- 经验分布是从数据总结来的 empirical distributions come from data
- Wasserstein距离会比K-L divergence等更灵活地度量分布的距离 Wasserstein metric is a more flexible measure of closeness between two distributions
- 计算minimax的有效形式It often renders a computationally efficient reformulation of the minimax robust hypothesis testing problem.

（2）提出minimax问题的近似最优形式 develop a safe approximation of the minimax formulation by considering a family of tests with a special form that facilitates a convex approximation



# 2 Problem Set-up 

- observation space $\Omega \in \Bbb R^d $

  分布球(uncertainty sets) $\mathcal P_1,\mathcal P_2 \subset \scr P(\Omega) $, are two families of probability distributions on $\Omega$

  Simple hypothesis: Given an observation $w$ of the random variable, we would like to decide which one of the following hypotheses is true：

$$
H_1: w \sim P_1,\quad  P_1 \in \mathcal P_1\\
H_2: w\sim P_2, \quad P_2 \in \mathcal P_2
\notag
$$

- test is a (Lebesgue) measurable function: $T:\Omega \rightarrow\{1,2\}$ 即是判断随机变量每个值$w$要映射到哪个假设，或者说哪个概率分布上，1还是2。

- 对某个test最坏情况下的错误代价 The worst-case risk of a test : the maximum of the worst-case type-I errors (false positive) and type-II errors (false negative) ，即在每个分布球中，错误率（比如，属于$\mathcal P_1$的分布，但是detector T却估计结果为2了）最高（sup）的分布的错误率，然后取二者中更大（max）的那个错误率：（对于给定的T）
  $$
  \begin{equation}
  \epsilon\left(T | \mathcal{P}_{1}, \mathcal{P}_{2}\right):=\max \left(\sup _{P_{1} \in \mathcal{P}_{1}} P_{1}\{\omega: T(\omega)=2\}, \sup _{P_{2} \in \mathcal{P}_{2}} P_{2}\{\omega: T(\omega)=1\}\right)
  \end{equation}
  \notag
  $$

- minimax robust hypothesis test：在前述基础上，给定错误率为$\epsilon-optimal$，我们想要找到让这个最坏情况下最大错误代价最小达到$\epsilon$的test $T$，那么所有比最坏情况好的情况的错误代价就不那么大了：
  $$
  \begin{equation}
  \inf _{T: \Omega \rightarrow\{1,2\}} \epsilon\left(T | \mathcal{P}_{1}, \mathcal{P}_{2}\right)
  \end{equation}
  $$
  

- construct our uncertainty sets $\mathcal P_1,\mathcal P_2$:   centered around two empirical distributions $Q_k$ and defined using the Wasserstein metric:

$$
\begin{equation}
\mathcal{P}_{k}=\left\{P \in \mathscr{P}(\Omega): \mathcal{W}\left(P, Q_{k}\right) \leq \theta_{k}\right\}, k=1,2
\end{equation}
$$

​	$\theta_k $ is radius of the of the uncertainty set
$$
\begin{equation}
\mathcal{W}(P, Q):=\min _{\gamma \in \mathscr{P}\left(\Omega^{2}\right)}\left\{\mathbb{E}_{\left(\omega, \omega^{\prime}\right) \sim \gamma}\left[\left\|\omega-\omega^{\prime}\right\|\right]: \gamma \text { has mariginal distributions } P \text { and } Q\right\}
\end{equation}\notag
$$
​	We consider Wasserstein metric of order 1 for the ease of exposition.

# 3 Optimal Detector

- a family of tests in a special form 相对于前面的唯一特定的test $T$，这里考虑的是一系列test的集合，其中的每一个test称为为$T_{\phi}$，对于每一个test有不一样的$\phi$，且$\phi : \Omega \rightarrow \Bbb R$ 是一个从$d$维observation space映射到具体常数轴范围的函数，不再是映射到1和2（也就是$w$经过$\phi$函数映射到$x$轴上的会有一个归一化的、以0为界的threshold，左边判定为一个假设，右边判定为另一个假设）。即
  $$
  \phi (w) \geq 0 \rightarrow H_1\\
  \phi (w) < 0 \rightarrow H_2
  \notag
  $$
  那么基于此的前述(1)式的问题就变为：
  $$
  \begin{equation}
  \inf _{\phi: \Omega \rightarrow \mathbb{R}} \max \left(\sup _{P_{1} \in \mathcal{P}_{1}} P_{1}\{\omega: \phi(\omega)<0\}, \sup _{P_{2} \in \mathcal{P}_{1}} P_{2}\{\omega: \phi(\omega) \geq 0\}\right)
  \end{equation}
  $$
  任务变成找到$T_\phi$的集合中某一个这个$\phi$

- 【Definition 1】接下来（4）式就是给出（3）式的一个近似，它和（1）之间有gap。
  $$
  \begin{equation}
  \left.\Phi\left(\phi ; P_{1}, P_{2}\right):=\mathbb{E}_{P_{1}}[\ell \circ(-\phi)(\omega))\right]+\mathbb{E}_{P_{2}}[\ell \circ \phi(\omega)]
  \end{equation}\notag
  $$
  

$$
\begin{equation}
\inf _{\phi: \Omega \rightarrow \mathbb{R}} \sup _{P_{1} \in \mathcal{P}_{1}, P_{2} \in \mathcal{P}_{2}} \Phi\left(\phi ; P_{1}, P_{2}\right)
\end{equation}
$$

- 【Proposition 1】交换$inf$和$sup$运算顺序：
  $$
  \inf _{\phi: \Omega \rightarrow \mathbb{R}} \sup _{P_{1} \in \mathcal{P}_{1}, P_{2} \in \mathcal{P}_{2}} \Phi\left(\phi ; P_{1}, P_{2}\right)=\sup _{P_{1} \in \mathcal{P}_{1}, P_{2} \in \mathcal{P}_{2}} \inf _{\phi: \Omega \rightarrow \mathbb{R}} \Phi\left(\phi ; P_{1}, P_{2}\right)\notag
  $$
  

- 【Theorem 2】计算inf，即optimal detector
  $$
  \inf _{\phi: \Omega \rightarrow \mathbb{R}} \Phi\left(\phi ; P_{1}, P_{2}\right)=\int_{\Omega} \psi\left(\frac{d P_{1}}{d\left(P_{1}+P_{2}\right)}\right) d\left(P_{1}+P_{2}\right)\notag
  $$
  

$$
t^{*}(\omega) \in \arg \min _{t \in \mathbb{R}}\left[\frac{d P_{1}}{d\left(P_{1}+P_{2}\right)}(\omega) \ell(-t)+\frac{d P_{2}}{d\left(P_{1}+P_{2}\right)}(\omega) \ell(t)\right]\notag
$$

$$
\phi ^*(w) := -t^*(w)\notag
$$

- 求 optimal detector的sup：（表1的第4列）即找到最优detector下的让risk最大即我们最不希望出现的分布的情况，也就是两个分布距离最近的情况
  $$
  \sup _{P_{1} \in \mathcal{P}_{1}, P_{2} \in \mathcal{P}_{2}} \inf _{\phi: \Omega \rightarrow \mathbb{R}} \Phi\left(\phi ; P_{1}, P_{2}\right)=\sup _{P_{1} \in \mathcal{P}_{1}, P_{2} \in \mathcal{P}_{2}} \int_{\Omega} \psi\left(\frac{d P_{1}}{d\left(P_{1}+P_{2}\right)}\right) d\left(P_{1}+P_{2}\right)
  $$
  



# 4 Tractable Reformulation

In this section, we provide a tractable reformulation of (5) by deriving a novel strong duality result.

# 5 Numerical Experiments

- data: for human activity detection released by the Wireless Sensor Data Mining (WISDM) Lab in October 2013.

- The activity recognition task involves mapping time-series accelerometer data to a single physical user activity。
- 动作识别任务是要从时间序列的加速度序列数据对应到相应的动作。我们的目标是实时探测动作的变化。由于难以对很多不同的动作建立分布的模型，传统的参数方法不适用。Our goal is to detect the change of activity in real-time from sequential observations. Since it is hard to model distributions for various activities, traditional parametric methods do not work well in this case.

# 6 Conclusion

In this paper, we propose a data-driven, distribution-free framework for robust hypothesis testing based on Wasserstein metric. We develop a computationally efficient reformulation of the minimax problem which renders a nearly-optimal detector. 

The framework is readily extended to multiple hypotheses and sequential settings.



