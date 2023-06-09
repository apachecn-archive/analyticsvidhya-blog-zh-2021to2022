# 创建一个自我更新的股票价格数据库

> 原文：<https://medium.com/analytics-vidhya/create-a-self-updating-stock-price-database-7c03abedc4b5?source=collection_archive---------7----------------------->

## 你下载了多少次相同的时间序列数据来回溯测试一个交易策略？如果你像我一样愚蠢的老我——太多次了……或者至少有足够的时间去写它！

![](img/3539d86b1bf61134614bfd6975b2e0fd.png)

泰勒·维克在 [Unsplash](https://unsplash.com?utm_source=medium&utm_medium=referral) 上的照片

你可能会说，像 *yfinance* 这样的大多数 API 都很快且易于使用，所以没什么大不了的。当然，大多数情况都是如此。但是，如果您想深入研究分钟间隔或任何要求您抑制 API 请求以遵守限制的场景，它确实会从一个小的不便升级为众所周知的严重问题。

如果我还没有说服你，重复下载相同的时间序列至少是一种严重的低效率，作为程序员，我们讨厌低效率，所以让我们粉碎它！

好了，废话说够了。让我们直接进入代码。

从第 50 行开始，我已经设置了基本配置，其中包括所需的列(在这种情况下，只是收盘价)，带有各自报价器的表和存储更新价格的字典。3 个金融市场中的每一个都有 2 个报价器，让您了解如何在多个表中包含多个报价器。密码，货币和股票…咳咳…股票。

第 58 行创建了我们所有重要的数据库连接。

第 60 行遍历数据库表，从那里创建一个 ticker 字符串，并传递给 *yfinance* API。

最后，第 62 行调用 *update_database* 函数，传入相应的表、tickers、数据库连接和所需的列。

*update_database* 函数首先利用 **Try** 块来检查数据库中每个表是否有任何现有价格。

如果不存在数据，将引发异常，触发除块之外的**块。在这种情况下，我们知道我们需要将开始日期设置为时间序列的开始。**

如果价格以 *db_response* dataframe 的形式从数据库中返回，代码将前进到 **Else** 块，并简单地查找我们需要更新价格的日期。

**最后是**，我们将调用 *yfinance* API 来返回一个完整的时间序列，或者一个部分的时间序列来附加到现有的时间序列，这取决于 Except 或者 Else 代码块中的哪一个运行了。

现在是自我更新的部分…

PythonAnywhere 使得在云中调度这类任务变得相对简单。也是免费的！所以继续把这个球传给你自己的虚拟版本，把你的脚抬起来！

[](https://www.pythonanywhere.com/) [## 在云中托管、运行和编码 Python:Python anywhere

### Python 是一种很好的教学语言，但是在所有学生的计算机上安装和设置它可能会…

www.pythonanywhere.com](https://www.pythonanywhere.com/) 

文档很容易理解，所以我不会把它作为 PythonAnywhere 教程。只需创建您的免费帐户，添加一个 Python 控制台和一个 bash 控制台来安装您需要的包。上传您的脚本，然后安排您的任务在每天的特定时间运行。

仅此而已。一个低接触，自我更新的价格数据库，在你的指尖为下一个交易策略做好准备，这将使你成为百万富翁！

虽然本文是在考虑财务数据的情况下撰写的，但它肯定有更广泛的使用案例。作为旁注，这也是一个很好的例子，说明如何使用完整的 Try、Except、Else 和 Finally，而不是仅仅使用 Try 和 Except。试一试，让我知道你进展如何。欢迎并感谢任何反馈！