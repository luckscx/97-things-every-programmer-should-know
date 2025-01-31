# 通过删除代码来改进代码

*少*即是多。这是一句相当陈旧的格言，但有时它确实是对的。

在过去的几周里，我对我们的代码库做了一些改进，其中一项就是删除了其中的一部分代码。

我们遵循XP（极限编程）的原则编写了软件，包括YAGNI（即，你不需要它）。然而，人性使然，我们不可避免地会在某些地方做得不够好。

我注意到产品在执行某些任务时花费了太长时间——这些任务本应该是几乎瞬间完成的简单任务。这是因为它们被过度实现了；添加了许多不必要的额外功能，这些功能在当时看起来似乎是个好主意。

因此，我通过从代码库中删除这些多余的功能，简化了代码，提高了产品性能，并降低了全局代码的熵值。幸运的是，我的单元测试告诉我，在操作过程中我没有破坏其他任何东西。

这是一次简单而令人满意的体验。

那么，为什么这些不必要的代码会出现在代码库中呢？为什么一个程序员会觉得有必要编写额外的代码，而它又是如何通过审查或结对编程过程的呢？几乎可以肯定的是，原因如下：

- 这是一些有趣的额外内容，程序员想写它。*（提示：编写代码是因为它增加了价值，而不是因为它让你感到有趣。）*
- 有人认为将来可能会需要它，所以觉得最好现在就编写它。*（提示：这不是YAGNI。如果你现在不需要它，就不要现在编写它。）*
- 它看起来并不是一个很大的“额外”功能，所以实现它比回去询问客户是否真的需要它更容易。*（提示：编写和维护额外的代码总是需要更长的时间。而且客户实际上是非常容易接近的。一小段额外的代码会随着时间的推移滚雪球般地变成一大块需要维护的工作。）*
- 程序员发明了一些既没有文档记录也没有讨论过的额外需求，这些需求为额外功能提供了理由。实际上，这些需求是虚假的。*（提示：程序员不设定系统需求；客户才是决定需求的人。）*

你现在在做什么工作？这些工作都是必要的吗？

作者：[Pete Goodliffe](http://programmer.97things.oreilly.com/wiki/index.php/Pete_Goodliffe)