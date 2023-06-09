# NLP —文本编码:Word2Vec

> 原文：<https://medium.com/analytics-vidhya/nlp-text-encoding-word2vec-bdba5b900aa9?source=collection_archive---------2----------------------->

—了解 Word2Vec 的工作和直觉的博客。

![](img/23e44584aac91c783927244493c5a9c9.png)

来源:谷歌

这是我以前的 NLP 相关博客的延续，我已经在以前的博客中介绍了 NLP 的基础知识。

如果你没穿过，请在这里找: [*NLP —文本编码:入门指南*](/analytics-vidhya/nlp-text-encoding-a-beginners-guide-fa332d715854)

在我们开始之前，请记下以下几点。

*   我会把 Word2Vec 互换称为 w2v。
*   我们不打算深入研究 W2V 是如何设计的数学表达式或解释。如果你想要一个详细的演练，请参考这里的研究论文:【https://arxiv.org/pdf/1301.3781.pdf 
*   我不会太深入地研究它的深度学习方面，因为我希望这个博客是这个过程的概述，即直观的解释。

好了，现在我们有了上面提到的要点，让我们开始吧。

Word2Vec，顾名思义，就是用数值向量表示的单词。这就是需要理解的全部。主要问题是怎么做？这就是棘手的地方。别担心，让我把每件事都分成几个部分，让我们一个一个地理解它们。

## Q1:什么是 w2v？

Word2vec 是一个浅层的两层人工神经网络，它通过将文本转换为数字“矢量化”单词来处理文本。它的输入是一个大型单词语料库，输出一个向量空间，通常有数百个维度，语料库中的每个唯一单词都用生成的向量空间表示。它用于将单词的语言上下文重建为数字。单词向量在向量空间中以这样的方式定位，即共享共同上下文的单词在多维空间中彼此非常接近，用外行的术语来说，意思几乎相同的单词将被放置在一起。该模型捕捉单词之间的句法和语义相似性。

## Q2:该模型如何捕捉单词向量中的语义和句法相似性？

现在这里要解释的东西很多，我尽量简单点。

首先让我们了解一下我们如何获得两个词之间的语义？人们怎么能说把单词转换成可能有相似意思的数字可以彼此接近地表示呢？这是一些显而易见的问题，我们需要了解模型的输出，以及如何测量接近度，然后我们将继续了解这些向量是如何创建的。

让我们借助一个例子来理解这一点:

让我们用四个词:国王、王后、男人、女人。

现在，根据我们的理解，我们显然可以说，如果我想把相似的单词组合在一起，我宁愿用(国王，男人)和(女王，女人)。此外，如果我想将相反的单词组合在一起，我会用(国王、王后)和(男人、女人)来表示。

所以如果你仔细观察，国王与男人相似，与王后相反，王后与女人相似，与国王相反。

现在主要的问题是，我的向量表示，如何捕捉到这种本质？

这可能吗？是的，它是。

让我们看看怎么做。为了理解这一点，即单词中同义词和反义词的保留，我们必须理解如何比较两个向量，并得出它们在数学上是否相似的结论。我们需要两个向量之间的比较度量。

通常，我们可以将相似性度量分为两个不同的组:

1.  **基于相似性的度量:**

*皮尔逊关联*

*斯皮尔曼对射*

*肯德尔的τ*

*余弦相似度*

*Jaccard 相似度*

**2。基于距离的指标:**

*欧几里德距离*

*曼哈顿距离*

我不会深入讨论这些指标，因为我们没有学习如何计算它们。为了解释如何理解这些:两个向量越接近，它们将具有更高的相似性值和更小的距离。两个向量越远，相似度值越低，距离越大。

你可以把这想象成

1-距离=相似性或

1-相似度=距离。

相似度和距离是成反比的。

现在我们明白了如何比较两个向量的相似性。因此，如果我们以国王、王后、男人和女人为例，我们通常的理解是:

国王的词向量应该具有高的相似性得分和与男人的词向量的较低的距离，王后的词向量应该具有高的相似性得分和与女人的词向量的较低的距离，反之亦然。

