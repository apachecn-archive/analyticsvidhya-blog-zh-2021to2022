# Linux 中的动态库

> 原文：<https://medium.com/analytics-vidhya/dynamic-libraries-in-linux-c978b478efea?source=collection_archive---------0----------------------->

![](img/8271244bfe6c1d8b1bc19f3f498ad207.png)

本文将扩展上一篇文章中讨论的概念: [C 静态库](/analytics-vidhya/c-static-libraries-da439d9afc09)。我们将谈论库，但在这个场合是关于另一种现有的类型:动态库。扩展概念、它们的用法、优缺点以及如何创建它们。值得一提的是，所有的例子和术语都将基于 Linux 操作系统。在其他操作系统中，文件的命名、示例和扩展名可能会有所不同，但任何操作系统的概念应该是相同的。

在编程中，我们总是在所有的程序中使用库，但是创建它们并不常见。虽然一旦我们有了概念，就很容易建立自己的概念。回想一下上一篇文章中给出的例子，库是软件的集合，这些软件被组合在一起以创建一个“概念的大书”。可以被其他程序调用和重用的概念。最常见的例子是 C 标准库，它拥有 malloc、realloc、free、printf 等函数。在 C 程序中我们一直在使用的函数，我们不知道它们来自哪里。实际上，它们保存在先前创建的库中，我们的程序在需要时会使用它们。

# 静态库之间的区别、优点和缺点

如前所述，存在两种类型的库。其中一个主要的区别在于我们的程序如何访问图书馆的信息。如果我们谈论的是静态库，这是由编译器在链接步骤中完成的，如果我们谈论的是动态库，这是在运行时完成的。这两个概念也被称为动态或静态链接，指的是在程序和库之间连接信息的行为。

静态链接和动态链接的另一个区别在于实现和修复错误。当我们必须修复一个静态库的错误时，除了修复它并重新编译所有使用它的文件之外，没有别的办法。因为要记住，库的信息是在代码编译的时候就嵌入代码中的。因此，如果我们改变了库，我们就改变了已编写的部分代码。当我们动态链接我们的库时，这不是一个问题。如果我们改变库的某些东西，就像编辑一个单独的程序。如果我们正在测试这个库，或者甚至当我们想要与其他同事共享它时，这是一个巨大的优势。

![](img/2b93cbf15cab3df86b881e95952823ea.png)

静态链接和动态链接的另一个区别在于实现和修复错误。当我们必须修复一个静态库的错误时，除了修复它并重新编译所有使用它的文件之外，没有别的办法。因为要记住，库的信息是在代码编译的时候就嵌入代码中的。因此，如果我们改变了库，我们就改变了已编写的部分代码。当我们动态链接我们的库时，这不是一个问题。如果我们改变库的某些东西，就像编辑一个单独的程序。如果我们正在测试这个库，或者甚至当我们想要与其他同事共享它时，这是一个巨大的优势。

你也可以想象，把我们程序中用到的所有函数都放在另一个地方会让我们的程序变得更小。虽然在小程序中大小不是问题，但在大软件中，大小肯定是问题。正如我们之前所说的，静态库嵌入在我们的代码中，是代码的一部分，所以它的大小取决于我们的程序和使用的库。

# 它们是如何工作的？

为了成功地在 C 中创建一个动态库，我们首先需要确定哪些函数将包含在我们的集合中。然后将它们编译成目标代码，这样这些文件就可以在我们未来的程序中使用。在编译过程中，这是将其转换为可执行文件之前的前一步。如果我们使用的是 GCC 编译器，那么运行这个命令，在要添加的文件后面加上-c 和-fPIC 标志。第一个标志用于在汇编步骤后停止编译过程，作为机器目标代码给出。第二个代表位置无关码。我们需要使我们的目标代码可以在任何位置被可执行文件访问。

```
gcc file1.c file2.c -c -fPIC
```

在我们的文件作为独立于位置的目标代码之后，我们需要创建一个库文件。在这种情况下，扩展名将为"。所以“意思是共享对象。要创建它，我们必须再次运行 GCC 命令，选择先前创建的目标文件，后面跟一个共享标志，表明我们要创建一个共享对象(一个动态库)。因为我们已经在用-o 编译后命名了我们的可执行文件，我们可以在这里做同样的事情。

```
gcc file1.o file2.o -shared -o lib_test.so
```

一直到这里，应该已经成功地创建了一个动态库。所以)在你的目录里。所以现在:

# 我们如何使用它？

首先，我们需要创建一个测试文件，它使用我们在库中描述的函数。将文件转换成目标代码(在这种情况下，将其转换成 PIC 并不重要，因为不会从另一个目录请求它)。

```
gcc test.c -c
```

当我们已经编译了它，我们需要指定我们正在链接它到一个动态库。这可以通过运行命令来完成，该命令带有我们要链接的文件，后跟标志-L，告诉编译器在当前目录中查找库。之后，我们需要指定库的名称，在本例中，是“l_test”。注意，传递的库名现在在单词 lib 上被缩短了。在这一步，我们可以使用这个快捷方式，因为编译器假设所有以 l 开头的单词都是库。像往常一样，我们给我们的可执行程序命名。

```
gcc test.o -L. l_test -o testlib
```

如果我们试图运行我们的可执行文件来调用我们已经描述过的函数。它会给我们一个错误，因为默认情况下，系统将在系统的本地库目录中搜索库，而我们的库在当前目录中。我们可以用两种方法来避免这个错误。第一个是将我们的库复制到默认的搜索目录/lib、/usr/lib、usr/local/lib。通过在运行时这样做，我们的库将在系统搜索的地方。

第二种方法是，在执行文件之前，给程序一个我们想要使用的库的具体路径。为了获得特定的路径，我们可以运行命令“pwd”。复制粘贴到下面的变量 LD_LIBRARY_PATH 之后。通过这样做，我们为文件提供了库的地址，以便在运行时链接它。

```
LD_LIBRARY_PATH=”:/home/ubuntu/programs/libtest;$LD_LIBRARY_PATH” ./testlib
```

![](img/9d791fb332f00d768adf933d0ff1a4d8.png)

我们知道优缺点以及如何创建动态库。希望有了这些知识，我们的发展选择会更加明智。当然，这些概念将有助于在更大的软件需求中实现特定的功能。设计我们自己的函数库是程序员职业生涯中的一个巨大进步，它将强化每个程序员解决问题的独特方式。

以前的文章可能会有帮助---！>[用 C 编译的过程](/analytics-vidhya/the-process-of-compilation-with-c-6b9e97b9596a)

— -!> [C 静态库](/analytics-vidhya/c-static-libraries-da439d9afc09)