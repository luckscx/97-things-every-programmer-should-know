# 应用函数式编程原则

函数式编程最近在主流编程社区中重新引起了兴趣。部分原因是因为函数式范式的*涌现特性*非常适合应对我们行业向多核转变所带来的挑战。然而，尽管这无疑是一个重要的应用场景，但这并不是本文劝诫你*了解函数式编程*的原因。

掌握函数式编程范式可以极大地提高你在其他上下文中编写的代码质量。如果你深入理解并应用函数式范式，你的设计将展现出更高程度的*引用透明性*。

引用透明性是一个非常理想的特性：它意味着函数在给定相同输入的情况下始终产生相同的结果，无论它们在何时何地被调用。也就是说，函数的求值过程较少依赖于可变状态的副作用——理想情况下，完全不依赖。

命令式代码中缺陷的一个主要原因是可变变量。阅读本文的每个人都曾调查过为什么在某些情况下某个值不符合预期。可见性语义可以帮助缓解这些潜在的缺陷，或者至少大大缩小它们的位置范围，但真正的罪魁祸首实际上可能是设计中过度使用可变性。

在这方面，我们当然没有得到行业的太多帮助。面向对象编程的入门教程默许了这种设计，因为它们通常展示的示例是由相对长寿命的对象图组成的，这些对象愉快地互相调用可变方法，这可能是危险的。然而，通过精明的测试驱动设计，特别是确保“模拟角色，而不是对象”，可以设计出不必要的可变性。

最终的结果是一个通常具有更好责任分配的设计，其中包含更多的小函数，这些函数作用于传递给它们的参数，而不是引用可变的成员变量。缺陷会更少，而且通常更容易调试，因为在这些设计中更容易定位到引入错误值的位置，而不是推断出导致错误赋值的特定上下文。这大大提高了引用透明性，而学习一门函数式编程语言是让这些理念深入骨髓的最佳方式，因为在这种计算模型中，引用透明性是常态。

当然，这种方法并非在所有情况下都是最优的。例如，在面向对象系统中，这种风格通常在领域模型开发（即协作有助于分解业务规则的复杂性）中比在用户界面开发中产生更好的结果。

掌握函数式编程范式，以便你能够明智地将所学到的经验应用到其他领域。你的对象系统（至少）将因引用透明性的优点而受益，并且比许多人让你相信的更接近函数式编程的对应物。事实上，有些人甚至断言函数式编程和面向对象编程的巅峰*仅仅是彼此的反映*，一种计算中的阴阳形式。

作者：[Edward Garson](http://programmer.97things.oreilly.com/wiki/index.php/Edward_Garson)