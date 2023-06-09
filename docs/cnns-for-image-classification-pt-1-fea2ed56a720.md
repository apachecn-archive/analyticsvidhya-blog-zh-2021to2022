# 图像分类的细胞神经网络。一

> 原文：<https://medium.com/analytics-vidhya/cnns-for-image-classification-pt-1-fea2ed56a720?source=collection_archive---------14----------------------->

![](img/2d65206a41f1f63cb98415cbd09f1fff.png)

萨姆·帕克在 [Unsplash](https://unsplash.com?utm_source=medium&utm_medium=referral) 上拍摄的照片

使用卷积神经网络，有可能使用机器学习来分类图像。我最近在做一个项目，目标是训练一个模型，根据一张图片预测一个视频游戏的 ESRB 评分。该项目背后的基本原理是，使用这样的模型可能有助于标记 YouTube 或 Twitch 等平台上可能的成熟内容。

CNN 经常用于图像分类项目，但是对于这个项目，我担心分类可能太模糊。我没有要求模特在照片中识别任何特定的物品或形状。我让它来评估图片中描绘的游戏是否适合年轻观众。看着截图，我自己也找不到任何可靠的分类方法。我找不到任何可靠的蛛丝马迹，我自己的预测准确度也令人沮丧。自然，我只是对训练过程持谨慎乐观的态度。

然而，在你进行任何类型的训练之前，你需要数据。在这里，我将概述我为这个项目收集数据的过程。

*   标题和评级:在收集图片之前，我需要知道要寻找哪些游戏的图片，以及这些游戏的评级。我通过使用 python 的 Selenium 库从 ESRB 网站上搜集为 Xbox One、PlayStation 4 和任天堂 Switch 发布的每款游戏的标题和评级来实现这一点。有了这个，我希望收集一个相当现代游戏的合理规模的数据集。这些信息随后被储存在熊猫数据库中。我将展示下面的代码。

*   图片:将标题和评级的数据框架放在一起后，我再次使用 Selenium 从 Google Images 中提取图片。使用 DataFrame 来指导 Selenium 的搜索查询，我为数据集提取了每款游戏的 10 张图片。每个图像都保存在特定于其等级的目录中。同样，我将在下面展示我的代码。

*   数据分割:在将所有这些图像收集到四个目录中之后，我需要将它们分成训练集、验证集和测试集。这些验证和测试集对于确保模型不会过度适应训练数据非常重要。我用来分割数据的代码如下所示。

完成所有这些后，我为每个标题准备了 10 张图片。“图像”目录包含训练/val/测试分割中每个集合的子目录。这些子目录中的每一个都包含每个评级的子目录。以这种方式保持数据的良好组织将使下一步向模型提供数据变得更加容易。

我将在第 2 部分中介绍该项目的建模部分，在那里我将详细介绍使用 Keras 构建卷积神经网络。我将展示如何使用 Keras 的 ImageDataGenerator 使用批量图像数据来训练 CNN 模型。虽然它肯定不会是对 Keras 或 CNN 的详尽全面的指南，但它有望成为快速启动和运行您的模型的有用指南。