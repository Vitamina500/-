AI新手网，https://aixinshou.com/  全站9.9元终身免费下载！

我们前面章节是基于 Cursor 0.48 之前的版本进行介绍的，这篇文章主要是给大家讲解下 Cursor 0.48 主要的一些变更内容，整体影响不大。

聊天标签页：并行对话
----------

聊天标签页功能，让你可以同时进行多个对话。

*   使用快捷键 `⌘N` 创建新标签页
*   在不同标签间快速切换，同时处理多项任务
*   当某个标签页等待你的输入时，会显示橙色小点提醒

以下是 0.48 刚出来时我在公众号做的介绍

![image.png](https://p9-juejin.byteimg.com/tos-cn-i-k3u1fbpfcp/6e1f9fb24c8f49dfa8a3b391b121f1e0~tplv-k3u1fbpfcp-jj-mark:1600:0:0:0:q75.jpg#?w=707&h=248&s=27805&e=png&b=191919)

发现又不显示多个标签页了（0.48.9），不确定是不是 Cursor 的一个 bug，这个影响不大。

![image.png](https://p1-juejin.byteimg.com/tos-cn-i-k3u1fbpfcp/1c0e3609558f486e8590099e96957a00~tplv-k3u1fbpfcp-jj-mark:1600:0:0:0:q75.jpg#?w=906&h=237&s=32230&e=png&b=191919)

Normal 模式名字改了又改
---------------

Cursor 最开始有个 Normal 模式，在前面几个版本名字改为了 Edit，现在又改为了 Manual。现在用的比较多的是 Agent 模式，这个近段时间我都没怎么用过！

![image.png](https://p9-juejin.byteimg.com/tos-cn-i-k3u1fbpfcp/7f7380964d7f418e89e4c0978bb7a99f~tplv-k3u1fbpfcp-jj-mark:1600:0:0:0:q75.jpg#?w=637&h=332&s=30360&e=png&b=191919)

自定义模式
-----

这个是 0.48 一个比较大的更改，新版本彻底重新设计了模式系统，提供了更大的灵活性：

*   内置的 Agent 模式和 Ask 模式（这两个已经足够用了）
*   全新的自定义模式功能（测试版）
*   可自定义工具、设置、指令和模型
*   支持为每个模式设置专属快捷键

例如， Agent 模式你不开启 Yolo 功能，它就是一个不能自动执行命令的 Agent。但你现在可以用这个自定义模型功能，打造一个专属的 Yolo 模式。

自定义模式默认不会开启，需要在 Cursor 设置中手动开启。

![image.png](https://p6-juejin.byteimg.com/tos-cn-i-k3u1fbpfcp/8081c151553240cea921867554e33168~tplv-k3u1fbpfcp-jj-mark:1600:0:0:0:q75.jpg#?w=835&h=310&s=33743&e=png&b=1a1a1a)

Chat 窗口模型选择框 `Add custom mode`，输入名字，例如我们就叫 Yolo，开启你需要的一个功能，这样一个你自己的专属模式就好了

![image.png](https://p9-juejin.byteimg.com/tos-cn-i-k3u1fbpfcp/bbb5032d186f4ed2b2183d6dfe9bac1a~tplv-k3u1fbpfcp-jj-mark:1600:0:0:0:q75.jpg#?w=532&h=298&s=25639&e=png&b=191919)

![image.png](https://p3-juejin.byteimg.com/tos-cn-i-k3u1fbpfcp/ec71130bf8d648cca6471d4ad25c601e~tplv-k3u1fbpfcp-jj-mark:1600:0:0:0:q75.jpg#?w=513&h=682&s=54837&e=png&b=191919)

![image.png](https://p6-juejin.byteimg.com/tos-cn-i-k3u1fbpfcp/639f70dcd82d4dee9a21d12fa3f5c54e~tplv-k3u1fbpfcp-jj-mark:1600:0:0:0:q75.jpg#?w=902&h=474&s=47486&e=png&b=171717)

Agent 模式现在绑定到 `⌘I` 快捷键，而 `⌘L` 用于切换侧边栏。

声音通知：不再盯着屏幕等待
-------------

一个小而实用的功能，让工作流程更加顺畅：

*   当聊天完成时播放提示音
*   你可以在处理其他任务时知道何时回来查看结果

![image.png](https://p9-juejin.byteimg.com/tos-cn-i-k3u1fbpfcp/c396bc734bd14df9a8718bc3a976e312~tplv-k3u1fbpfcp-jj-mark:1600:0:0:0:q75.jpg#?w=848&h=259&s=29203&e=png&b=191919)

这个功能对于需要等待较长时间的操作特别有用，让你能更高效地利用时间。

上下文窗口警告：避免超出限制
--------------

长对话现在更加智能：

*   当接近上下文窗口大小限制时，系统会建议创建新聊天
*   可以选择继续当前对话，旧消息会被自动总结
*   帮助保持对话流畅性并避免信息丢失

![image.png](https://p1-juejin.byteimg.com/tos-cn-i-k3u1fbpfcp/9fabbab743f44d46b8d9cf2eba36d070~tplv-k3u1fbpfcp-jj-mark:1600:0:0:0:q75.jpg#?w=1080&h=608&s=119667&e=png&b=1d2228)

移除 @Codebase 命令
---------------

0.48 版本之前 Ask 模式需要手动 `@Codebase` 才会索引代码库，在 0.48 版本中 Ask 会自动索引代码库，Agent 模式下此前也会自动索引代码库。

Cursor 本次是删除了这个 @Codebase 命令。如果出现没有自动搜索代码库，而你恰好需要这个功能时，使用自然语言 “搜索代码库” 即可。

参考

*   [www.cursor.com/cn/changelo…](https://www.cursor.com/cn/changelog "https://www.cursor.com/cn/changelog")
*   [mp.weixin.qq.com/s/Aweupfi\_s…](https://mp.weixin.qq.com/s/Aweupfi_ss1gS2lapD52Vg "https://mp.weixin.qq.com/s/Aweupfi_ss1gS2lapD52Vg")