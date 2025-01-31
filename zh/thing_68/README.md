# 将所有内容置于版本控制之下

将你所有项目中的一切都置于版本控制之下。你所需的资源都已具备：免费的工具，如Subversion、Git、Mercurial和CVS；充足的磁盘空间；廉价且强大的服务器；无处不在的网络；甚至还有项目托管服务。安装好版本控制软件后，你只需在包含代码的干净目录中执行适当的命令，就可以将你的工作放入其仓库中。你只需要学习两个新的基本操作：将代码更改*提交*到仓库，并使用仓库的版本更新你的工作版本。

一旦你的项目处于版本控制之下，你显然可以跟踪其历史，查看谁编写了什么代码，并通过唯一标识符引用文件或项目版本。更重要的是，你可以大胆地进行代码更改而无需担心——不再需要为了以防将来需要而注释掉代码，因为旧版本安全地保存在仓库中。你可以（也应该）用符号名称标记软件发布，以便将来轻松回顾客户运行的软件的确切版本。你可以创建并行开发的分支：大多数项目都有一个活跃的开发分支和一个或多个用于积极支持的发布版本的维护分支。

版本控制系统最大限度地减少了开发者之间的摩擦。当程序员在独立的软件部分上工作时，这些部分几乎会自动集成。当他们互相干扰时，系统会注意到并允许他们解决冲突。通过一些额外的设置，系统可以通知所有开发者每次提交的更改，建立对项目进展的共同理解。

当你设置项目时，不要吝啬：将*所有*项目资产置于版本控制之下。除了源代码，还包括文档、工具、构建脚本、测试用例、艺术作品，甚至库。将整个项目安全地放入（定期备份的）仓库中，可以最大限度地减少丢失磁盘或数据的损害。在新机器上设置开发环境只需从仓库中检出项目即可。这简化了在不同平台上分发、构建和测试代码的过程：在每台机器上，一个更新命令就能确保软件是最新版本。

一旦你体验到了使用版本控制系统的美妙之处，遵循几条规则将使你和你的团队更加高效：

- 在单独的操作中提交每个逻辑更改。将许多更改集中在一个提交中会使将来难以分离它们。这在你在项目范围内进行重构或样式更改时尤为重要，这些更改很容易掩盖其他修改。
- 每次提交时附带一条解释性消息。至少简要描述你所做的更改，但如果你还想记录更改的理由，这是存储它的最佳位置。
- 最后，避免提交会破坏项目构建的代码，否则你会不受项目其他开发者的欢迎。

在版本控制系统下的生活太美好，不要因为容易避免的失误而毁了它。

作者：[Diomidis Spinellis](http://programmer.97things.oreilly.com/wiki/index.php/Diomidis_Spinellis)