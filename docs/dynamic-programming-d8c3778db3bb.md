# 动态规划

> 原文：<https://medium.com/analytics-vidhya/dynamic-programming-d8c3778db3bb?source=collection_archive---------13----------------------->

![](img/356b6e534fc59a747138947862e6e7b1.png)

动态规划(DP)是一种算法技术，通过将优化问题分解为更小的子问题，并利用整体问题的最佳解决方案由其子问题的最佳解决方案决定的事实，来解决优化问题。

动态编程主要是一种递归优化。我们可以使用动态编程来优化任何重复调用相同输入的递归解决方案。这个想法是为了保存子问题的效果，这样我们以后就不用重新计算了。这种简单优化的时间复杂度从指数级降低到多项式级。

比如我们写一个简单的斐波那契数的递归解，时间复杂度是指数级的，但是如果我们通过存储子问题解来优化，时间复杂度是线性的。我们可以存储每个步骤的结果，这样我们就可以重用它。

检查下面的例子来理解它。

我们可以注意到，对于输入值完全相同的函数，有许多不同的调用。Fib (3)从头开始计算三次。Fib (2)算了五次！这些重新计算相当昂贵。所以，我们可以重用已经计算的 fib，并用新的函数替换它。

可以应用动态编程的两种方式:

**自上而下:**

问题以这种形式分解，如果问题已经解决，则返回保存的值；否则，函数的值被记忆，这意味着它将被第一次计算；否则，存储的值将被回调。对于计算密集型系统，记忆是一个完美的方法。不要混淆记忆和背诵。

记忆！=记忆

**自下而上:**

这是最小化递归的好方法，因为它减少了递归产生的时间复杂度(即，由于重新计算相同的值而产生的内存开销)。这里估计了小问题的解决方案，加起来就是整体问题的解决方案。(本文后面提供的示例将帮助您更好地理解这一点。)

让我们确定这两种方法的优缺点:

**自上而下的方法:**

**优点:**

1)更容易实现。

2)只计算必要的状态，如果不需要某个状态，则跳过该状态。

**缺点:**

1)容易耗尽堆栈中的空间。

2)难以推理的时间和空间复杂性。

**自下而上的方法:**

**优点:**

1)可以优化空间。

2)没有递归开销。

3)容易推理出时间和空间复杂度。

**缺点:**

1)必须计算所有的状态，因为我们是在一个循环中。

2)通常更难实现。

# 动态规划的不同算法

动态规划有各种算法，通过以递归方式将复杂问题分解成更简单的子问题，可以简化复杂问题。

这些算法列举如下:

**1)** **贝尔曼·福特最短路径算法:-**

该算法有助于找到从一个顶点到加权图中所有其他顶点的最短路径。它类似于 Dijkstra 的算法，但它可以处理边权重为负的图。

这种负权重边缘会产生负权重循环。这是一个循环，通过返回到同一点来减少总的路径距离。

贝尔曼福特算法的工作原理是高估从起始顶点到所有其他顶点的路径长度。然后，它通过寻找比先前高估的路径更短的新路径来迭代地放松那些估计。通过对所有顶点重复这样做，我们可以保证结果是优化的。

![](img/6af9b26d76e40a3005e2f5c0907ce227.png)

要使用该算法找到最短路径，我们需要遵循以下步骤:

1)从加权图开始。

2)选择一个起始顶点，并为所有其他顶点分配无限路径值。

3)访问每条边，如果路径距离不准确，则放宽路径距离。

4)我们需要这样做 V 次，因为在最坏的情况下，一个顶点的路径长度可能需要重新调整 V 次。

5)注意右上角的顶点是如何调整其路径长度的。

6)在所有顶点都有了它们的路径长度之后，我们检查是否存在负循环。

**2)** **背包问题算法:-**

这个算法在组合问题中很有帮助。它的基本意思是一定容量的袋子。

例如，在超市中有 n 个包装(n ≤ 100)，包装 I 的重量 W[i] ≤ 100，价值 V[i] ≤ 100。小偷闯入超市，小偷不能携带超过 M (M ≤ 100)的重量。这里要解决的问题是:小偷会拿走哪些包裹以获得最高价值？

![](img/954b233f1c8df4fa7b406b59d736e282.png)

输入:-

最大重量 M 和包装数量 n。

权重 W[i]和相应值 V[i]的数组。

输出:-

最大化价值和相应的容量权重。

小偷会拿走哪些包裹？

背包算法可以进一步分为两种类型:

**0/1 背包问题:——**在这种算法类型中，每个包可以带也可以不带。此外，小偷不能拿走被拿走的包裹的一小部分或者拿走一个包裹超过一次。这种类型可以使用动态规划方法来解决。

