# 封装行为，而不仅仅是状态

在系统理论中，**封装**是处理大型复杂系统结构时最有用的构造之一。在软件行业中，封装的价值已被广泛理解。编程语言通过子程序、函数、模块、包、类等构造来支持封装。

模块和包解决了更大规模的封装需求，而类、子程序和函数则解决了更细粒度的封装问题。多年来，我发现类是开发者最难正确使用的封装构造之一。我们经常看到一个类中只有一个3000行的主方法，或者一个类中只有针对其基本属性的*set*和*get*方法。这些例子表明，相关开发者并未完全理解面向对象的思想，未能充分利用对象作为建模构造的能力。对于熟悉POJO（Plain Old Java Object）和POCO（Plain Old C# Object 或 Plain Old CLR Object）术语的开发者来说，回归面向对象作为建模范式的基础的初衷是——对象是简单而朴素的，但并不愚蠢。

一个对象封装了状态和行为，其中行为由实际状态定义。以一个门对象为例，它有四种状态：关闭、打开、正在关闭、正在打开。它提供了两个操作：打开和关闭。根据状态的不同，打开和关闭操作的行为也会有所不同。对象的这种固有特性使得设计过程在概念上变得简单。它归结为两个简单的任务：分配和委派责任给不同的对象，包括对象之间的交互协议。

通过一个例子可以最好地说明这一点。假设我们有三个类：`Customer`、`Order`和`Item`。`Customer`对象是信用额度和信用验证规则的自然载体。`Order`对象知道其关联的`Customer`，并且它的`addItem`操作通过调用`customer.validateCredit(item.price())`来委托实际的信用检查。如果该方法的后置条件失败，可以抛出异常并中止购买。

经验不足的面向对象开发者可能会决定将所有业务规则封装到一个通常称为`OrderManager`或`OrderService`的对象中。在这些设计中，`Order`、`Customer`和`Item`被视为几乎只是记录类型。所有逻辑都被从类中提取出来，并集中在一个大型的过程化方法中，其中包含大量的内部*if-then-else*结构。这些方法很容易被破坏，几乎无法维护。原因是什么？封装被破坏了。

因此，最终不要破坏封装，并利用编程语言的能力来维护它。

作者：[Einar Landre](http://programmer.97things.oreilly.com/wiki/index.php/Einar_Landre)