# 代码布局的重要性

许多年前，我曾在一个Cobol系统上工作，那里的员工不允许更改缩进，除非他们已经有理由修改代码，因为曾经有人因为让一行代码滑入行首的特殊列而破坏了某些东西。即使布局有时会误导人，我们也必须非常仔细地阅读代码，因为我们不能信任它。这个政策一定在程序员效率上付出了巨大的代价。

有研究表明，我们在编程时花费更多的时间在导航和阅读代码上——找到*在哪里*进行修改——而不是实际打字，所以这是我们想要优化的地方。

- *易于扫描。* 人们非常擅长视觉模式匹配（这是我们必须在草原上发现狮子时的遗留技能），所以我可以帮助自己，通过标准化所有与领域无关的内容，所有大多数商业语言带来的“偶然复杂性”，使其淡入背景。如果行为相同的代码看起来相同，那么我的感知系统将帮助我挑出差异。这就是为什么我也遵守关于如何在编译单元内布局类的各个部分的约定：常量、字段、公共方法、私有方法。

- *表达性布局。* 我们都学会了花时间找到正确的名称，以便我们的代码尽可能清楚地表达它的功能，而不仅仅是列出步骤——对吧？代码的布局也是这种表达性的一部分。第一步是让团队就基本的自动格式化器达成一致，然后我可能会在编码时手动进行调整。除非有积极的异议，团队会迅速收敛到一个共同的“手工完成”风格。格式化器无法理解我的意图（我应该知道，我曾经写过一个），对我来说更重要的是，换行和分组反映代码的意图，而不仅仅是语言的语法。（Kevin McGuire让我从自动代码格式化器的束缚中解脱出来。）

- *紧凑的格式。* 我能在屏幕上看到的内容越多，我就能在不通过滚动或切换文件来打破上下文的情况下看到更多内容，这意味着我可以在脑海中保持更少的状态。对于8字符名称和行式打印机来说，冗长的过程注释和大量的空白是有意义的，但现在我生活在一个具有语法着色和交叉链接的IDE中。像素是我的限制因素，所以我希望每一个像素都能帮助我理解代码。我希望布局能帮助我理解代码，但仅此而已。

一位非程序员朋友曾经评论说，代码看起来像诗歌。我从真正优秀的代码中得到了这种感觉，文本中的每一部分都有其目的，并且它在那里帮助我理解这个想法。不幸的是，编写代码并没有像写诗那样浪漫的形象。

作者：[Steve Freeman](http://programmer.97things.oreilly.com/wiki/index.php/Steve_Freeman)