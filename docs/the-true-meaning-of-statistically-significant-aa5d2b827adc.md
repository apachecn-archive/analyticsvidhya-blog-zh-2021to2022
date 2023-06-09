# 统计显著的真正含义

> 原文：<https://medium.com/analytics-vidhya/the-true-meaning-of-statistically-significant-aa5d2b827adc?source=collection_archive---------3----------------------->

![](img/1a78610488a588d1c6f5c581760a97b3.png)

# **简介**

统计学是理解和解释大量数据的有力工具。它有助于做出正确的决策，但也可能被误用。与数学的其他领域不同，关于统计的最重要的认识之一是，它不能用来得出精确的答案。尽管统计学有描述数据中心的单一度量，如平均值和中位数，但它们并不能完全描述数据。试图量化大型数据集时，单一答案可能会产生极大的误导。这就是为什么统计学侧重于使用许多指标(如标准差、置信区间和 p 值)来提供整体答案，然后可以对这些指标进行分析，以得出特定发现是否具有统计意义。统计显著性用于量化您是否确信从您的分析中得到的发现不是纯粹由于偶然。更直白地说，有一个统计上显著的发现意味着你可以确信这个发现是真实的。

假设我的朋友梦想成为一名 NBA 球员。身高 6 英尺 2 英寸的他出现在 NBA 有多罕见，这个答案有统计学意义吗？当你和你日常接触的每个人比较时，你可能会认为 6 英尺 2 英寸是 NBA 中一个合理的高度。即使当你看到 6 英尺 2 英寸在 NBA 身高原始分布中的位置时，你也不能确定 6 英尺 2 英寸在 NBA 标准中是否普遍。

![](img/9152f4233a7abc44a090764424b5bfc3.png)

现在，让我们用统计学来找出 6 英尺 2 英寸是否被认为是具有统计学意义的 NBA 身高！

# **定义假设**

使用您想要测试的初始假设来建立分析是很重要的。在这种情况下，我想测试一个 6 英尺 2 英寸的人是否与 NBA 球员的平均身高相等。这被称为替代假说(Ha)。然而，另一个假设不是我们将要检验的。相反，我们将测试与我们想知道的相反的零假设(H0)。在这种情况下，一个 6 英尺 2 英寸的人和 NBA 球员的平均身高是一样的。数学表述:

![](img/1fea718c0c58b16f3333474a191cb1c3.png)

零假设和替代假设表

下一步是定义你的统计意义的阈值。在分析之前做这件事是很重要的，这样你就不会试图在分析之后通过调整这个阈值来强制得到一个特定的结果。通常，显著性阈值(alpha)设置为 0.05 或 5%。这代表我们确定分析结果是否具有统计显著性以及我们是否会拒绝或未能拒绝零假设的概率阈值。本质上，如果结果发生的概率小于 5%，我们将拒绝我们的零假设，而支持另一个假设，因为测试显示结果是随机的概率小于 5%。或者，如果结果发生的概率大于 5%，那么我们将无法拒绝零假设，因为结果是随机的概率高于我们的任意阈值 5%。在这个例子中，如果我们确定 NBA 中某人身高 6'2 "的概率大于 5%,那么我们将无法拒绝我们的零假设，即一个身高 6'2 "的人和一个普通 NBA 球员之间存在差异。如果概率小于 5%，我们将拒绝我们的零假设，而支持我们的替代假设，即 6 英尺 2 英寸的人明显不同于 NBA 的平均身高。

注意:你可能会觉得奇怪，我说“拒绝或未能拒绝”零假设，或者我没有说，因为我“未能拒绝”零假设，我“接受”替代假设。这是故意这样做的，这又回到了我在引言中提出的观点，即统计数字不能给我们一个明确的答案。相反，我们可以使用统计学来进行有根据的猜测，用概率和置信区间来量化，这也给错误留下了空间。

回到示例:下面显示了 NBA 身高的标准正态曲线，它绘制了数据集平均值周围的值的概率，其中平均值为 0。

![](img/26d20f3b464d451650ca6b33f0069c5e.png)

