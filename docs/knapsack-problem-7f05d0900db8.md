# 背包问题

> 原文：<https://medium.com/analytics-vidhya/knapsack-problem-7f05d0900db8?source=collection_archive---------0----------------------->

## 求解背包问题的不同方法

在解决动态规划问题时，我遇到了背包问题。是每个程序员必须解决的标准问题之一。在这篇文章中，我将讨论背包问题到底是什么以及有哪些不同的方法可以用来解决这个问题。

> 给定 n 个物品的重量和价值，将这些物品放入容量为 W 的背包中，以获得背包中的最大总价值

换句话说，0/1 背包问题的陈述可以解释为，给定两个整数数组 val[0..n-1]和 wt[0..n-1]分别表示与 n 个项目相关联的值和权重，以及表示背包容量的整数 W，找出 val[]的最大值子集，使得该子集的权重之和小于或等于 W。不能分解一个项目，要么选择完整的项目，要么不选择它(0–1 属性)。

![](img/bdade823a09538e69fa53e75037dfe68.png)

因此，在这个问题中，给我们一组物品，每个物品都有重量和价值，我们必须确定要包含在集合中的每个物品的数量，以便总重量小于或等于给定的限制，并且总价值尽可能大，也就是说，我们必须通过选择要包含在背包中的物品来使利润最大化。

## 背包问题的求解方法

虽然你会发现这个问题作为一个动态规划的例子，各种算法可以用来解决这个问题，即贪婪算法和分支定界算法。在本节中，我将简要讨论所有这些方法(包括动态编程)，并对它们进行比较，以找到最有效的算法。

## 1)动态编程:

动态算法是一种算法设计方法，可以在问题分解成更简单的子问题时使用。只要存在对相同输入进行重复调用的递归解决方案，就可以使用动态编程对其进行优化。***其思想是简单地存储子问题的结果，以便以后需要时不必重新计算。*** 这种算法因此利用了整体问题的最优解依赖于其子问题的最优解这一事实。这种简单的优化将时间复杂度从指数级降低到多项式级。它解决了显示 0–1 背包问题中存在的 [***重叠子问题***](https://www.geeksforgeeks.org/overlapping-subproblems-property-in-dynamic-programming-dp-1/) 和 [***最优子结构***](https://www.geeksforgeeks.org/optimal-substructure-property-in-dynamic-programming-dp-2/) 的性质的问题。

![](img/f2ad7b4ba49319246d52fb46171a1094.png)

使用动态规划寻找最佳解决方案的示例。

时间复杂度 **:** **O (N*W)。**
其中“N”是重量元素的数量，“W”是背包的容量。

## 2)贪婪算法:

Greedy 是一种算法方法，它一点一点地构建解决方案， ***总是选择下一个提供最明显和直接利益的方案*** 。所以选择局部最优解也导致全局解的问题最适合贪婪算法。该方法主要用于[分式背包问题](https://www.geeksforgeeks.org/fractional-knapsack-problem/)。这个问题中贪婪方法的基本思想是计算每个项目的比值/重量，并根据这个比值对项目进行排序。然后取比率最高的项目，把它们加起来，直到我们不能把下一个项目作为一个整体加起来，最后尽可能多的加下一个项目。这永远是这个问题的最优解。

但是贪婪算法并不总是给出 0/1 背包问题的最优解，因为该算法并不总是考虑整个目标，而是也可以考虑目标的一部分，以保持背包的容量并最大化利润。但是在 0/1 背包问题中，我们不能考虑对象的一部分，只能考虑整个对象。由此可见，贪婪方法并不总是保证 0/1 问题的最优解，但对分数问题有效。

时间复杂度: **O(n*logn)**

如果使用简单的排序算法(选择、冒泡),那么整个问题的复杂度是 O(n)。

如果使用快速排序或归并排序，那么整个问题的复杂度是) **O(n*logn)。**由于主要的耗时步骤是排序，整个问题只能在 **O(n*logn)** 中解决。

## **3)分支定界算法:**

一个[分支定界算法](https://www.geeksforgeeks.org/branch-and-bound-algorithm/)基于两个主要操作:分支，即将要解决的问题分成更小的子问题，这样就不会丢失任何可行解；和界，即计算当前子问题的最优解值的上界(对于最大化问题),从而最终可以求解该子问题。

该算法基于状态空间树。状态空间树是树的根，其中每一层表示依赖于上层的解决方案空间中的决策，并且任何可以想到的解决方案都由从根开始到叶子结束的几种方式来表示。根停留在 0 级，代表没有不完全解的状态。一片树叶没有年轻人，它代表了一种状态，在这种状态下，构成一个答案的所有决定都已经做出。

![](img/14e5cbe736302f3c12fb70dab1592d16.png)

强力法可以通过回溯来改进。如果我们知道最佳可能最优解的界限，使得分支定界法比回溯法或强力法更好，那么回溯法可以进一步改进。

时间复杂度 **: O(2n)**

在最坏的情况下，算法将生成所有中间阶段和所有叶子。因此，树将是完整的，那么时间复杂度= O (2n)

## 结论:

贪婪算法似乎是最有效的(时间复杂度)，但是它不能给出 0/1 背包问题的正确最优解。动态规划技术也是非常有效的，并且通常是解决 0/1 背包问题的最有利的算法，但是在所考虑的三种方法中，该技术所利用的存储器是最高的。因此，在这三个背包问题中，最有效的方法是分支定界技术。该方法简单易行，可用于解决所有情况下的背包问题。

上面给出的文章总结了我对 0/1 背包问题的了解。虽然它没有涵盖一切，但它可以给人一个关于问题的基本概念和解决问题的不同方法。希望这有所帮助！

> 本文参考—【https://www.geeksforgeeks.org/0-1-knapsack-problem-dp-10/】T2，0/1 背包问题算法的比较与分析