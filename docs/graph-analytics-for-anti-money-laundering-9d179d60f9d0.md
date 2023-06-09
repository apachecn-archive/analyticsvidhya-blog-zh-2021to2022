# 反洗钱图表分析

> 原文：<https://medium.com/analytics-vidhya/graph-analytics-for-anti-money-laundering-9d179d60f9d0?source=collection_archive---------0----------------------->

![](img/c27c073da4f4f6e2923a39ca0214df47.png)

照片由[法比奥](https://unsplash.com/@fabioha?utm_source=medium&utm_medium=referral)在 [Unsplash](https://unsplash.com?utm_source=medium&utm_medium=referral) 上拍摄

邪恶的行业依靠复杂的洗钱计划来运作。洗钱被称为将犯罪所得转化为干净合法资产的过程，是世界各地普遍存在的现象。由于涉及银行或合法企业的转移，非法获得的资金通常会被“清洗”。这是金融犯罪领域最难发现的活动之一。这往往与恐怖主义、毒品和武器贩运以及剥削人类联系在一起。资金通过标准的金融工具、交易、中介、法律实体和机构在众目睽睽之下流动，避免被银行和执法部门发现。

人们通常从合规的角度来看待反洗钱，因为取证分析的负担主要落在金融机构(FIs)身上，金融机构负责满足“了解您的客户”( KYC)标准、监控交易、关闭或限制可疑账户，并及时向执法机构提交可疑活动报告(SARs)。监管罚款的成本和金融机构受损的声誉都是实实在在的。

在过去的几十年中，大多数可疑活动都是通过考虑客户常规交易流程中的异常情况来识别的:随着时间的推移，行为模式和趋势会得到比较，以发现意想不到的变化。

基于规则的分类方法是常见的。其他研究使用贝叶斯方法，或者为客户行为分配风险分数，也考虑这种行为的演变，或者更一般地，将贝叶斯规则与关于过去操作历史的数据库信息相结合，优于其他模糊技术。

机器学习算法也被应用于相同的一般目的:集成分类器、决策树、神经网络、贝叶斯网络和聚类算法，以检测纳税人的虚假发票。当时人们认为集群技术是最好的解决方案。相比之下，机器学习方法的局限性得到了大量讨论，例如识别依赖于数据的参数的问题，有时具有有限的适应性和可扩展性，错误分类的风险，类别不平衡问题或解释潜在行为模式的困难。

最近的研究将注意力集中在关系数据上，以揭示新的模式并超越传统方法的一些限制。金融机构需要依赖易于应用和理解的规则，同时需要更复杂的方法，这应该很难避免，而不是依赖预先建立的众所周知的规则，这些规则可能容易被回避。

图表分析作为一种支持反洗钱分析的理想技术已经成为前沿，因为洗钱涉及实体之间的现金流关系(即网络结构)。图表克服了在大量、复杂和相互关联的数据中揭示关系的挑战，是从头开始设计的。

许多反洗钱用例需要识别可疑连接，而图形分析旨在从大规模大数据中分析复杂的连接。可以构建多种图形类型。可以形成一个图，其中单个账户被表示为顶点，两个账户之间的单个交易被表示为边。另一种方法是将一组账户表示为顶点(例如，诸如控股公司下的账户，或者诸如通过聚类推断为共享所有者的账户)，并将边定义为在一段时间内与相邻节点的总交易量。

反洗钱领域存在一系列核心问题，这些问题带来了挑战，需要图形分析能够解决的解决方案。

一个例子是**识别政治公众人物** **和制裁甄别**:金融机构的任务是甄别其客户，以确定他们与政治公众人物(pep)或制裁名单(如外国资产管制办公室公布的名单)上的个人和组织的潜在联系。这些人意味着洗钱风险增加。客户和风险实体之间的关系可以简单到客户和政治人物共用同一个地址。在这种情况下，检测这种情况很容易。如果风险实体真的想参与洗钱，该怎么办？很有可能会花很大力气隐藏这些关系，以逃避强化尽职调查。图形分析可以跨多种类型的实体和关系(地址、共有公司、IP 地址、电话号码、交易等)识别这种间接关系。).

另一个例子，**实体解析** (ER)是数据库中每个人或公司都是唯一的问题。尽管有可能情况并非如此。也许零售银行数据库中的戴维·约翰逊与消费者信用数据库中的戴维·约翰逊或公司所有者数据库中的戴维·约翰逊具有不同的 id，尽管这三个人实际上是同一个人。在具有不同筒仓的 IT 系统中，避免这种重复是一个复杂的问题。图形分析可以检测不同实体之间的常见链接，以帮助识别潜在的重复项。也许即使三个戴维·约翰逊有不同的身份证，他们都有相同的出生日期，相同的地址和相同的电话号码。如果是这样，很有可能他们确实是同一个人。

**最终受益所有权** (UBO)是金融机构负责识别 UBO 的另一个有趣例子。这些人拥有客户，或代表客户进行交易。有时，这需要通过考虑相关的所有权阈值来遵循一个很长的所有权关系链。如果一家公司由单一股东所有，事情就好办了。当所有权层数增加时，事情就变得棘手了。手动查看每家公司的所有权结构以确定其 ubo，并重复该过程直到没有新的 ubo，这是一个耗时且容易出错的过程。这种类型的分析可以转化为一个单一的图形查询，以自动化的过程。结果也可以被可视化。例如，合规分析师可以查看总体所有权图，以确定有问题的 UBO 位于何处。

# 结论

图表分析有助于发现洗钱活动的案例不断增加。随着犯罪分子洗钱的方式越来越复杂，帮助他们反击的工具也越来越复杂。当金融机构配备了图表分析工具时，洗钱活动就没有机会了。

# 关于漂亮的活动

NICE Actimize 是为地区和全球金融机构以及政府监管机构提供金融犯罪、风险和合规解决方案的最大和最广泛的提供商。NICE Actimize 专家在该领域一直排名第一，他们应用创新技术来保护机构，并通过识别金融犯罪、防止欺诈和提供法规遵从性来保护消费者和投资者的资产。该公司提供实时、跨渠道的欺诈防范、反洗钱检测和交易监控解决方案，解决支付欺诈、网络犯罪、制裁监控、市场滥用、客户尽职调查和内幕交易等问题。