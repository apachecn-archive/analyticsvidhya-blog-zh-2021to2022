# 数据科学的权力结构

> 原文：<https://medium.com/analytics-vidhya/power-structures-of-data-science-65353522c8f0?source=collection_archive---------3----------------------->

提出一个框架来衡量、评估、比较和判断数据科学实践/公司和技术的效果。

![](img/ddad8cd7ecffc8300f61c50e77232172.png)

保罗·费尔胡芬电影《机械战警》中的彼得·威勒，1987 年。

数据是新的石油，还是一种永远延续你便利的观点泡沫的工具？它将有助于解决全球变暖、税收和医疗保健系统范围内的问题，还是会被用来向你出售越来越多的塑料瓶装苏打水，而你正在试图躲避两个机械战警般的私人警卫，这两个警卫现在永远生活在转基因增强的杰夫·贝索斯——他们不纳税，但作为回报，普通公民没有获得免费医疗保健。虽然这些例子看起来有些牵强，但它们捕捉到了数据的前景和陷阱之间的巨大差异——此外，从夸大特征的极端角度思考通常是有用的。
然而，可以肯定的是，我们需要建立适当的框架来检查、比较和判断数据的影响，并最终兑现承诺和避免数据科学的陷阱。在多个框架中思考也很重要。特别是，对于像数据科学这样广泛传播、多样和强大的现象，评估应该能够捕捉事物的复杂性，同时仍然提供有意义和全面的分析。在我看来，围绕数据科学的对话经常成为这两个错误的牺牲品，不可否认，这两个错误很容易犯，也就是说，它们要么提供了一个非常简单的观点，要么进入了如此小的细节，以至于没有真正的关键陈述。

为了在某种程度上解决这个问题，我想提出一个可能的框架，基于这个框架可以评估数据科学的影响/技术。框架本身是相当基本的，因此是广泛的；相对于技术而言，这是一个理论性的问题。它建立在(实际上无耻地老调重弹)米歇尔·福柯对权力的两种形式的区分之上:“纪律”和“安全”。在这篇短文中，我将只提出基本的概念，但我真的希望将来在这个基础上扩展和建立。
然而，该项目也存在不确定性。尚不清楚纪律和安全之间的区别是否在所有情况下都适用，甚至可能证明这些概念已经过时，不适合评估数据科学。然而，目前在我看来，这里存在着巨大的机会——如果结果不是这样，我也不会感到极度震惊。无论如何，我们试试吧！

# 纪律和安全

那么，我们应该如何理解纪律和安全这两个术语呢？纪律应该被理解为一种权力的系统/技术，在这种系统/技术中，个人根据这种权力本身设定的规范被监控、衡量和评估。如果天气太阴，想想学校。在学校，所有学生在课堂上的行为和表现都受到监控。在上面创建、更新和维护标签和日志。此外，根据同样的标准对儿童进行评估，并期望他们“一致化”，或者如福柯所说，“规范化”。诚然，我们很少有人依赖化学动态平衡的知识，然而，我们都被评估过(由权力本身建立的规范)。另一方面，安全性以不同的方式运作。福柯说，政府在安全方面的问题不是也不应该是如何监管人民以符合规范，而是如何治理才能对人民的愿望说“是”。他举的例子是自由放任经济。在这种安排下，个人可以自由地追求自己的兴趣，总的来说，这导致了人口的整体福利。价格波动是允许的，因此，在某些地方可能会出现短缺；然而，总体而言，这将是一种福利状态。因此，安全不像纪律那样投资在个人身上。一个人不应该遵循任何目标或规范。安全是投资在人口上的，只关心是否有足够数量的人按应该的那样行动。它通过统计数据、置信区间和接受度来运作，而不是在个人层面上的硬性规定。

# 作为混合系统的数据科学

我想提出的是，围绕数据科学构建的结构和实践具有学科和安全的双重性质。这方面的一个经典例子是社交媒体，我们不要超过你通常怀疑的 Myspace…哈哈，只是开玩笑，显然这将是脸书。因此，通常的说法是，脸书将用户置于持续监控之下，它积累了关于每个用户的数十亿字节的数据，每秒钟记录数百万个数据点。所有这些数据点都可以与个人匹配，描述他们的情绪、与他人的关系、他们关注的页面、购买模式等等。不需要指出这确实是纪律的特征:个人被广泛地测量、记录和评估他们的数据。然而，我们应该比这更进一步。虽然基于大量的粒度数据，很容易对个人进行描述和放大，但扎克伯格不太可能花时间浏览你的日志(和/或其他任何人的日志)。另一方面，纪律的一个关键特征是，它在很大程度上涉及并致力于控制个人。想想乔治·奥威尔的《一九八四年的 T2》。极权国家积极参与塑造个人。大洋国很可能在温斯顿·史密斯不崩溃的情况下继续运转；然而，这将违背纪律的逻辑。幸运的是，在脸书这样的平台上，这种控制到这种程度的渴望是缺失的。

与此同时，脸书可以说是一个按照安全逻辑运作的实体。它参与塑造用户行为，因为它足以满足其商业目的。它将对其用户进行描述和分类，以便传达相关的广告；然而，它不会强迫个人购买产品，甚至参与广告。唯一的一点是，需要足够多的人购买产品，以保持公司的收入。为此，脸书将依赖基于汇总数据的统计和概率模型，而不是与每个用户逐一接触。当然，分类和随之而来的定向广告是在个人层面上体验的，但这个过程本身并不是个性化的。即使它经常令人毛骨悚然地感觉像是真的。

基于这个非常非常非常粗略的图景，我们应该得出结论，脸书致力于塑造，或者说，惩戒个人，但还没有达到完全被定性为一个完全的惩戒系统的程度。脸书是一家商业企业，因此应该根据其资本主义逻辑对其进行评估。它的主要目的是保持收入增长，它将只在服务于其商业目的的范围内使用纪律手段(衡量、建立投资组合、分类和针对个人)。因此，它将主要依赖关于人口的总体统计数据，这些数据有接受的阈值和带宽。它不会创造一个每个人都必须被迫接受的终极标准或规范。个人可以在这个平台上自由“漫游”,然而，这个平台是经过修改的，目的是让足够多的人参与商业活动。但是(目前)没有这样做的强制措施或惩罚。

这篇短文提出的问题可能比它回答的更多。在这个所谓的纪律-安全尺度上，脸书到底在哪里？我们在哪里划定纪律界限？数据的巨大粒度以及相关算法和技术的高度复杂本质是否实际上需要个性化的控制，即使从上面看除了统计数据和概率模型之外似乎没有别的？这些都是很好的问题，但是我希望在将来解决。然而现在，我只想考虑这个单一的纪律和安全框架。我认为，每个实体或平台，甚至这些实体或平台所使用的技术，都应该在这个尺度上进行单独评估——理想情况下。比方说，脸书的做法将与 HMRC 非常不同，但它们都可以在纪律和安全的背景下进行评估，

最后，我想简要地思考一下在不同的框架上评估公司/实践/技术的重要性。首先，它需要批判性的思考，并强制澄清任何不确定性或模糊性，这有助于避免围绕这些主题的普遍混乱。它也有助于阐明组织和技术的潜在逻辑。周围的混乱表明，他们的目的和逻辑不能想当然，应该始终仔细检查。最后，通过以上所述，它应该使评估这些做法的影响更加容易，并为未来的情景/复杂情况做准备更加有效。

最后但同样重要的是，我真的要感谢你能坚持到这篇文章的结尾；我真的很欣赏你的毅力和承诺！