**分数背包问题:——**这类可以用贪心策略解决。

**3)**弗洛伊德-沃肖尔算法:-

该算法用于从给定的赋权图中寻找所有对的最短路径问题。作为该算法的结果，它将生成一个矩阵，该矩阵将表示图中任何节点到所有其他节点的最小距离。

作为第一步，我们初始化与输入图矩阵相同的解矩阵。然后，我们通过将所有顶点视为中间顶点来更新解矩阵。其思想是一个接一个地挑选所有的顶点并更新所有的最短路径，其中包括作为最短路径中的中间顶点的挑选的顶点。当我们选择顶点编号 k 作为中间顶点时，我们已经将顶点{0，1，2，k-1}视为中间顶点。分别对于每对(I，j)源顶点和目的顶点，有两种可能的情况。

![](img/50f4f115d0e0467dee765930715ecb14.png)

1) K 不是从 I 到 j 的最短路径中的中间顶点

2) K 是从 I 到 j 的最短路径中的中间顶点。如果 dist [i] [j]> dist [i] [k] + dist [k] [j]，我们将 dist[I][j]的值更新为 dist[I][K]+dist[K][j]。

下图显示了所有对最短路径问题中的上述最优子结构属性。

![](img/fe9e39bac3a34f404391e00354c3acc2.png)

**4)** **汉诺塔**

如图所示，汉诺塔是一个数学难题，由三个塔(桩)和几个圆圈组成。

![](img/7bd1fb0bf318997482f108abf1cc1e6c.png)

这些环大小不一，按升序排列，较小的环位于较大的环之上。这种谜题变体涉及盘的数量，同时保持相同的塔数。

**规则:**

目标是将所有光盘转移到另一个塔，而不干扰排列系列。以下是一些需要遵守的汉诺塔规则:

对于任何给定的时间，只有一个光盘可以在塔之间移动。

“顶部”光盘是唯一可以更换的光盘。

大圆盘不能叠在小圆盘上。

**算法:**

写一个汉诺塔的算法，首先要学会如何用较少的圆盘解题，比如一个或两个。名称、来源、目的地和辅助都写在三个塔上(只是为了帮助移动磁盘)。如果我们只有一张光盘，我们可以快速地将它从源位置传送到目标位置。

如果有两张光盘，

较小的(顶部)光盘首先被转移到辅助钉。

较宽的(底部)光盘然后被移动到目标钉。

最后，较小的光盘从 aux 移动到目的地 peg。

因此，我们现在可以用两个以上的圆盘为汉诺塔建立一个算法。这叠光盘被分成两部分。最大的盘(第 n 个盘)在一个区域，而剩余的(n-1)个盘在另一个区域。

我们的目标是将盘 n 从源移动到目的地，然后将所有其他(n1)盘复制到其中。我们可以想象用递归的方式对所有的磁盘做同样的事情。

要采取的步骤如下:

步骤 1:将 n-1 张光盘从源移动到辅助。

步骤 2:将第 n 张盘从源移动到目的地。

步骤 3:在第三阶段中，n-1 张光盘从辅助光盘到目的光盘。

**5)** **最长公共子序列:-**

最长共同子序列(LCS)被定义为所有给定序列所共有的最长子序列，前提是该子序列的元素不需要占据原始序列中的连续位置。如果 S1 和 S2 是两个给定的序列，那么 Z 是 S1 和 S2 的公共子序列，如果 Z 是 S1 和 S2 的子序列。此外，Z 必须是 S1 和 S2 指数的严格递增序列。

![](img/1ef13d184a6a04414a749417e6d3a71f.png)

在严格递增的序列中，从原始序列中选择的元素的索引在 z 轴上必须是升序。

如果 S1 = {B，C，D，A，A，C，D}

那么，{A，D，B}不可能是 S1 的子序列，因为元素的顺序不同。

**6)矩阵链乘法:-**

这是一个寻找给定矩阵序列相乘的最有效方法的优化问题。问题不在于实际执行乘法，而仅仅是决定所涉及的矩阵乘法的顺序。

矩阵乘法是相关的，因为无论乘积如何被加上括号，所获得的结果将保持不变。

![](img/604bc22f26155198e34b6282fa8dedf3.png)

例如，对于四个矩阵 A、B、C 和 D，我们将得到:

((AB)C)D =((A(BC))D)=(AB)(CD)= A((BC)D)= A(B(CD))

然而，乘积加括号的顺序会影响计算乘积所需的简单算术运算的数量或效率。