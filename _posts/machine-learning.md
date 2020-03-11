---
title: machine learning
date: 2020-03-11 20:37:29
tags:
- Machine Learning
- notes
- 校内公开课
- Deep Learning
categories: Machine Learning
description:
typora-root-url: machine-learning
---

从校内深度学习公开课开始，每天高效地学习与记录吧！

<!-- more --> 

# 校内深度学习公开课

## 1. introduction

<img src="image-20200311220116042.png" style="zoom:50%;" />

<img src="image-20200311220706311.png" style="zoom:50%;" />

<img src="/image-20200311235135688.png" alt="image-20200311235135688" style="zoom:50%;" />

<img src="image-20200311230016827.png" style="zoom:50%;" />

- 深度学习的end-to-end：representer和learner可以端到端地学习，见下图。
  - 但是也不是说只能端到端，Hinton最早的unsupervised pre-training其实是两阶段的；
  - 一些representing learning的算法，效果不一定比深度方法差，端到端可能不一定要做，但是深度学习的常见端到端。

<img src="image-20200311230223713.png" style="zoom:50%;" />

## 正则项/惩罚项

- 度量假设空间的大小，高次多项式空间比线性空间大；
- 控制模型复杂度。因为机器学习的模型的泛化误差要求，在足够小（简单）的模型上足够大的训练集上训练得到足够小的训练误差，这样的模型才可能是在未知测试数据上效果好（泛化误差小）的模型。

<img src="image-20200311231046782.png" style="zoom:50%;" />

## loss function损失函数

- 0-1损失函数和分类准确率是完全对应的，也即和学习出来模型的评价准则对应；

  - > 评价准则：查准率，查全率，ROC等，直接针对它们优化是很困难的。

- hinge loss, logistic loss不对应，针对它们的优化和最终用来评价模型的准则并不等价。

## linear regression线性回归

<img src="/image-20200311231800367.png" alt="image-20200311231800367" style="zoom:50%;" />

- L2损失函数（均方误差）；
- 线性假设空间；
- L2二范数正则项；
- 目标函数有闭式解（正规方程normal equation），但是一般闭式解意味着大规模的计算量，这是我们不期望的。

## logistic regression逻辑回归

<img src="/image-20200311232358886.png" alt="image-20200311232358886" style="zoom:50%;" />

- logistic损失函数；
- 不能求闭式解，用梯度下降法迭代求解。

## softmax regression

<img src="/image-20200311233310919.png" alt="image-20200311233310919" style="zoom:50%;" />

- logistic 回归的多分类形式；

- softmax function：将score变成probability；

  <img src="/image-20200311233529287.png" alt="image-20200311233529287" style="zoom:50%;" />

- 交叉熵cross entropy损失函数：预测概率向量和标签（概率）向量的距离。

## 误差

<img src="/image-20200311234028935.png" alt="image-20200311234028935" style="zoom: 50%;" />

- 近似误差：假设空间好不好，近似误差太大可能就需要换一个假设空间更大的模型；

- 估计误差：估计误差大则说明假设空间可能太大了，否则学习算法在太大的假设空间中可能找不到最优的假设。

	- > 深度学习就是要学习feature extraction让假设空间和真实目标函数之间的gap变小。

## 参数化与非参数化

<img src="/image-20200311234413017.png" alt="image-20200311234413017" style="zoom:50%;" />

## 维度灾难与流形学习

<img src="/image-20200311234550862.png" alt="image-20200311234550862" style="zoom:50%;" />

- 高维空间十分稀疏，在“虫洞”中维度可能低一些；数据在流形行上的维度可能低于输入空间的维度，因此在流形的低维空间上就可能做数据的相似度等建模。

  - > unsupervised representation learning

## 偏差与方差

<img src="/image-20200311234952926.png" alt="image-20200311234952926" style="zoom:50%;" />

## 泛化

<img src="/image-20200311235338823.png" alt="image-20200311235338823" style="zoom:50%;" />

## 模型选择

<img src="/image-20200311235453094.png" alt="image-20200311235453094" style="zoom:50%;" />

- 不同超参，在训练集上分别训练，在验证集上检验效果，选效果最好的超参。

  - > 暴力方法：Auto-ML

