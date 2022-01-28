---
title: week1
date: 2021-10-01 04:06:54
tags: 
  - COMP218
  - COMP219
  - COMP201
---
第一周划水度过，内容比较少。
<!--More-->

# 人工智能

+ 本周主要是对模型的总体介绍，和对数据集的介绍
  + 数据表示
	 + 数据的表示方法会影响存储数据的内存大小和处理速度，模型的准确度也会被影响
	 + 使用`feature vectors`表示数据，比较常见的是用固定大小的向量表示数据实体
	 + 使用`feature space`表示。我们将各个数据实体认为是分布在特征空间内的点
  + 数据集
	 + 我们认为数据集内的数据都是完全独立分布(`independent and identically`)的, 所以数据集越大，分布越接近真实分布(`underlying distribution`)
	 > 时间序列的数据就不是独立分布的
  + Hypothesis space and inductive bias
	 + 机器学习会通过训练数据不断迭代优化模型，这个模型是从一个函数空间`Hypothesis space`选择出来的（这意味着确定了学习范围），这个函数空间由学习算法决定的。
		+ 如果你认为模型是线性的，那么不论你有多少数据，你也只能在线性函数里面寻找最优的模型
	 + 学习算法本身的偏好或者局限导致的误差称为`inductive bias`,
		+ 例如决策树算法会偏好产生更简单的决策树，神经网络使用正则化让模型在参数之间产生偏好
	 + 学习分为`batch learning` 和 `online learning`，前者分批送入，后者一个个送入
  + Density Estimation
	 + Maximum Likelihood Estimation
		+ 这是一个`frequentist method`, 我们使用公式计算出该模型的最大似然
		  $$\theta_{MLE} = arg_{\theta}maxP(D|\theta)$$

		+ 其中$D$是数据分布， $\theta$是模型参数。因为我们默认数据均是独立随机分布的，所以数据集合的生成的概率是所有数据点选取的概率的乘积，即
		  $$\theta_{MLE} = arg_{\theta}max \prod_{(x, y) \in D} P(x|\theta)$$
		+ 其中$(x, y)$是一条数据，x是数据，有是数据的标签，为了减少连乘，我们会使用`Log Maximum Likelihood Estimation`
		  $$\theta_{MLE} = arg_{\theta}max \sum_{(x, y) \in D} logP(x|\theta)$$
	 + Maximum a posteriori(MAP) queries
		+ 这是一种`bayesian method`，我们在目前数据分布的情况下推测出最佳的参数
		  $$\theta_{MAP} = arg_{\theta}maxP(\theta|D)=arg_{\theta}maxP(D|\theta)P(\theta)$$
		+ 这个公式内省略了常数项，$P(D)$, 这一项对每个数据集是一样的，该方法和$MLE$的不同主要在是否我们有先验的参数，我们可以认为$MLA$是$MLE$加上regularisation。
		  $$\theta_{MLA} = arg_{\theta}max \sum_{(x, y) \in D} logP(x|\theta) + P(\theta)$$
	 + Expected A Posteriori(EAP)
		$$E(\theta|D) = \int_{\theta}\theta P(\theta|D)d\theta$$
  + Probability
	 + `marginal probability` 表示的是无条件概率，该概率不把任何其他事情作为前提如$P(X)$
	 + `joint probability` 表示联合概率，多件事同时发生的概率
	 + `Conditional probability` 条件概率 在一件事发生之后，另一件事发生的可能性
	 + `independence and Conditional independence` 前一种是独立，后一种是在某种条件满足了之后他们互相独立 
# 编译原理

+ 本周主要讲了`DFAs`和`NFAs`。前者为确定有限自动机，后者为不确定有限自动机。它们都可以用一个`元组`进行表示，$(Q, \Epsilon, \delta, q_0, F)$。
	 + $Q$是状态`states`(有限)的集合
	 + $\Epsilon$是字符串`alphabet`， 输入进自动的字母
	 + $\delta$是变化方程`transition function`，一个状态加上一个字母，会进入新的状态、
		+ 在`DFA`中，新状态是有且仅有一个，但是在`NFA`中新状态可以是一个集合，甚至是空集
		> $\epsilon$-NFA可以接受空串
		>
		> 如果在`DFA`中没有画出end的状态点，需要计数进去
	 + $q_0$是初始状态，这个状态有且只有一个
	 + $F$是最终（接受的）状态，这个状态可以有多个
# 软件工程
prototype
+ waterfall model
  + difficulty of accomondation change after process is underway
  + 熟知了需求才能使用
+ Evolutionary Development
  + easy to change after process is underway
  + lack of process visibility
  + systems are sometimes pooly structured
+ agile development --- test driven development
+ incremental Development  --- 将需求分成小部分，先完成用户的需求，用户可以很早用到

