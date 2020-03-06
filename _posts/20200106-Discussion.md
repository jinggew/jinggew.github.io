---
title: 20200106 Discussion
date: 2020-01-06 13:36:59
tags:
- Domain Adaptation
- Hypothesis Testing
categories: Discussion
description: 2020/1/6与老师的讨论，关于hypothesis testing和domain adaptation。
typora-root-url: 20200106-Discussion
---

<!-- more --> 

# Simple hypothesis testing

## Problem setup

Simple hypothesis testing for data $x$, we hope to get to know whether its distribution is more close to the probability $p_1$, which is our hypothesis $H_1$, or it is more close to the probability $p_2$, which is our hypothesis $H_2$.
$$
H_1: x \sim P_1\\
H_2: x\sim P_2
\notag
$$

## Log likelihood ratio test

How to decide which hypothesis is better ? We use log likelihood ratio test as following:          

​                                                                                                                                                
$$
log \frac{P(x|H_1)}{P(x|H_2)}>\frac{P_2(C_{12}-C_{22})}{P_1(C_{21}-C_{11})}\notag \
$$

then choose the hypothesis $H_1.$
$$
log \frac{P(x|H_1)}{P(x|H_2)}<\frac{P_2(C_{12}-C_{22})}{P_1(C_{21}-C_{11})}\notag \
$$
then choose the hypothesis $H_2$.

i.e. we choose the corresponding distribution $P1$ or $P_2$ as the result.

Log likelihood is a kind of decision rule, also called "detector", which can discriminate between two hypotheses and achieve small error probability.

假设P1 P2分别来自uncertainty set
$$
x \sim p\in\mathcal P_1=\{p|W(p,\hat p_1)<\theta\}
$$
w是 wassentein distance

minmax问题：

外部最小化最坏情况的error

内部最大化worst case rick得到两个最近的分布

  

优化问题变为
$$
min \  E (T|\mathcal P_1,\mathcal P_2)\\
\\worst-case risk
$$
minmax变为maxmin问题
$$
sup \ inf
$$
【步骤

- find least favorable distribution $p_1,p_2$

  therem 2 里面的解convex问题 就解决了sup问题

- find detector可以用log likelihood等，就是解决给定p1p2下的inf问题

【优点

- p1p2 doesnt habe to habe same support 两个分布不必要靠的太近
- work on small sample size

【用于domain adaptation

- source的$p(x|y=0)$和$p(x|y=0)$是不同的分布，
- $p(x|y=0)和target的Q(x|y=0)$是related在一个分布球里的

【用于activity detection问题

- time window用于检测不同的跑步和走路状态信号
- i时刻前后的分布是否相同/发生变化

## dataset

【wifi localization

【人机互动：上半身信号迁移到身体其他部位信号的模型

【image：office caltech MNIST postoffice

# 用到domain adaptation

$p(\phi(x)|y=0)和target的Q(\phi(x)|y=0)$是related在一个分布球里的

找TCA找出$\phi$的代码

文章方法的MATLAB代码

在wifi数据集上试一下

- robust论文不用看理论细节
- 找带神经网络版本的JAN？
- 提取feature的方式，也可以
- wifi数据集是不是分类问题，分几类？





# 2020.1.11

- 凸优化，书，基础知识
- duality对偶问题，参考TCA中用到拉格朗日对偶将constraints问题化为unconstraint问题
- 将文中（6）式化为unconstraint用到loss中，和classification loss和domain close的loss一起BP。
- $P_1^*$ 和$P_2^*$是二分类问题下的最接近的分布，要是它能分出来，那更简单的也可以分出来。
- 将二分类拓展到多分类，可能需要重新推导文中公式。