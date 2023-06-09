# 如何有效地用代码解决问题:过程

> 原文：<https://medium.com/analytics-vidhya/bare-minima-how-to-solve-any-problem-with-code-b6fb934c7899?source=collection_archive---------17----------------------->

![](img/45b69ef47ed63ef346cc93bda9698a64.png)

如今，几乎任何技术问题都可以通过创造性编程来解决，然而有时很难看出这是怎么回事。有些问题本质上很简单，比如获取用户输入和输出信息，但是较大的应用程序(比如社交媒体应用程序)需要更多的思考。在这篇文章中，我将概述用于将复杂的想法转化为工作应用程序的常用方法。这些方法也经常作为学校课程的一部分教授，如果你曾经上过计算机科学或类似的学科，你可能对它们很熟悉。

# 抽象

抽象的核心是一个非常简单的概念，你可以把问题中所有不必要的细节都去掉，而选择关注最重要的细节。虽然这似乎是显而易见的，但在处理一个更大、更复杂的项目时，很容易关注错误的细节并偏离主题。规划和缩小应用程序设计的核心组件可以大大提高开发过程的效率。

当以某种方式模拟现实时，抽象是最有用的。在社交媒体应用程序的例子中，可以清楚地看到，作为软件开发人员，我们可能并不特别关心人们如何或为什么成为朋友，只关心他们是朋友，并使用这些模式来推荐新朋友。这些友谊的内部工作应该无关紧要，因为它们对代码的运行几乎没有影响。抽象中更常用的例子是，为了可读性和用户体验，每个地图都省略了某些细节。这不会使地图变得不准确，因为它只是被调整以使导航更容易。

# 分解

分解是把一个大问题分解成几个组成部分的过程。这在应用程序的规划过程中也非常有助于决定操作顺序。将小部分分解成整体确实有助于分解一个复杂的项目。这确保了您可以从一个小模块开始，并在此基础上创建最终结果，而不是一头扎进一个不知道从哪里开始的大项目。这也可能是决定你正在构建的应用程序的优先级的时候。分解可以进一步分解为发布时必须拥有的部分，你应该拥有的部分和你可能拥有的部分。这就产生了必要性的层次，并且意味着，作为一个开发者，你可以在转移到不太紧急的部分之前，优先考虑那些被认为是绝对必要的部分。虽然，这似乎是显而易见的，对某些人来说是自然而然的，但是学习遵循这个过程是有好处的，因为它可以非常快速地将项目带到起点，甚至使编码过程大大加快。

通过将应用程序分成页面或小部件，可以将分解应用于社交媒体应用程序的示例。这可能包括朋友系统、消息页面、提要和发现新朋友的方法。考虑到这个具体的例子非常复杂，这些部分可以进一步分解。例如，消息传递页面将包括消息发送过程、消息接收过程、通知过程，甚至可能包括图像发送和接收处理程序。将这些部分分解到最底层有助于了解如何在没有清晰工作流程的情况下进行大型项目。

# 模式识别

模式识别是指大多数程序，特别是当它们的范围变得更大时，在它们的设计或代码中倾向于有一些模式。通过利用类和函数，这种类型的重复可以为开发人员带来好处，使程序更容易编码。

再次以社交媒体应用程序为例，将要重复的主要模式是应用程序用户的个人资料。很可能每个用户都有相同类型的详细信息，尽管各个值会有所不同。这允许为用户概要文件创建一个类，其中可以为需要在应用程序中显示的每个用户创建这个概要文件的一个新实例。这样，模式识别可以帮助减少程序员编写的代码量，同时也使代码更容易理解。

# 算法规划

虽然这个过程通常不一定是一步一步的过程，但实际将代码提交到文件之前的最后一部分往往是算法规划。这是确保项目能够正常运行的重要一步，只需简单地将上述所有步骤的结果，按照它们发生的顺序，进行，并产生已经决定的部分的算法表示。如果做得正确，这些部分中的每一个在规模上都应该相当于一个简单的项目。知道分解到什么程度很大程度上是基于经验，随着时间的推移，你会了解需要多大的块。

# 结合

这个抽象、分解、模式识别和算法创建的过程只有在所有这些都做到足够好的程度时才真正起作用。无论如何，我不认为这应该是一个严格的政策，但是当我开始一个项目时，我总是把它放在我的脑海里，因为它会让我走上完成的轨道。我的过程通常包括遵循这些步骤，无论是在纸上还是在我几天的头脑中，然后列出我已经决定的算法或部分。这些通常被写成描述而不是伪代码，因为这是我更喜欢的，在每一个都被转换成代码和单独测试之前，它们被集成到最终的程序中。

*最初发表于 2021 年 1 月 09 日*[*【https://kgdavidson.co.uk】*](https://kgdavidson.co.uk/codespertise--how-to-solve-any-problem-with-code/)*。*