# 流媒体即服务背后的技术

> 原文：<https://medium.com/analytics-vidhya/data-streams-2a52e3b7fdd0?source=collection_archive---------17----------------------->

对流媒体服务的需求呈指数级增长，像网飞、Spotify、Twitter、优步这样的公司希望向他们的客户提供实时服务，这将需要数据在他们的计算机网络上即时流动。他们还希望收集数据并构建对其业务流程的实时分析，以便即时做出决策。

流媒体技术让他们可以做到这一点。

![](img/8ad5ccde43e443445693a37be09af377.png)

流引擎是一种技术，能够在网络上以低延迟从 A 点到 B 点实时传输和处理大量数据。

数据流的一些应用包括

—实时音乐和视频流

—实时更新您的社交媒体源。

—实时游乐设备数据事件收集

随着对即时服务需求的增加，流技术是必不可少的。

流行的流技术包括 Apache Kafka、Spark stream、Flume、Storm 等。这些流引擎的一个共同主题是，它们能够将大量数据分解为微批处理或连续流，并即时发送到客户端，利用云的分布式计算能力进行大规模分区和处理。它为涉及高吞吐量的传输提供了低延迟。

对于 Kafka，数据被分解为发送到主题的事件(数据流的路径)，而对于 Spark stream，数据被分解为数据帧/数据集的连续流。它们通过网络发送给消费者。

一个网飞用户想要播放一部放在欧洲服务器上的电影。流引擎用于通过网络将电影数据文件从服务器发送到用户，确保播放质量不会下降(除了添加的 CDNs-内容交付网络)。

> 当这些引擎被注入机器学习时，它可以优化和调整流以适应网络带宽，youtube 使用相同的技术，这就是为什么在观看 Youtube 视频时，分辨率可以根据用户的带宽自动从 720p 调整到 480p。

网飞还使用 streams engine 收集用户视频观看活动的事件数据，并将其发送到分析仪表板。观看电影网飞公司收集视频性能、编码效率和网络效率的数据，这些数据被可视化，以帮助他们在不同地点和设备上做出服务性能决策。

优步使用流引擎在他们的应用程序上收集事件数据。当用户打开优步应用程序时，该操作会生成一系列数据事件，从骑手实际请求搭车到行程完成。

> 当司机搭载乘客时，他们的应用程序会向调度系统发送一个“搭载完成”事件，从而有效地开始行程。当司机到达目的地，并在他们的应用程序中指示乘客已经下车时，它会发送一个“行程完成”事件。这些数据事件通过流(Kafka 主题)发送到数据存储，用于未来的分析，以改进他们的服务。

此外，UberEATS 还收集了客户满意率和销售额等实时指标，使餐厅能够更好地了解其业务的健康状况和客户的满意度，从而优化潜在收入

Twitter 向用户提供最新的更新、突发新闻和相关广告，以及许多其他使用流处理的实时用例。

> Twitter 在其时间线更新管道中集成了流引擎，以向用户提供热门推文(你可能会关心的推文)。这些推文基于你互动最多的账户、你参与的推文等等。挑选热门推文的系统使用机器学习模型来预测你最感兴趣的推文。

Kafka stream engine 用于构建实时数据管道，该管道用于使用基于您的互动的最新热门推文来重新训练机器学习模型。由于用户兴趣是不断变化的，这个模型必须在一个称为刷新模型的过程中定期重新训练/更新。

使用流处理引擎，Twitter 已经成功地将更新模型的时间从 7 天减少到大约 1 天，而之前使用的是批处理。也就是说，现在所有的训练数据都是实时收集和准备的，没有任何延迟。

这使得该模型对用户兴趣的变化更具响应性和适应性，提供与兴趣变化一样快的热门推文。此外，这一变化有助于支持家庭时间表排名的内部系统变得更加敏捷、健壮和有弹性。

此外，想象一个分析仪表板从几个 POS(销售点)终端接收实时数据。流引擎从 POS 终端收集这些数据，并将其即时发送到分析仪表板以可视化数据。

我希望我能够在流引擎方面提供更多的信息。我一直在做几个流项目。

要构建流引擎，特别是使用 Kafka & Spark-Stream 这样的流行工具，Java 或 Scala 或 Python 的知识非常重要。Kafka 和 Spark Stream 支持所有功能，但 Python 在 Kafka 中的功能有限。