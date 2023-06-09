# 机器学习背后的数学

> 原文：<https://medium.com/analytics-vidhya/the-mathematics-behind-machine-learning-b4bb3bec967c?source=collection_archive---------12----------------------->

在过去的几年里，有几个人联系我，说他们热衷于进入数据科学的世界，使用机器学习(ML)技术来探索统计规律，并构建无懈可击的数据驱动产品。然而，我观察到有些人实际上缺乏必要的数学直觉和框架来获得有用的结果。这是我决定写这篇博文的主要原因。最近，出现了许多易于使用的机器和深度学习包的可用性热潮，如 [scikit-learn](http://scikit-learn.org/) 、 [Weka](http://www.cs.waikato.ac.nz/ml/weka/) 、 [Tensorflow](https://www.tensorflow.org/) 、 [R-caret](http://topepo.github.io/caret/index.html) 等。机器学习理论是一个交叉统计学、概率学、计算机科学和算法方面的领域，产生于从数据中迭代学习和发现可以用于构建智能应用的隐藏见解。尽管机器和深度学习有巨大的可能性，但要想很好地掌握算法的内部工作原理并获得良好的结果，对这些技术中的许多技术进行彻底的数学理解是必要的。

# 为什么要担心数学？

机器学习的数学之所以重要，有很多原因，下面我将重点介绍其中的一些原因:

1.  选择正确的算法，包括考虑准确性、训练时间、模型复杂性、参数数量和特征数量。
2.  选择参数设置和验证策略。
3.  通过理解偏差-方差权衡来识别欠拟合和过拟合。
4.  估计正确的置信区间和不确定性。

# 你需要什么水平的数学？

当试图理解像机器学习这样的跨学科领域时，主要问题是理解这些技术所需的数学量和数学水平。这个问题的答案是多维度的，取决于个人的水平和兴趣。对机器学习的数学公式和理论进步的研究正在进行中，一些研究人员正在研究更先进的技术。我将陈述我认为成为机器学习科学家/工程师所需的最低数学水平，以及每个数学概念的重要性。

![](img/0772a0c7c72f29740b9f331841d3cb57.png)

# 线性代数:

我的一位同事 Skyler Speakman 最近说“线性代数是 21 世纪的数学”，我完全同意这种说法。在 ML 中，线性代数随处可见。诸如主成分分析(PCA)、奇异值分解(SVD)、矩阵的特征分解、LU 分解、QR 分解/因式分解、对称矩阵、正交化和正交归一化、矩阵运算、投影、特征值和特征向量、向量空间和范数等主题对于理解用于机器学习的优化方法是需要的。线性代数的神奇之处在于有如此多的在线资源。我总是说，传统的课堂正在消亡，因为互联网上有大量的可用资源。我最喜欢的线性代数课程是麻省理工学院课件提供的课程(吉尔伯特斯特朗教授)。

![](img/d973c7b3f139b0a5c11ad0aea6470ce1.png)

# 概率论与统计:

机器学习和统计学不是很不同的领域。实际上，最近有人将机器学习定义为“在 Mac 上做统计”。ML 需要的一些基本统计和概率理论是组合学、概率规则和公理、贝叶斯定理、随机变量、方差和期望、条件和联合分布、标准分布(伯努利、二项式、多项式、均匀和高斯)、矩母函数、最大似然估计(MLE)、先验和后验、最大后验估计(MAP)和抽样方法。

![](img/c50bac397401b7a90c3a8a682822ab14.png)

# 多元微积分:

一些必要的主题包括微分和积分，偏导数，向量值函数，方向梯度，海森，雅可比，拉普拉斯和拉格郎日分布。

![](img/7f4b0d3912574d42091f31cbdd5c9bab.png)

# 算法和复杂优化:

这对于理解我们的机器学习算法的计算效率和可扩展性以及利用我们的数据集中的稀疏性是重要的。需要了解数据结构(二叉树，散列，堆，栈等)，动态规划，随机和次线性算法，图形，梯度/随机下降和原始对偶方法。