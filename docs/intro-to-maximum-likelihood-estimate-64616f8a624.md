# 最大似然估计简介

> 原文：<https://medium.com/analytics-vidhya/intro-to-maximum-likelihood-estimate-64616f8a624?source=collection_archive---------15----------------------->

![](img/76b457386b4d171bd325ebfe6952e288.png)

[https://unsplash.com/photos/6tG_liBojOk](https://unsplash.com/photos/6tG_liBojOk)

**注意:**这篇文章将会比我的其他文章更加数学化。

想象把一便士翻转 10 次。在那 10 次之后，你有 4 次正面。你的朋友掷硬币 10 次，10 次都是正面。你和你的朋友继续抛硬币，但是在所有的尝试中，你有 65%的概率正面朝上。你的朋友辩称这是错误的，真实概率是 50%，但如果硬币有偏差呢？给定这些试验，我们将如何着手寻找最可能的正面概率方程(或估计值)？你的朋友很有说服力，但你知道数据是有意义的。你们两个一起扔了 1000 次硬币。怎么才能让你朋友相信概率是 65%？这就是最大似然估计(MLE)的用武之地。

# **什么是最大似然估计？**

最大似然估计只是一种估计概率分布参数的方法。寻找最大似然估计有两个主要步骤。第一步是建立似然方程。在实践中，对数似然法用得更多，我将在给出似然法和对数似然法的公式后解释这一点。以下是公式:

![](img/5faff822c7d545eebe9f3b04c8e1397f.png)

似然公式

![](img/f83ecd20b4351b6f576a243261d15747.png)

对数似然公式

那么，为什么使用对数似然公式而不是似然公式呢？可能性公式的主要问题是，我们处理的概率是小于或等于 1 但大于 0 的浮点数(或小数)。由于我们取这些小数的乘积，结果有时会非常小。这导致我们改用对数似然法。

最大似然法的第二步是找到使似然/对数似然方程最大化的参数。我们可以通过计算似然性/对数似然性方程相对于该参数的导数并将该方程设置为 0 来找到使似然性/对数似然性方程最大化的参数。它应该看起来有点像这样:

![](img/39f09a379d847c4e389de8740db12f92.png)

现在，抛开所有这些疯狂的数学，让我们来看一个例子。

# MLE 示例

让我们回到前面提到的便士的例子。让我们找到 P(头)的最大似然估计。那么，我们如何开始呢？让我们从我们所知道的开始。我们知道硬币可能是正面也可能是反面。我们知道方程一定涉及 P(头)和 P(尾)，但是我们也可以把 P(尾)写成(1-P(头))。让我们也创建一个名为 x_i 的变量。如果硬币正面着地，这个变量为 1；如果硬币反面着地，这个变量为 0。这种概率质量函数(pmf)被称为伯努利试验。如果这没有多大意义，我强烈建议阅读一下伯努利分布。

所以，我们应该有一些看起来有点像这样的东西。

![](img/70e9b7529414b46b54a27bbf15d9d5ce.png)

现在，我们如何着手求解 hat？我们必须对似然或对数似然方程求导，并将其设为 0。我将两者都做，只是为了演示如何对两个似然方程进行计算。它们将等同于相同的答案。

# 使用似然方程的最大似然估计；

![](img/aea55c463d45d4ffba93374ddf6be978.png)

# 使用对数似然方程的最大似然估计；

![](img/265ccdfe95fbfc689b360a96dd86e9a0.png)

# 3 头 1 尾的可能性图

![](img/0b4c32222b212c94f99c292285895caa.png)

如你所见，P(HHHT |θ)有一个最大值，即人头数除以翻转总数。在上面的证明中，我展示了正面概率的最大估计值是正面数除以总翻转数。希望这种可视化能让我们更深入地了解我们在上述方程中所做的事情。

# 结论

好吧，我知道有很多要消化。在这篇文章中，我们学习了最大似然估计及其用途。我还简要讨论了为什么对数似然比正态似然函数更有用。然后，我们完成了应用 P(Heads)的 MLE 的演示。我们证明了如果硬币是平衡的，朋友可能是真的。P(头数)最有可能的估计是 65%。和往常一样，如果你喜欢这篇文章，一定要击碎鼓掌按钮！下次见。