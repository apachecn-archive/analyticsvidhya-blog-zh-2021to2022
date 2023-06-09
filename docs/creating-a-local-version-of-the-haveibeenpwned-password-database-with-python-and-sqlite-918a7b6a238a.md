# 创建本地版本的 Haveibeenpwned 密码数据库(使用 Python 和 SQLite)

> 原文：<https://medium.com/analytics-vidhya/creating-a-local-version-of-the-haveibeenpwned-password-database-with-python-and-sqlite-918a7b6a238a?source=collection_archive---------3----------------------->

在这篇文章中，我们将展示如何创建一个本地版本的 Haveibeenpwned 密码数据库。这可以用来检查密码的安全性，而不需要互联网连接。

什么是 Haveibeenpwned？

Haveibeenpwned 是安全研究员特洛伊·亨特(Troy Hunt)创建的一个网站，收集数据泄露造成的泄露凭证。作为一个用户，你可以输入你的电子邮件地址，然后找出它是否已经被列入数据违规。[你也可以用同样的方法测试你的密码](https://haveibeenpwned.com/Passwords)。

如果密码包含在漏洞中，应立即更改。

**地方版有什么意义？**

Troy Hunt 是一名世界知名的安全研究员，该网站的安全性非常好。然而，在这个网站上简单地输入你的密码的想法对一些人来说可能听起来很奇怪。也许这种检查也因某些公司准则而变得困难或不可能。

作为替代，还有一个[haveibenpwned API](https://haveibeenpwned.com/API/v3)。这样，您可以在自己的计算机上用 SHA-1 散列您的密码，然后只将散列的前 5 个字符传输给 API。然后，API 用一个以这 5 个字符开头的所有散列的列表来响应。平均来说，你会收到 400 份回复。有了这些，你现在可以在你自己的计算机上检查它们中是否有一个与原始密码散列相对应。

这实际上是一个不错的解决方案，但是如果攻击者设法实施中间人攻击，他可能会读出 API 回复。然后，他可以尝试哈希传递攻击，或者尝试用彩虹表破解 400 个响应。

与本地版本，另一方面，没有密码或哈希在网络上传输，一切都发生在你的电脑上。

**你需要什么？**

基本上，你需要三样东西:

**良好的互联网连接:**目前，最小的文件(NTLM 格式，按哈希排序)为 8.5GB。最大的文件(SHA-1 格式，按流行程度排序)甚至为 12.5GB。因此下载可能需要一段时间。

**存储空间:**解压后的文本文件大约 20GB。如果我们直接在这个文本文件中搜索密码，将会花费非常长的时间。为了确保快速查询，我们需要一个数据库。为了进一步优化，我们使用指数。但是，这也大大增加了数据库的大小，因此您应该计划大约 50GB 的空闲内存。

**Python:** 我用的是 Python 3.9，不过应该也能用其他 3。x 版本。好的一面是 Python 安装已经包含了 SQLite，所以我们不需要安装额外的数据库**。**

**第一步:下载文本文件**

在页面[https://haveibeenpwned.com/Passwords](https://haveibeenpwned.com/Passwords)可以下载密码散列。SHA-1 和 NTLM 版本可用，这是根据哈希或流行程度排序。

因为我们用 SHA-1 还是 NTLM 散列对我们来说并不重要，也不需要散列的特殊顺序，我们可以决定最小的版本(NTLM，按散列排序)来最小化下载时间。

![](img/eb67efa6e77b32bf24c7239eb509354e.png)

Haveibeenpwned 上可下载文件的屏幕截图

我们下载一个 ZIP 文件，在成功下载后我们解压它。结果是一个简单但非常大的文本文件。请不要试图用普通的文本编辑器打开这个文件。在最好的情况下，什么也不会发生，在最坏的情况下，你的电脑会挂掉，因为它不能处理这个大小。如果你想打开文件仔细看看内容，你需要一个特殊的编辑器，比如 EmEditor。

该文本文件的每一行都包含一个密码的散列，以及该密码在违规中出现的频率。哈希和流行度用冒号分隔。看起来是这样的:

![](img/72467630463b9a4a9b246615a586d5b2.png)

解压缩后的行的格式。txt 文件

因此，哈希 00000001 F4 a 473 ed 6959 f 04464 f 91 bb 5 在数据库中出现了 4 次。

**第二步:创建数据库**

此时，我们也可以只使用文本文件来检查我们的密码是否在其中。我们将散列我们的密码，然后逐行检查文件。我们必须在冒号处拆分每一行，然后将哈希与我们的密码哈希进行比较。这是可行的，但需要很长时间(在我的笔记本电脑上大约 20 分钟)。

由于这有点不切实际，我们在下一步创建一个数据库来加快查询速度。为此，我们使用 SQLite，它已经包含在标准 Python 安装中，因此我们不需要任何额外的数据库软件或 Python 库。

然而，如果我们创建一个经典的 SQLite 数据库，查询仍然不是很快。这并不奇怪，毕竟数据库中有 6.13 亿个密码哈希。

为了提高查询的性能，我们需要为散列列创建一个索引。索引导致数据库被构造成 B 树。这种数据结构大大减少了在树中搜索的时间，但缺点是数据库变得非常大。您应该用原始文本文件所需的大约三倍的存储空间来计算。

创建数据库的代码如下所示:

(代码可以在我的 [GitHub](https://github.com/ChrisInmodis/Haveibeenpwned-Local-Version/tree/main/English) 上找到)

![](img/a63793b8ab9274b2b367c77238f51632.png)

用于构建 SQLite 数据库的 python 脚本

首先，我们用 sqlite3.connect 创建一个 SQLite 数据库，这里的标题是“pwned_indexed”。该数据库创建在与脚本相同的目录中。如果希望将数据库存储在不同的位置，也可以指定一个路径。

然后，我们创建一个“密码”表，包含两列 Hash 和 Prevalence。对于 hash 列，我们还创建了一个索引，这样以后查找 Hash 值的速度会特别快。

然后，我们将文本文件中的值读入数据库:读取每一行，在冒号处分割，第一个值(索引 0)保存为 hash，第二个值(索引 1)保存为 frequency。

此外，在输入一百万个散列值之后，我们在终端上输出一个中间计数。系统简单地检查计数变量是否能被一百万整除而没有余数。如果是这种情况，将显示进度。

最后，我们只需提交所有内容并关闭与数据库的连接。所有这些只是 30 行 Python 代码(如果没有进度输出也可以，也可以删除这需要的四行)。

在 Windows 资源管理器中，我们新的 SQLite 数据库如下所示:

![](img/891ef2e63bcf41e05036a33132bb9c3d.png)

来自 Windows 资源管理器的屏幕截图

如果查看属性，您会看到数据库的大小为 52.5GB。

![](img/48101a243257739c4ef75a1238748db7.png)

文件的属性

**第三步:查询数据库**

现在我们有了一个包含 6 . 13 亿个密码散列的数据库，我们可以编写另一个脚本来查询这个数据库。

![](img/a48dc56d13c513b652a43e8713efc10b.png)

用于查询数据库的 python 脚本

通过 input()函数，我们可以输入用户输入。然后，用户可以输入任何密码并检查是否有漏洞。输入的密码是用 NTLM 散列的，因为这种格式也用于我们数据库中的散列。

由于数据库中的散列都是以大写字母存储的，所以我们也将输入转换成大写字母，然后将 bytes 对象解码成一个字符串，以便可以与数据库中的字符串进行比较。

然后，我们连接到数据库，检查是否包含散列。如果是这种情况(即返回一个结果)，则输出“Pwned”和散列。如果您愿意，您也可以输出这一点上的流行程度，但由于这与我们无关(不管密码被破解了一次还是五万次，它都不应该被再次使用)，我们将在这一点上不使用它。

这个脚本也可以用 24 行代码实现。总共有 50 行代码(如果省去进度的输出)，您可以重新创建 Haveibeenpwned 的功能。

![](img/078c490660254a87f131a9caeed3f15f.png)

脚本的输出:密码

该屏幕截图显示了“password”的脚本输出。不出所料，这个密码已经被 pwn 了。

![](img/bacd1705c98e9a4b41a23a2180243c12.png)

随机密码脚本的输出

另一方面，完全随机的密码还没有包含在数据库中。

顺便说一句，查询几乎可以立即给出结果，因为 B 树结构意味着在找到正确的散列之前只需要检查很少的节点。

可以用它做什么？

您可以使用密码数据库的本地版本来检查所有现有密码的安全性，还可以检查新密码，以查看它们是否已经是违规的一部分，因此不应该使用。

或者，您可以将数据库集成到您自己的应用程序中。这一程序已经得到 Troy Hunt 的明确许可，不涉及任何费用。

![](img/178ff8800c0f6b6f929d79b74b74e163.png)

特洛伊·亨特允许我使用密码数据库

如果数据库集成到其他应用程序中，当用户注册时，可以检查他们的密码是否已经包含在数据漏洞中。如果是这种情况，可以将密码标记为不安全，并要求用户选择另一个密码。