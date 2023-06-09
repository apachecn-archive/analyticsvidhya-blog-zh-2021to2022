# 微软 Bot Framework Composer v2 的突然飞跃

> 原文：<https://medium.com/analytics-vidhya/a-sudden-leap-into-microsoft-bot-framework-composer-v2-8b6774bd8f9d?source=collection_archive---------13----------------------->

## 我其实很期待你的回答

在工作中，我们一直在开发一些真正令人兴奋的面向商业的自然语言软件。然而，我是一个技术功能通才，这意味着我花了大部分时间将存在于不同抽象层次的想法拼接在一起，而不是卷起袖子编写工作代码。

换句话说，我对项目的贡献是有价值的，但它们通常不会在代码级别上体现出来。在大多数情况下，我对此没什么意见，但有时我想尝试一个想法，而我的中级编程技能不能让我走得足够远、足够快。这意味着我必须吸引其他团队成员来实现我的想法。

我的团队中有一群聪明、有才华的专家，他们具备快速原型开发所需的编程能力，这很好。*但是，如果我能独自完成一个概念证明，那不是更令人满意吗，*我对自己说，*？*这样，我可以把它作为功能软件交给团队，而不是几页手绘的 UI 草图和一大堆冗长的用户故事。

显然，宇宙在倾听。前几天，我听说微软最近发布了第二版 [Bot Framework Composer](https://docs.microsoft.com/en-us/composer/introduction?tabs=v2x) ，这是他们用于构建聊天机器人的集成开发环境。显然，Composer 将允许我创建功能齐全的聊天机器人，而无需输入大量代码。我甚至不需要深入的自然语言处理或机器学习知识！

乍一看，我似乎只需要设计对话流，从下拉菜单中选择设置，并添加一些聊天机器人响应。我想这意味着我还不需要学习机器人框架 SDK 耶！不像自己一个人敲代码那么难，但是我决定我可以忍受。我下载了桌面应用程序，安装了它，然后就上床睡觉了，充满了聊天机器人带来的兴奋。

# 坎坷的开端

你知道当你有了这个好主意，但手边没有笔时是什么感觉吗？或者当你想玩视频游戏，但你的电脑决定安装一个小时的操作系统更新？当我启动 Composer 并试图创建一个新的 bot 时，我就是这样的感觉，只是被告知我需要安装 Node.js。

这不应该是我前一天晚上经历的安装过程的一部分吗？不管怎样，我还是继续做了，作为我这样的人，我也决定安装所有的可选项目。我很快就后悔了。一个 PowerShell 脚本出现了，根据它，我的笔记本电脑已经开始下载 Python 3.9(我已经有了)和 Visual Studio 构建工具(我没有)。

过了一会儿，脚本就停在那里，很长一段时间没有任何进展的迹象，所以我启动了任务管理器，等到 Visual Studio 安装程序(实际上没有显示为可见窗口)停止下载它正在下载的任何东西，然后终止脚本。我仍然不确定它是否应该自己结束；我应该为此担心吗？

好吧，作曲家，让我们再试一次。我再次尝试创建一个新的机器人。因为 Python 是我选择的机器人框架 SDK v4 的语言，所以我决定用那个选项…但是显然 **Composer v2 不支持 Python。**嗯。

![](img/d1fa5bd2aa764819bb8bf4d9df0d20ba.png)

你可以使用任何语言，只要是 C#或者 Node。

这并不理想，但我可以接受 C#。语法与 Java 并没有太大的不同，所以我仍然可以在需要的时候读取代码。由于 Composer 应该是高度可视化的，我可能不需要经常这样做。我选择了一个基本的 C#模板，然后……被告知安装。NET SDK。好吧…好吧。我会做的。

我做到了。我在下一次尝试时收到的构建错误让我想到我应该重启我的计算机。一旦我做到了*，我终于能够开始我的旅程，进入 Bot Framework Composer 的奇妙世界。*

我想我要说的是，安装过程可以稍微顺利一点。

# 下一步是什么？

我实际上花了大约一个小时浏览 Composer 中的各种菜单，然后开始在 Bot Framework Composer 的官方 YouTube 频道上关注 Ben Brown 的旧 Composer v1 教程。我可能会在明天的某个时候完成它。

到目前为止，Composer v1 教程的内容与我在 v2 中看到的内容非常相似，足以让我跟随，但在几个地方又有足够的不同，可能会引起一些混乱。一旦我完成了，我会有更多的话要说，但我已经可以说，使用教程视频可能会让你比从官方文档开始更快地上手和运行。

就这个博客而言，我会继续发表我在人工智能和自然语言处理方面的冒险经历，而且肯定会有一些其他有趣的想法混杂在这里和那里。由于我在 [Algo](https://www.algo.com/) 做的很多工作都是保密的，我将创建一些爱好项目来探索 Composer 和其他工具。心里已经有一个了，迫不及待的想和大家分享！