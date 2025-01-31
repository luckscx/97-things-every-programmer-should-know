# 警惕共享

这是我在公司的第一个项目。我刚完成学位，急于证明自己，每天加班加点地阅读现有代码。在处理我的第一个功能时，我格外小心地应用了我所学的所有知识——添加注释、记录日志、尽可能将共享代码提取到库中，等等。我本以为已经准备充分的代码审查却让我大吃一惊——重用代码竟然不受欢迎！

怎么会这样？在整个大学期间，重用代码一直被奉为高质量软件工程的典范。我读过的所有文章、教科书，以及那些经验丰富的软件专业人士教给我的东西，难道都错了吗？

事实证明，我忽略了一个关键因素。

**上下文**。

系统中两个截然不同的部分以相同的方式执行某些逻辑，这一事实的意义远没有我想象的那么重要。在我提取出这些共享代码库之前，这些部分彼此之间并没有依赖关系。每个部分都可以独立发展。每个部分都可以根据系统业务环境的变化调整其逻辑。那几行相似的代码是偶然的——一种暂时的异常，一种巧合。直到我出现之前，情况一直如此。

我创建的共享代码库将两只脚的鞋带绑在了一起。一个业务领域的步骤必须与另一个业务领域同步才能进行。这些独立功能的维护成本曾经可以忽略不计，但共享库需要的测试工作量却增加了一个数量级。

虽然我减少了系统中代码的绝对行数，但却增加了依赖关系的数量。这些依赖关系的上下文至关重要——如果它们是局部的，可能还情有可原，甚至有一定的积极价值。但当这些依赖关系不受控制时，它们的触角会纠缠到系统的更大问题中，尽管代码本身看起来还不错。

这些错误的阴险之处在于，它们的核心听起来像是个好主意。在正确的上下文中应用这些技术是有价值的。但在错误的上下文中，它们会增加成本而不是价值。如今，当我进入一个现有的代码库，并且对各个部分的使用上下文一无所知时，我会更加谨慎地对待共享的内容。

**警惕共享。检查你的上下文。只有这样，才能继续前进。**

作者：[Udi Dahan](http://programmer.97things.oreilly.com/wiki/index.php/Udi_Dahan)