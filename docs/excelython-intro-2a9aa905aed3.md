# Excelython —简介

> 原文：<https://medium.com/analytics-vidhya/excelython-intro-2a9aa905aed3?source=collection_archive---------25----------------------->

![](img/23687057a3adb2bf7fbfe61ccafd04ed.png)

非常感谢

我记得，5 年前，我不得不处理一个情况，我团队中的一个关键角色将要离开。在此期间，我们有一个流程，每天 4 次，这个角色下载四个不同的 excel 文件，将它们合并成两个新文件，然后将它们上传到主(怪物)文件 excel 中，其中有许多公式在 15 分钟后得以更新。在处理之后，还有一部分是将公式拖到新行，并使用过滤检查公式的计算中是否有错误，或者是导致一些错误的误导性过滤。无论如何，这个过程在一天中的每一个循环都需要大约一个半小时。除了时间消耗，一个有经验的用户很容易理解，在过去的几年里，我们不得不处理这个过程中产生的许多错误。

回到我必须处理的情况，正如你所理解的，问题是我必须立即找到一个替代者，必须对他/她进行培训和监督，直到他/她能够以同样的速度操作。但是在此之前，我必须找到一个临时的解决方案，因为团队中没有人能够以同样的效率做同样的工作。

在这一点上，一篇文章出现在我的观点上，是关于那本传奇的书，“[用 Python](https://automatetheboringstuff.com/) 自动化枯燥的工作人员”。

没有以前的编码经验，但有解决上述情况的巨大需求，我想出了一个决定:我不会取代这个角色，我会创建一个替代品。

第二天，我开始谷歌如何安装 python，并在 YouTube 上查看了一些快速入门教程。我设计的学习曲线，并不是要成为一个全栈 Python 开发者，而是如何命令 Python 去复制这个角色正在做的所有步骤。

记得我在 Google 写的第一个问题:“如何用 Python 打开 excel 文件？”。我花了大约 2 个小时来配置回复如下。

```
file1 = pd.read_excel("path_of_file", encoding="utf-8")
```

就一行代码，真的很好理解。在你输入的人类文字中，阅读位于这个路径中的=_ excel，并请对特殊字符进行编码(在我的例子中是希腊字母)，这样它们就可读了。

*****在较新的版本中，不需要添加编码部分，因为它已经过时。*

即使我花了两个小时来寻找上面的答案，这也极大地鼓舞了我的士气，因为我明白如果剩下的事情都这么简单，那么我就能创造出我的第一个机械团队成员。

因此，在接下来的 3 天里(40 个小时)，我继续用谷歌玩问题游戏，用 excel 做每一个动作。

我最终得到了一个 3000 行代码的脚本，并在 2 分 15 秒内完成了所有工作，没有任何拖放错误！！！！！！！！！！！

兴奋是如此之大，以至于在那之后，我们在下个月升级了脚本，在一定程度上，为业务产生的信息、我们决策中的智能以及它用于所有这些的时间消耗，成功地克服了我们不是用一个团队成员而是用至少 4 个人的团队可能得到的结果。

另一件好事是，我们确实把可以花在 4 个人身上的钱投资到了系统和人员上，从而提高了团队的生产力和质量。

现在，如果你有兴趣打开一些日常事务自动化的大门，你可以关注我的 business view 教程，如“我如何用 Python 做 vlookup”或“我如何用 Python 保存 excel 文件并将其作为附件发送”，或者你可以像一个 5 岁的孩子一样开始询问 Google。

无论如何，你将进入一个质量和工作幸福的新世界。

玩得开心点！！

## [**转到第 1 部分**](https://servos-yiannis.medium.com/excelython-part-1-install-python-and-ide-c09f723b232f)