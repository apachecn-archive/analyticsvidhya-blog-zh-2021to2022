# 数据编排的内容、原因和时间

> 原文：<https://medium.com/analytics-vidhya/the-what-why-and-when-of-data-orchestration-2f128746b5ac?source=collection_archive---------16----------------------->

关于数据编排和 2021 年流行的框架，你需要知道的一切。

![](img/396f7173fca9fe2fe5be4749a453b9c5.png)

[万圣业](https://unsplash.com/@wansan_99?utm_source=medium&utm_medium=referral)在 [Unsplash](https://unsplash.com?utm_source=medium&utm_medium=referral) 上的照片

当大多数人听到配器这个词时，他们会想象一个管弦乐队在演奏交响乐。在每个管弦乐队的前面都站着一个指挥，他挥舞着手臂，提示管弦乐队中的所有乐器，以便它们同步定时。最终，观众可以享受到统一的音乐视觉和适当的强度。

你会问，为什么用这个比喻。嗯，将数据转化为实际的、有价值的信息也需要一个指挥。过去，大多数数据接收都是作为预定批处理作业的一部分在夜间完成的，但云改变了这一切。在过去的几年中，许多数据编排框架已经问世，并成为现代数据堆栈的重要组成部分。但是在深入研究编排解决方案之前，让我们先了解一下数据编排及其对数据分析的重要性。

# 数据编排到底是什么？

尽管这个词相对来说还是个新词，但在过去几年里，它的势头越来越大。这里有一些很好的理由。如今，数据的增长仍然是前所未有的，来自无数的来源。越来越复杂的跨各种生态系统的数据移动使管理变得非常困难，这种逆趋势将在未来继续。因此， [Gartner 的研究](https://www.gartner.com/smarterwithgartner/gartner-top-10-trends-in-data-and-analytics-for-2020/)表明，到 2025 年，75%的企业的人工智能需求将显著增加数据量。数据编排是组织保持领先的方法。

此外，数据是与资本资产和知识产权一样重要的资产。而且数据越多，越难管理。这就是为什么企业需要新的方法来移动和编排数据。

本质上，数据编排指的是消除数据孤岛，这样您的数据就不会到处都是，可以按需输入。实际上，如果一个组织能够很好地处理数据，它就不需要数据编排。但是由于不断发展的技术和不断增长的数据海洋，这几乎是不可能的。

正在讨论的概念通常描述了一组技术，这些技术自动化了数据驱动的流程，虚拟化了所有数据，并通过带有全局命名空间的标准化 API 将数据呈现给数据驱动的应用程序。它还要求集中控制跨不同系统、数据中心或数据湖管理数据的流程。因此，IT 团队能够创建和自动化包括整个组织的数据、文件和依赖关系在内的全范围流程，而无需编写自定义脚本。

对于大多数拥有各种数据流的公司来说，数据编排是一个安全的选择，因为它不需要对数据进行任何大规模的迁移，而这通常会引入另一个数据孤岛。除此之外，数据编排还有助于遵守数据隐私法，消除数据瓶颈，并增强数据治理。

# 数据编排框架——数据世界中缺失的一块

尽管企业继续投资于数据科学和人工智能技术，但他们仍然难以理解即将到来的价值。此外，大多数公司可能有微调的方法，但没有对数据进行尽职调查的工具或技术。因此，企业最终会将整个数据周期委托给手动流程，从而产生冗余。数据编排框架通过创建一个配有自动化工具的理想数据科学环境，有助于将所有这些结合在一起。—可以是开源的，也可以是专有的，从而使整个过程真正自动化。编排框架提供的一些功能有:

*   作业调度
*   依赖性管理
*   错误管理和重试
*   作业参数化
*   SLA 跟踪、警报和通知
*   元数据的数据存储，等等。

管理依赖关系的最流行的框架有 *Apache Airflow、Ozzie 和 Lugie* 。让我们仔细看看他们中的每一个，看看是什么让他们如此受青睐。

# 阿帕奇气流

Apache Airflow 是一个多功能的工作流管理器，已经成为任何知识渊博的数据工程师的工具箱。如果你查看数据工程师职位的空缺，你会发现气流经验是该职位的要求之一。

它于 2014 年开发，是一个开源工具，允许您开发、计划和监控复杂的工作流程。主要区别在于它使用 Python 编程语言来描述流程。这个特性为您管理项目和开发提供了许多优势。因此，它将您的 ETL 项目转换成一个简单的 Python 项目，这样您就可以根据基础设施、团队规模和其他需求，随心所欲地改变它。从技术角度来说，也很简单。比如可以用 PyCharm + Git。

Apache Airflow 中的主要工作流实体包括:

*   有向无环图。
*   调度程序
*   经营者
*   任务

这个框架还可以编排复杂的机器学习工作流。而且可以用插件大量定制。这就是为什么它受到数据工程师和数据科学家的青睐。

# 驭象者

Apache Oozie 是一个 orchestrator，以其与 Hadoop 堆栈的紧密集成而闻名。它包含在 Cloudera 和 Hortonworks 最大的 Hadoop 发行版中。实质上，Apache Oozie 是一个基于服务器的工作流调度系统，用于管理 Apache Hadoop 作业。

像 Apache Livy 一样，Oozie 中的工作流被表示为 DAG 链(有向无环图)。该框架支持运行 Hadoop MapReduce、Apache Hive、Pig、Sqoop、Spark、HDFS 操作、UNIX Shell、SSH 和电子邮件任务，并且可以扩展以支持其他操作。可以将任务设置为定期运行或在某个事件发生时运行一次。Oozie 本身是作为运行在 Java servlet 容器中的 Java web 应用程序实现的，并在 Apache 许可下分发。

Oozie 一开始看起来很可怕，因为它完全由 XML 驱动，当出现问题时很难调试。然而，一旦你掌握了它，它会创造奇迹。对于调度 Hadoop 作业来说，它非常强大，支持管道中的大量操作节点，并管理复杂的依赖关系。

Oozie 框架的另一个优势是它与 Apache Hadoop 堆栈完全集成，并支持 Hadoop 作业。它还可以用于调度特定于系统的作业，如 Java 程序。Oozie 允许 Hadoop 管理员创建复杂的数据转换，这些数据转换可以组合各种单独任务的处理，甚至是作业的子线程。这一功能提高了复杂任务的可控性，并使得以预定的时间间隔重复这些任务变得更加容易。

# 路易吉

Luigi 是另一个使用 Python 描述任务图的 orchestrator。最初创建它是为了在基于 Apache Hive、Spark 和其他大数据技术的推荐系统中运行复杂的管道。Luigi 在 2012 年成为 Apache 2.0 许可下的开源项目。

这个框架允许您构建批处理作业的复杂管道，并管理依赖关系解析、工作流管理、可视化等等。Luigi 还设计为通过将工作流呈现为 DAG 管道来管理工作流。这个框架比 Airflow 更容易使用，但是功能更少，限制更多。

然而，截至 2020 年底，Apache AirFlow 被认为是自动化大数据管道编排的领先数据操作工具。这是因为它专注于大型生产解决方案和许多其他优势。

# 选择什么管弦乐队

与每个解决方案提供的基础设施和复杂性相比，您选择的编排框架将主要基于您的目标。

要缩小搜索范围，请仔细阅读以下几点:

*   您是否需要移动和转换大数据的功能？通常，这将涉及几千兆字节到兆兆字节的数据。如果是，请选择最适合大数据的选项。
*   您是否需要能够以适当规模运营的托管服务？如果是，选择一个不受本地计算机计算能力限制的基于云的服务。
*   有些数据源是本地托管的吗？如果是，请选择可用于云和本地数据源或目标的选项。
*   源数据是否放在 HDFS 文件系统的 BLOB 对象存储库中？如果是，请选择支持配置单元查询的选项。

# 底线

在向真正的数据驱动型数字业务转型的过程中，企业面临着管理错综复杂的数据结构的挑战。这就是管弦乐队成为焦点的时候。任何数据编排平台的主要目的都是揭示杂乱的数据。就像唱诗班指挥一样，指挥者允许每个数据点在一定范围内与其他信息同步。