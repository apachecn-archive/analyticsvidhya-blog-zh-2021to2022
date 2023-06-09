# 数据科学项目中的工作流

> 原文：<https://medium.com/analytics-vidhya/workflow-in-a-data-science-project-9aea41d9a3fd?source=collection_archive---------18----------------------->

![](img/02f3629044987445a2af63265ac946fd.png)

数据科学项目的目标始终是识别尽可能多的价值。

即使算法的能力每天都在提高，新的分析可能性不断出现，自动驾驶汽车将成为未来的新常态，但这并不意味着最新的算法和机器人 PA 就是适合你的东西。归根结底，数据科学创造的价值是基于金钱模型，而算法正在为你的公司节约或创造价值。

这就是为什么我们在 Borbaki 遵循七步结构化工作流程，确保我们不断追求尽可能多的价值。

为了保持对目标的关注，我们的每个数据科学项目都要经历以下七个步骤:

1.  商业理解
2.  数据挖掘技术
3.  数据清理
4.  数据探索
5.  特征工程
6.  预测建模
7.  数据可视化

本文将解释每个步骤包含的内容，以及为什么它对于数据科学项目是必不可少的。这篇文章是写给那些想学习如何处理数据科学项目和重要子目标的企业高管的。因此，它不会讨论不同的算法，代码语言和程序使用。

# 商业理解

了解行业、公司的工作流程和面临的挑战是第一步。

数据科学之旅的开始就是问“为什么”

问“为什么”可以确保具体的数据支持公司做出的战略决策，并且这是有保证的，有很高的可能性取得成果。

[微软 Azure 博客将为什么问题分成了五种不同的问题类型](https://docs.microsoft.com/en-us/azure/machine-learning/team-data-science-process/lifecycle-business-understanding):

1.  多少或多少？(回归)
2.  哪一类？(分类)
3.  哪个组？(聚类)
4.  这很奇怪吗？(异常检测)
5.  应该采取哪种选择？(建议)

在第一步，我们确定项目的中心目标，我们通过确定公司真正想了解他们的公司、竞争对手或客户的什么来做到这一点。

根据所提问题的类型，分析的重点会有所不同。

如果问题是如何导向，目标是使销售预测和营销支出改善。相比之下，分类和聚类的目标是深入了解客户概况和客户终身价值。

关于问题的类型没有什么规则，但最常见的问题是“*我的每个客户值多少钱*”、*我如何才能提高我的客户终身价值*”或“*我如何才能优化公司的工作流程？”*

# 数据挖掘技术

当通过问正确的问题来定义目标时，是时候收集必要的数据了。

当在数据挖掘步骤中工作时，我们收集可用的数据作为 fx。销货成本和位置数据。

数据挖掘和数据清洗(步骤 3)之间有着密切的联系。因为 Borbaki 的主要服务是为公司提供外包数据科学部门的可能性，所以数据挖掘过程比内部创建分析需要更长的时间。

在数据挖掘步骤，我们的数据科学家考虑需要提供什么数据来回答步骤 1 中定义的问题。然后，当基于可用数据指定数据需求时，我们从定位数据开始，找出获取数据的方法，以及哪种方法是存储和访问数据的最有效方法。这些都是与客户合作完成的。

# 数据清理

顾名思义——该打扫卫生了。数据清理通常是整个过程中最耗时的任务。这样做的原因很简单，因为许多可能的情况都需要清洗。

外汇。如果数据集中的同一列存在不一致，则相同的行可能被标记为 *0 或 1* ，而其他行被标记为*否或是，*，这使得算法无法抓取数据。

行中的数据也可能不一致，这意味着一些 0 可能是整数，而一些可能是字符串[1]。

# 数据探索

当清除了数据中的所有错误和不一致时，我们可以开始分析数据集。数据探索步骤是集思广益的地方。我们如何分析数据，我们对数据有什么样的概述，以及我们如何尽可能最好地使用数据。

当然，所有这些想法都已经在步骤 2 和 3 中考虑过了，但是现在是时候通过一个漏斗来获取数据了，所以我们只有最适合的数据来回答步骤 1 中提出的问题。

它包括提取和分析数据的随机子集，或创建直方图或分布曲线，以清楚地了解数据的总体趋势。

我们根据新信息缩小数据范围，以确定所提问题的最佳答案。

# 特征工程

“特征”是不同的数据类别，通过合并来识别模式。

外汇。一项来自以色列法官的研究发现，法官在午餐前做出的裁决更加严厉，而在美餐一顿后准予假释时则更加宽容。

这一分析的特点是:

*   给予判决
*   审判时间
*   评委午餐

*“想出特性很难，耗时，需要专家知识，应用机器学习基本上是特性工程”吴恩达机器学习专家*[*【2】*](http://sudeep.co/data-science/Understanding-the-Data-Science-Lifecycle/)

这一步是关于使用领域知识来转换原始数据信息信息特征，这些特征可以帮助回答步骤 1 中的问题，并且不要害怕使用不规则的数据来识别模式。

特征工程中通常有两种类型的任务:

特征选择和构造。

**功能选择:**

您决定哪些功能使用起来有意义，哪些功能制造的“噪音”比信息多。

**特色建设:**

要素构造包括从现有要素创建新要素。外汇。如果其中一个特征是年龄，但是所使用的模型只关心这个人是成年人还是未成年人，那么您可以将其阈值设置为 18，并为高于和低于该阈值的实例分配不同的类别。

# 预测建模

在这一步，机器学习被添加到数据科学项目中。根据步骤 1 中提出的问题，我们的数据科学家会根据步骤 4 和 5 中的数据决定哪个模型最适合回答问题。

这个决定并不容易，因为从来没有一个正确的答案。我们选择训练的模型将取决于可用日期和时间的大小、类型和质量。

一旦模型被训练，最重要的事情是评估它的成功以保证尽可能高的模型精度。

基于知识和专业技能，我们的数据科学家知道在开始项目时使用哪些模型，但在步骤 6 创建敏捷的工作方式之前不要决定，以确保我们最终使用的模型最适合这项工作。

# 数据可视化

一旦从模型中确定了预期的见解，我们的重点是呈现结果，以便公司的所有关键利益相关者能够理解结果并从中获得价值。

因为如果我们无法将分析结果作为可操作的见解交付，那么分析结果一文不值，所以我们确保报告以 CEO、中层领导和执行者能够理解的方式突出最重要的发现，并根据结果采取行动。

**将结果付诸行动**

现在，当分析被密封并交付时，我们到达了分析的最重要的部分:实现业务工作流结果。

在这一步，我们评估结果和对公司的理解。公司负责在日常工作流程中应用结果，但我们始终与客户保持密切联系，以确保他们不会对结果或如何从中获得价值感到不确定。

数据科学可以在所有行业和所有企业中获得价值，无论规模大小，这都是关于提出正确的问题。

在 Borbaki，我们相信未来是由数据科学驱动的。今天的公司越早开始使用数据科学来制定战略业务战略决策，他们就能越早将公司带到新的高度。

*原载于 2021 年 5 月 16 日 https://www.borbaki.com*[](https://www.borbaki.com/2021/05/05/data-science-and-pos-data/)**。**