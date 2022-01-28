---
title: week2
date: 2021-10-05 00:07:00
tags:
---
<!--More-->
# 人工智能
## Evaluation
+ Groud Truth
  + 理论上来说，机器学习的模型是在近似`Ground Truth Function`, 而衡量算法就是为了让我们弄清楚这两个之间的差距。
  + 实际上，实际存在的实体是一个连续的空间，损失函数不能枚举所有的可能，他需要平衡数量和成本。
  + 我们采集到的数据往往会被认为是对`underlying data`的取样
+ Model Evaluation Methods
  + `Accuracy`, 最直接的方法，然后我们可以得到$ERR = 1 - ACC$
  + `Confusion Matrix`多个标签的时候会使用各个标签组成二维矩阵记录,二元(binary)的时候会直接使用正错误作为横纵轴组成二维矩阵记录
  + `ROC` 我们在二维图上以$\frac{FP}{TN+FP}$为$x$轴，以$\frac{TP}{TP+FN}$为$y$轴画图
  + `PR curve` precision/recall curve
+ Safety and Reliability Issues
  + 因为我们只能选择在部分数据上训练，在这部分上训练的平均误差我们认为是经验误差(empirical loss)，但实际上，我们使用的是`underly data`，在这个数据上的误差我们称为期望误差(expected loss)，这两个误差之间的距离我们称之为`generalisation error`，这是导致过拟合的原因
  + 使用perturbation在分类边界处，使人类和实际上的判断相同的两幅图片，在机器中被分为两类。
  + [backdoor](backdoor) Attack通过在模型训练数据内加上标志，使模型总是将某个标志的数据分类在一个标签内。
# 软件工程
# 编译原理
## CS143
+ expression
# 数据库
使用`GROUP BY`的时候要注意, 如果选取的列中有两个及以上的列的取值是一个集合（即不是唯一取值），那么这些列都要放入`GROUP BY`。或者需要提前使用`MIN`或者`COUNT`等函数将其变为唯一值,对于被聚合的值来说，这相当与直接在这个小标签后生成一个子表

`HAVING`相当与对各个子表进行一次筛选。`UNION`要求两个表的数据以相同的顺序和相同的数据类型排列，其中命令默认保留唯一值，如果要保留全部，需要使用`UNION ALL`
```sql
CREATE VIEW XXX as
SELECT [DISTINCT] column_name FROM table_name
WHERE [in, exists]
GROUP BY xxx
HAVING xxx
ORDER BY xxx [DESC]
UNION
SELECT xxx from xxx;
```