为了更好地理解，它应该是这样的:

![](img/cf76e537e2e6a6ec7ddd46671b5cc4fa.png)

多维空间中的词向量

所以我们知道如何用数学方法测量单词的同义词和反义词。

现在的主要问题是，我们如何实现我们的目标向量？

## 问题 w2v 如何将单词转换成数字向量，从而保持它们的语义？

这可以通过两种方式实现，即:

1.  CBOW:尝试使用上下文单词预测目标单词
2.  跳跃式语法:尝试使用目标单词预测上下文单词。

让我们开始吧:

在我们开始之前，我们需要了解某些关键词，以及它们为何如此命名:

目标单词:被预测的单词。

上下文单词:句子中除目标单词以外的所有其他单词。

嵌入维数:我们希望我们的单词被编码到的向量维空间的数目。

举例理解:

句子:“敏捷的棕色狐狸跳过懒惰的狗”

假设我们试图预测单词 fox，那么“fox”就成了我们的目标单词。

并且剩余的剩余单词成为上下文单词。

CBOW——连续单词包，是一个我们尝试使用上下文单词来预测目标单词的过程。在这里，我们将教我们的模型学习单词“fox ”,当我们有其余的单词作为输入时。CBOW 在较小的数据集中表现良好。

跳格是一个过程，我们试图在目标词的帮助下预测语境词，这与 CBOW 正好相反。Skip-gram 在较大的数据集中表现更好。

![](img/9a8bb63a7262c164ce4745dcedbbe794.png)

来源:谷歌

在这里，输入单词被一个一个地热编码并发送到模型中，隐藏层试图从该层中关联的权重中预测最可能的单词。

我们将向量设为 300 维，因此任何单词都将被编码成 300 维向量。

我们的 w2v 模型的最后一层是 Softmax 分类器，它试图识别最可能的输出。

这个网络的输入是表示输入单词的一个热点向量，并且标签也是表示目标单词的一个热点向量，然而，网络的输出是目标单词的概率分布，而不一定是像标签那样的一个热点向量。

隐藏层权重矩阵的行实际上就是我们想要的词向量(词嵌入)！

隐藏层用作查找表。隐藏层的输出只是输入单词的“单词向量”。

隐藏层中神经元的数量应该与我们决定的嵌入维数相同。

假设我们的语料库中有 5 个单词:

句子 1:祝你愉快

句子 2:祝你过得愉快

所以没有独特的词？“有”、“有”、“好”、“棒”、“天”= 5

现在，考虑我们句子 1 的目标词是“好”

因此，如果我给我的模型输入其余的上下文单词，它应该知道“good”是它想要预测句子 1 的正确单词

考虑我们句子 2 的目标词是“棒极了”

因此，如果我给我的模型输入其余的上下文单词，它应该知道“great”是它想要预测句子 2 的正确单词

如果你仔细观察，如果我们移除目标词，句子的两个上下文词是相同的，那么模型如何准确地预测哪一个预测哪里呢？实际上这并不重要，因为它会预测出最有可能的词，在我们的例子中是“好”和“很好”，没有一个是错的。所以现在，如果你把它和我们的同义词保存联系起来，单词“good”和“great”的意思是相同的，并且是我们给定上下文单词的极有可能的输出。因此，这就是我们的模型如何学习单词的语义含义，因为在外行人看来，如果我可以互换使用单词，那么只有我的目标单词会改变，而上下文单词不会改变，任何两个具有相同同义词的相似单词都很可能是我们提供给模型的上下文单词的输出，并且彼此具有几乎相似的数值。如果它们具有几乎相似的数值，它们应该像向量一样接近，具有相似性度量和较小的距离。这就是语义是如何被捕获的。

## 问题 4:该模型如何工作？

我们将通过 4 个步骤来理解模型架构

*   数据准备
*   投入
*   隐蔽层
*   输出

这是该模型仅有的结构。

**数据准备:**

首先让我们了解数据是如何为我们的模型准备的，以及它是如何提供给模型的。