您可以看到有 2 个不同的区域(红色和绿色),它们受我们之前建立的 0.05%或 5%的显著性阈值限制。我们在这里进行一个双尾假设检验，因为我们的替代假设没有说明一个特定的方向，而是简单地说明我们正在观察我们的测试身高和 NBA 身高之间是否有差异。

![](img/ed20c78f85e61646adfdb86bc965aaaa.png)

双尾假设检验

由于双尾检验，我们将显著阈值分成两个各为 2.5%的区域。这就在中间留下了一个 95%的区域，我们预计 95%的 NBA 高度都在这里。当转换为实际身高时，界限在 6.23 英尺和 6.81 英尺之间。换句话说，我们有 95%的信心认为 NBA 球员的身高在 6 英尺 3 英寸(6.23 英尺)和 6 英尺 10 英寸(6.81 英尺)之间。

![](img/a4fd89a971ffb7c17b5955fdbfe2a737.png)

# **执行统计测试**

有许多统计假设检验用于不同的情况。在这里，我不会介绍如何选择不同的测试。一个适用于我们在这里试图检验的假设的检验是单样本 Z 检验。该测试使用 z 得分来确定特定数据点在与总体进行比较时出现的概率。让我们使用 Z 检验方程来计算我们的 Z 检验统计量:

![](img/c5830549ab4f291a93bd80f69d4002e7.png)

其中，S 是我们测试的样本高度，是总体均值，σ是总体标准差，n 是样本数(在本例中，单个样本为 1)。

z 检验统计量为我们提供了一些重要的信息；值的符号和大小。负值表示样本小于总体平均值，而量值则量化样本与总体平均值的距离。z 检验值为-2.36 表示感兴趣的值(6'2 ")比总体平均值小 2.36 个标准差。当看下面的标准正态曲线时，你可以看到一个离平均值 2.36 个标准差的值是相当远的，因此不太可能。

![](img/bdb7bbcf0dd2e1900d7fb6f86194b592.png)

标准正态曲线

但是可能性有多大呢？为此，我们需要得到概率或 p 值。

# **证明显著性**

下一步是将 z 检验统计结果转换为概率或 p 值。这是 z 检验统计量是我们的比较总体的一部分的概率。在这个例子中，一个 6 英尺 2 英寸的人在 NBA 的概率是多少。我使用 python 的 scipy stats 包，使用以下代码将 z 测试统计值-2.36 转换为 p 值:

```
stats.norm.cdf(-2.36)
```

这产生了 0.009 或 0.9%的 p 值。

**注:**如果 z 检验统计量为正 2.36，则确定 p 值的等式为:

```
1 - stats.norm.cdf(2.36)
```

这将导致相同的 p 值 0.009 或 0.9%。这是因为 p 值是从左到右的累积概率。2.36 的 p 值实际上是 0.991 或 99.1%。

0.009 的 p 值意味着 NBA 中 6 英尺 2 英寸或更低的人的概率只有 0.9%。由于我们建立了 5%的显著性阈值，我们现在将拒绝我们的无效假设，即 6 英尺 2 英寸的人与普通 NBA 球员相比没有差异，因此，支持我们的替代假设，即有差异。

结果显示，一个 6 英尺 2 英寸的人将处于 5%的红色区域，因此不太可能发生:

![](img/e31d79f50bea4063b833a3e77ba32daa.png)

# **结论**

当试图使用统计数据时，量化你得到的任何结果的显著性水平是必要的。如果你用假设检验的结果来证明一家公司商业实践的改变，这一点尤其正确。仅仅显示样本之间均值的差异是不够的，相反，必须有一些定量的衡量标准来保证你得到的答案不是随机的，因此是不正确的。在这种情况下，有人可能已经猜到 6 英尺 2 英寸的人是 NBA 的简称，但在商业中，我们不能简单地猜测而不提供背景，这使我们能够将信心与我们的答案联系起来，从而使管理层能够做出明智的决定。举个例子，我不会打赌我会在我最喜欢的 NBA 球队中找到一个 6 英尺 2 英寸的球员。