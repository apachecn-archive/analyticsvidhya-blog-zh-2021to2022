# 关于统计的常见问题:第一部分

> 原文：<https://medium.com/analytics-vidhya/frequent-questions-related-to-statistics-part-i-8b2a856b22c7?source=collection_archive---------33----------------------->

![](img/fa2e38a631ee5846b43f8d425ad1e85e.png)

图片来自谷歌图片

无论数据科学、数据分析、预测、时间序列分析等任何领域，统计学都是与数据相关的任何分析的不可否认的基础。统计是探索和理解的广阔舞台。记住这一点总是很重要的，不管这是多么简单的事实，再次知道总是好的。

在这里，我写下了一些采访或小组讨论中遇到的关于统计数据的常见问题，以及这些问题是如何得到回答的。这个博客是这个系列的第一部分，有 15 个问题。

![](img/5efd8250e57f38c74526f3de7e99ce62.png)

图片来自谷歌图片

# 1) *什么是统计推断？*

使用给定数据对总体建模得出的任何统计结论。该分析有助于发现关于人口的新见解。它们涉及解释性数据分析，以可视化的模式或见解。

# 2)描述样本和总体？

人口是一整个群体，任何统计结论都是根据这个群体得出的。样本是被认为代表总体的总体子集。

# 3)什么是变异？

在现实世界中，样本并不总是完全代表总体的特征。例如，人口统计数据不能通过某个特定国家的小样本来计算，因为存在许多变量，如居住群体的规模、生活方式、死亡率、出生率等。这种差异叫做变异。

# 4)什么是统计中的自变量和因变量？

样本中要考虑的变量可以是因变量，也可以是自变量。因变量显示出对其他变量的依赖性，而自变量不依赖于其他变量。在研究过程中操纵自变量，测量因变量。

# 5)什么是数据采样？

数据采样是收集、处理和分析数据点(样本)以发现数据洞察和模式的方法或过程。它有助于预测建模和分析。

# 6)数据采样有哪些类型？

**简单随机抽样**:通过从总体中随机选择数据点来创建样本。

**分层抽样**:将数据点按共同特征分组，然后进行随机抽样。

**聚类采样**:数据最初被划分为一个定义因子的子集，将它们分成多个聚类，然后从每个聚类中收集数据点。

**系统抽样:**通过设置从较大总体中提取数据的间隔来创建样本。

# 7)什么是选择偏差？有哪些常见类型的选择偏差？

当从模型中收集和准备的样本数据不能代表模型将看到的真实病例群体时，就会出现选择偏倚。

**一些常见类型的选择偏差:**

1.观察者错误

2.时间间隔

3.抽样偏误

4.消耗

5.志愿者偏见

# 8)什么是中心极限定理？

“中心极限定理表明，无论总体分布的形状如何，随着样本量的增加，样本均值的抽样分布都接近正态分布。”

# 9)中心极限定理(“CLT”)为什么重要？

据说，随着样本量的增加，抽样误差减小。中心极限定理成立需要样本量等于或大于 30。这有助于实现样本数据的钟形曲线或正态分布。

# 10)什么是推断统计学？

它处理的是检验不同数据假设的统计数据。假设可以定义为什么数据会以某种模式产生结果。我们可以拒绝或不拒绝一个假设。我们不接受假设。

# 11)您在分析中常用的统计方法是什么？

a)均值(平均值)

b)中间值

c)模式

d)标准偏差

e)差异

f)四分位间距

# 12)中位数在哪里优于平均数？

在有大量异常值导致数据失真的情况下，中位数可以给出更准确的结果，因为它们对这种情况更稳健。发现异常值的一种方法是使用箱线图胡须。

# 13)什么是异常值，为什么会出现异常值？

离群值是与其他数据点非常不同的数据点。它们可能是由于数据收集过程中的错误、系统错误、仪器错误、欺诈性错误或任何自然偏差造成的。

离群值并不总是坏值；有时，这些异常显示出一种需要注意的模式或检测。就像在医疗报告的情况下，如果在患者的记录中检测到高 ECG 率，则该患者可能有一些心脏风险。因此，离群值需要用领域知识来分析。

# 14)如何处理异常值？

我们可以用许多方法处理异常值:

a)丢弃值。

b)给异常值封顶。

c)转型。

d)给数据点分配一个新值。

# 15)那么什么是根本原因分析呢？

根本原因分析(RCA)是确定数据显示的任何特定异常或模式的原因的过程。主要地，异常的原因可以通过 A/B 测试或假设测试来测试，并且可以推断出相应的决定。

任何改进的建议总是受欢迎的，因为它也将帮助我改进。

干杯！！