考虑上面的同一句话，“祝你有美好的一天”。该模型将该句子转换成形式为(上下文单词，目标单词)的单词对。用户必须设置窗口大小。如果上下文单词的窗口是 2，那么单词对将看起来像这样:([have，good]，a)，([a，day]，good)。有了这些词对，模型就试图在考虑上下文词的情况下预测目标词。

**输入:**

这些模型的输入只不过是一个大的独热编码向量。

让我们用例子来理解:

假设我们的数据语料库中有 10000 个唯一的单词，我们希望我们的嵌入维是一个 300 维的向量。

因此，我们的输入将是一个 10000 维的向量，所有其他单词为 0，而上下文单词保持为 1。我们的输入向量的维数是 1 x 10000。

**隐藏层:**

隐藏层只不过是一个权重矩阵，所有的单词在开始时随机地用 300 维编码。然后，我们训练我们的模型来调整这些权重值，以便模型在每个训练步骤中预测得更好。

现在，隐藏层的神经元正好等于我们选择的嵌入维数，即 300

所以我们权重矩阵的维数是 10000 x 300。

**输出层:**

输出层只是一个 softmax 层，它使用概率值来预测我们拥有的 10000 个向量的结果。我们输出向量的维数变成 1 x 300。

现在，让我们试着去理解发生在 w.r.t 维度上的数学，

输入:1 x 10000

隐藏层:10000 x 300

输出= Softmax(输入 x 隐藏层)(矩阵乘法)= 1 x n * n x dim = 1 x dim = 1 x 300

我刚才解释的上述架构是 CBOW 模型的架构，为了理解 Skip-gram，我们只需颠倒顺序，而不是输入上下文单词并找出目标单词，我们现在输入目标单词并试图找出上下文单词，CBOW 就像多输入单输出，Skip-gram 就像一个输入和多个输出。

在 Skip-gram 中，我们可以定义我们想要预测多少上下文单词，并相应地创建输入输出对。

例如:“祝你有美好的一天”

如果我们将窗口大小设置为 2，那么训练对将是；

目标词:好

语境词:有，一，一天

(好，有)

(好，答)

(好，天)

因此该模型学习并试图预测接近目标单词的单词。

## Q5:将单词转换成矢量的目的是什么？

这些词向量现在很好地配备了嵌入其中的句法和语义含义，因此它们可以完美地用作任何其他复杂 NLP 程序的输入，其中我们想要理解复杂的人类对话或语言上下文。

W2V 本身是一个神经网络，但是它在处理与 NLP 相关的应用程序之前在特征工程层工作。

**实施:**

我们不会从头开始学习如何实现 w2v 模型，因为我们已经有了 [*Gensim*](https://radimrehurek.com/gensim/) 库，如果你有自己特定的面向领域的数据语料库。

或者，如果你正在处理普通的英语语言文本数据，那么我会建议你查看斯坦福大学从数十亿维基百科、推特或普通抓取文本中创建的 [*GloveVectors*](https://nlp.stanford.edu/projects/glove/) 。

**结论:**

我们现在对单词嵌入有了更好的理解，并且熟悉了 Word2Vec 的概念。我们理解 Skip-Gram 和 CBOW 之间的区别。我们也直觉地知道单词嵌入是如何创建的，隐藏层是一个巨大的单词嵌入查找表。我们也有一个要点来理解语义和句法意义是如何被捕获的。单词嵌入具有非常有用的潜力，甚至是许多 NLP 任务的基础，不仅是传统文本，还有基因、编程语言和其他类型的语言。

下一次我们将研究文本的 BeRT 编码，直到那时快乐学习！

> **感谢阅读！**
> 
> 如果你想了解更多类似的话题或者看看我还能提供什么，一定要访问我的网站:[所有关于东西](https://digital.allaboutstuffs.com/)
> 
> 准备好让你的学习更上一层楼了吗？查看我提供的课程:[课程](https://digital.allaboutstuffs.com/courses/)
> 
> 生活工作压力大？花一点时间来放松和放松我的舒缓和放松的视频！现在就去我的频道，用"[灵魂镇定剂](https://www.youtube.com/c/TheSoulTranquilizer)"开始你的内心平和与宁静之旅