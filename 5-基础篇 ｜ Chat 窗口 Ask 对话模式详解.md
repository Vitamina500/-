AI新手网，https://aixinshou.com/  全站9.9元终身免费下载！

在 Cursor 0.46 版本之前分为 Chat、Composer（Normal、Agent） 两个窗口三种对话模式。

0.46 版本后统一合并为 Chat 窗口，现在分为 Ask、Edit、Agent 三种对话模式。统一在一个窗口的好处是，如果 Ask 模式讨论的内容，可以方便的切换为 Agent 模式直接将内容写到文件中。

![image.png](https://p3-juejin.byteimg.com/tos-cn-i-k3u1fbpfcp/e7e036fc531340bbb0c13f4c2b7dccb3~tplv-k3u1fbpfcp-jj-mark:1600:0:0:0:q75.jpg#?w=1032&h=572&s=53491&e=png&b=181818)

Ask 模式是 Cursor 中最基础的 AI 交互方式，主要用于帮助你理解和探索代码。它就像一个随时待命的 AI 助手，可以：

* 回答你关于代码的各种问题
* 帮助搜索和理解代码库
* 提供代码解释和建议
* 快速修复代码错误（通过 AI Fix 功能）
* 和 Agent 模式最大区别是不能自动生成文件，如果是代码片段需要手动 Apply

## 使用技巧

* 使用 `⌘ + L` 快速打开/关闭 Chat 窗口，并自动切换到 Ask 模式
* 通过 `@` 符号添加特定上下文
* 悬停在代码错误上方，点击 AI Fix 按钮快速修复问题

## 使用示例

例如，在 Ask 模式下，我们让 Cursor 帮我们写一个冒泡排序的代码，如果当前项目没有指定语言，Cursor 可能会随机选择一种语言，如下默认使用 TypeScript 写的。

![image.png](https://p9-juejin.byteimg.com/tos-cn-i-k3u1fbpfcp/1d21495f1d434537be7f31f9bedb1b15~tplv-k3u1fbpfcp-jj-mark:1600:0:0:0:q75.jpg#?w=784&h=966&s=129825&e=png&b=181818)

我们让 Cursor 用 JavaScript 语言实现。

接下来，我们新建一个 sort.js 文件，并添加到上下文，Apply 地方就会提示我们可以将代码应用到 sort.js 文件中。

![image.png](https://p9-juejin.byteimg.com/tos-cn-i-k3u1fbpfcp/001536bc03da4e948dd58459929fb74b~tplv-k3u1fbpfcp-jj-mark:1600:0:0:0:q75.jpg#?w=1582&h=795&s=103331&e=png&b=181818)

当我们点击 Apply 按钮后，Cursor 会自动将代码应用到 sort.js 文件中。界面上会出现三个保存相关的选项：

1. 文件代码片段右下角的 "Accept ⌘Y" 和 "Reject ⌘N" 按钮是针对当前代码块的，一个文件中可能有多个代码块。
2. 代码编辑区域底部的 "Accept file ⌘Y" 和 "Reject file ⌘N" 按钮，是整个文件的保存。
   * Accept file 是保存到文件中。
   * Reject file 是拒绝此次修改。
3. 聊天窗口中代码块右上角的确认（✓）和取消（×）按钮

![image.png](https://p9-juejin.byteimg.com/tos-cn-i-k3u1fbpfcp/5f69f34c0c144cb198dd3ada1547559f~tplv-k3u1fbpfcp-jj-mark:1600:0:0:0:q75.jpg#?w=1585&h=1037&s=229747&e=png&b=181818)

如果你觉得生成的代码不满意，可以点击 Reject 拒绝此次修改。

## 发送和 使用 codebase 发送 区别

在 Chat 窗口下，发送消息此前是两个提交按钮，0.46 版本后只展示了一个按钮，如果不看文档，你都不知道它这里竟然还有隐藏功能：

1. `↵`：
   * 直接按回车或点击发送按钮
   * 普通提交，只发送当前的对话内容
   * 适合简单的问题咨询和代码讨论
   * 不会包含项目上下文信息

前面我们刚实现了冒泡排序的代码，现在我问 Cursor 当前项目下都有啥排序算法，这明显是在一本正经的胡说...，所以它回答的内容，有时候需要甄别，大家不要被它忽悠了。

![image.png](https://p1-juejin.byteimg.com/tos-cn-i-k3u1fbpfcp/6659c3c8034648da9f58ad43b29c4244~tplv-k3u1fbpfcp-jj-mark:1600:0:0:0:q75.jpg#?w=1573&h=817&s=200656&e=png&b=181818)

2. `⌘↵`：
   * 按住 `⌘`（command） + `↵`（回车） 键发送
   * 带有代码库上下文的发送
   * 会自动分析并包含相关的代码文件内容
   * 适合需要 AI 理解当前项目结构和代码的场景
   * 能得到更准确的回答，因为 AI 有更多上下文信息

当我这次使用 Command + 回车键发送消息时，Cursor 会自动分析相关的代码文件内容，并给出更准确的回答。

![image.png](https://p6-juejin.byteimg.com/tos-cn-i-k3u1fbpfcp/0070cf53fef5415c86663240b95fabe0~tplv-k3u1fbpfcp-jj-mark:1600:0:0:0:q75.jpg#?w=1579&h=897&s=191145&e=png&b=171717)

## 问题快速修复

Cursor 提供了便捷的代码错误修复功能。

例如，在下面的示例中，我们在 JavaScript 代码中故意引入了一个语法错误：把变量声明语句中的赋值符号 `=` 删除了。此时代码会报错，提示 "应为","。"。

鼠标悬停在错误处，把错误信息发送给 Cursor Chat 窗口，AI 会分析错误原因并给出修复建议。在这个例子中，它发现了语法错误：`const len arr.length` 缺少了赋值运算符，需要改为 `const len = arr.length`。

原先底部的 Ask 模式会被切换为 Agent 模式。

注意，按下 `⌘` 键再点击错误信息，会发送错误信息到新 Chat 窗口。

![image.png](https://p3-juejin.byteimg.com/tos-cn-i-k3u1fbpfcp/5a931a70eaab41f892287bf17c6b7999~tplv-k3u1fbpfcp-jj-mark:1600:0:0:0:q75.jpg#?w=1266&h=959&s=135021&e=png&b=191919)

## 总结

Ask 模式是 Cursor 中最基础的交互方式，主要用于代码探索和理解。通过 “普通提交” 和 “使用 Codebase 提交” 两种提交方式，以及便捷的错误修复功能，它能够帮助我们快速解决日常编程中遇到的各种问题。就像一个 AI 助手，你可以随时向它提问。