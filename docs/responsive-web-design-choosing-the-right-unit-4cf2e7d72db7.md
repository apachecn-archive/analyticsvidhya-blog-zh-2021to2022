# 响应式网页设计-选择正确的单位！

> 原文：<https://medium.com/analytics-vidhya/responsive-web-design-choosing-the-right-unit-4cf2e7d72db7?source=collection_archive---------13----------------------->

你有没有想过你每天访问的所有网站是如何设计和开发的？我一直对开发网站感兴趣。虽然我在学生时代学过 HTML，但我在 web 开发方面的知识和经验远远不足以让我自己开发一个网站。但是这次禁闭给了我时间来提高我的技能。所以，我参加了几个在线课程，从零开始，开发了一个自己的网站。

我学习网页开发已经快 4 个月了。在我课程的第四周，当我完成了 HTML 并学习了 CSS 的基础知识时，我的老师花了整整一节课来为我们在样式表中设置的所有参数选择正确的单位。最初，我认为在它上面浪费 30 分钟太多了，但是到最后，我意识到这些单元可以发挥多么重要的作用。也是在这类课程中，我意识到开发一个网站时的小细节让它从成千上万的其他网站中脱颖而出。所以在这篇文章中，我将试着分享我在那次会议中学到的要点。

![](img/7ae1991cea7f67aa5ddfc0100fb6eb57.png)

费伦茨·阿尔马西在 [Unsplash](https://unsplash.com?utm_source=medium&utm_medium=referral) 上的照片

一些最常用的指标是像素、ems、rem 和百分比。它们用于设置宽度、边距、填充、字体等的值。我将在这篇文章中解释每一个，并尝试理清思路，建立一个响应性网站。

## 1)像素:

你看到的是一个由许多小点组成的显示器，这些小点构成了一幅图像。这些被称为像素。这些微小的点将屏幕分割开来，并连接在一起形成一幅图像。由于像素固有的精确性和准确性，像素一直是网页设计者最喜欢的单位之一。 ***一旦为字体或元素选择了像素值，字体大小将在所有设备和浏览器中保持不变。*** 虽然这种方法提供了非常精确的控制，但最近它不支持我们构建能够适应所有屏幕类型的响应式设计的需求。因此，将刚性像素值指定为字体大小的选项似乎不是最佳选择。

## 2) EMS:

Ems 是长度的相对度量。em 是任何字样中大写 M 的大小，是相对于字体的大小。使用 em 作为字体大小调整的基础的优点是 ***通过改变父字体大小，你可以同时改变所有的字体大小。*** 1em 等于当前字体大小。例如，如果我们构建一个< div >并包含字体大小为 16 像素的文本，1 em 将对应于 16 像素，2 em 对应于 32 像素，依此类推。em 在所有浏览器中都是可调整大小的，没有必要为每个元素设置值，因为在这种情况下，规则可以应用于“父”元素，并通过级联过程自动应用于其各自的“子”元素。这很有用，因为它允许您改变元素的绝对大小，如字体大小，而不改变它们相对于彼此的大小。

## 3) REMS:

Rems 代表 Root-Ems。它的行为类似于前面提到的 em 单元，但有一个重要的区别: ***它的值是相对于文档的根元素(在 HTML 中，就是< html >元素)的，而不是相对于与之相关联的任何其他元素的。字体大小总是相对于这个根 html 的大小，而不是在嵌套多个不同大小的容器时进行调整。因此，要使您的网页具有响应性，您所要做的就是添加支持各种设备的带有特定断点的媒体查询，并在这些查询中指定您的< html >元素的大小。网站中的所有其他元素都会根据它来调整大小。Rem 对于克服 em 中面临的嵌套元素问题也很方便。正因为如此，rems 现在是使用最广泛的单元之一，因为它提供了所需的响应能力，并且几乎在所有浏览器中都得到支持。***

## 4)百分比:

百分比也是相对大小的度量。百分比采用数字后跟%的形式。这是一个相对的度量，如果你设置任何元素的宽度，比如说 50%，它将占据可用屏幕大小的 50%，可能是显示器或手机屏幕。百分比可以用于宽度、高度、填充、边距等属性，以及开头提到的字体大小。就像 ems 一样，percentage 也是字体大小的可调整单位，它们的 CSS 声明可以被继承。理论上，百分比和 ems 之间没有太大的区别，它们都是可延展的度量单位。

通过选择正确的指标，您可以轻松地使您的网页响应迅速，并创建一个支持所有平台和浏览器的网站。有一篇非常好的 [***文章***](https://css-tricks.com/rems-ems/) 是由 *Chris Coyier* 写的，它解释了一种方法，你可以将所有这些单元合并到你的网页中，并充分利用它们。您可以查看更多与此主题相关的 [***文章***](https://www.w3.org/TR/css3-values/#em)*文章 [***这里***](https://css-tricks.com/the-lengths-of-css/) 。*

*这篇文章总结了我学到的东西，以及我记下的关于选择合适单位的笔记。虽然一个非常简单的主题，如果理解透彻，可以使开发网页的过程变得容易得多。希望我可以清楚地解释这些单元的用途，你可以在你的下一个项目中以更好的方式使用它们。祝你今天开心！玩的开心！*

*参考-[https://design shack . net/articles/typography/what-the-deal-with-em-and-rem/](https://designshack.net/articles/typography/whats-the-deal-with-em-and-rem/#:~:text=An%20em%20is%20the%20size,look%20better%20in%20big%20type)*