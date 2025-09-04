AI新手网，https://aixinshou.com/  全站9.9元终身免费下载！

Agent 模式是 Cursor 默认的对话模式，也是一个更强大的 AI 编程助手，专注于代码的创作和修改。它不仅能理解代码，还能直接进行文件操作。

## 困惑的 Edit 模式

Cursor 在 0.45 版本及之前，有个 Normal 模式，相当于现在的 Edit 模式，自从 0.46 版本对 Chat 做整合后，Normal 模式没有消失只是改了名字，变成了 Edit 模式。

很多用户在这里也会犯困惑，那 Edit 模式和 Agent 模式有什么区别？

正如它的名字，Edit 模式是专注于代码的编辑，它支持文件的创建和修改。

Agent 是在此基础上增加了思考、一些额外的工具调用能力，例如网络搜索、终端命令执行等。相当于 Ask + Edit 的组合。

很有意思的是以前 Normal 是默认模式，Agent 需要手动切换。而现在 Agent 是默认模式，Edit 需要手动切换。

建议大家这里直接选中默认的 Agent 模式。

## Agent 模式详解

Agent 模式是 Chat 窗口中最强大的功能，它像一个真实的编程助手，可以主动帮你完成各种复杂的编程任务：

* 自动获取相关上下文
* 执行文件创建、修改、删除操作
* 运行终端命令（需要开启 Yolo 模式）
* 自动代码库搜索（Codebase 功能）
* 执行过程中如果发现错误，会尝试自动修复错误
* 呼叫 MCP 功能，只有在 Agent 模式下能使用
* 自动进行网络搜索

让我们通过一个实际的例子来看看 Agent 模式的强大之处。在这个例子中，我们只需要告诉 Agent："帮我为排序算法创建一个测试文件，添加性能测试"，Agent 就会自动：

1. **分析项目结构**：
   * 自动搜索代码库发现现有的 sort.js 文件
   * 理解已实现的冒泡排序算法
   * 确定测试文件的最佳位置
   * 创建测试文件

![image.png](https://p3-juejin.byteimg.com/tos-cn-i-k3u1fbpfcp/187cc4315d614fe38da307207e8648db~tplv-k3u1fbpfcp-jj-mark:1600:0:0:0:q75.jpg#?w=2514&h=1209&s=462960&e=png&b=181818)

2. **自动错误修复**：

当上面代码完成后，最后会提示我们执行运行测试命令。

![image.png](https://p9-juejin.byteimg.com/tos-cn-i-k3u1fbpfcp/f2839396e7ac427680e83ee1cb8ebd4f~tplv-k3u1fbpfcp-jj-mark:1600:0:0:0:q75.jpg#?w=1079&h=383&s=40258&e=png&b=161616)

看起来没那么顺利，运行命令后报错了，不过别担心，我们可以直接将终端的错误信息一键添加道 Chat 中，让 Agent 自动修复。

![image.png](https://p1-juejin.byteimg.com/tos-cn-i-k3u1fbpfcp/3bd6bee4cd774acdb8d33bac6c808065~tplv-k3u1fbpfcp-jj-mark:1600:0:0:0:q75.jpg#?w=1549&h=543&s=150417&e=png&b=171717)

如果执行期间有错误，它会自动修复。

3. **自动运行测试命令**：

最后点击 Run 按钮后，会自动执行 `npm run test` 命令，并在 Cursor Chat 窗口展示测试结果。

![image.png](https://p6-juejin.byteimg.com/tos-cn-i-k3u1fbpfcp/d0e09b78928044329eebae0fe0ffbb16~tplv-k3u1fbpfcp-jj-mark:1600:0:0:0:q75.jpg#?w=611&h=617&s=82803&e=png&b=161616)

在上图中，我们可以看到 Agent 的工作流程：

1. **主动行为**：

   * 自动分析了项目中的排序算法
   * 提出了添加性能测试的具体方案
   * 创建了必要的测试文件

2. **文件操作**：

   * 创建了 sort.test.js 文件
   * 自动导入了排序函数
   * 添加了测试辅助函数

3. **终端集成**：

   * 提示运行测试命令
   * 展示测试结果
   * 所有命令都会先征求你的同意（前提是 Yolo 模式为关闭状态）

4. **智能搜索**：

   * 自动找到相关的排序算法文件
   * 分析代码依赖关系
   * 提供相关代码建议

5. **上下文管理**：

   * 自动包含了相关文件的内容
   * 理解代码之间的关联
   * 保持测试代码风格一致

6. **错误自动修复**：

   * 如果执行期间有错误，它会自动修复。
   * 我们还可以将错误信息直接添加到 Cursor Chat 中，让 Agent 自动修复。

这个例子展示了 Agent 模式如何自动化完成复杂任务。它不仅仅是执行你的命令，而是：

* 主动思考下一步该做什么
* 自动创建和组织文件
* 提供完整的解决方案
* 确保代码质量和一致性

## Chat 窗口回滚&撤销

在 Chat 窗口中，右下角有一个 Restore 按钮，可以回滚到之前的版本

![image.png](https://p3-juejin.byteimg.com/tos-cn-i-k3u1fbpfcp/560498f3634a434081b1451ec7d375bb~tplv-k3u1fbpfcp-jj-mark:1600:0:0:0:q75.jpg#?w=1051&h=469&s=103663&e=png&b=111111)

在回滚之后，还可以使用撤销按钮，撤销回滚。

![image.png](https://p9-juejin.byteimg.com/tos-cn-i-k3u1fbpfcp/59a17e699f664500a0e2c88838fc2a06~tplv-k3u1fbpfcp-jj-mark:1600:0:0:0:q75.jpg#?w=643&h=302&s=34095&e=png&b=181818)

这里还是推荐大家及时通过 Git 的版本控制来管理代码的每次主要变更。

## 布局选择

Chat 窗口提供了两种布局模式，可以通过右上角的按钮快速切换：

### Pane 模式（默认）

Pane 模式是默认的布局方式，将窗口分为左右两部分。在右上角点击 "Open Chat as Editor" 可以切换到 Editor 模式：

![image.png](https://p1-juejin.byteimg.com/tos-cn-i-k3u1fbpfcp/79943b061ab540b78714d1b9560bc086~tplv-k3u1fbpfcp-jj-mark:1600:0:0:0:q75.jpg#?w=646&h=274&s=30577&e=png&b=1a1a1a)

### Editor 模式

Editor 模式类似于一个正常的编辑器，您可以移动它、分割它，甚至将其放在单独的窗口中。

![image.png](https://p9-juejin.byteimg.com/tos-cn-i-k3u1fbpfcp/6e4dd048214548debfa66cd9d3eb937a~tplv-k3u1fbpfcp-jj-mark:1600:0:0:0:q75.jpg#?w=1185&h=305&s=106464&e=png&b=191919)

0.46 版本之前还有一个浮动模式，可以来回拖动，最新版本已经找不到了！

## Chat 配置

Cursor 有很多设置选项，可以调整 Chat 的使用方式。下面介绍每个设置项：

![image.png](https://p1-juejin.byteimg.com/tos-cn-i-k3u1fbpfcp/7368d8ec9f644dba9962c1c883d4c14d~tplv-k3u1fbpfcp-jj-mark:1600:0:0:0:q75.jpg#?w=794&h=310&s=37231&e=png&b=1a1a1a)

![image.png](https://p9-juejin.byteimg.com/tos-cn-i-k3u1fbpfcp/85c7031783fc4b84bf33c01f2c6e116c~tplv-k3u1fbpfcp-jj-mark:1600:0:0:0:q75.jpg#?w=750&h=454&s=45105&e=png&b=1a1a1a)

### 1\. 基础设置

#### Auto-scroll to bottom（自动滚动到底部）

* 作用：新消息出现时，自动滚动到聊天窗口底部
* 建议：打开此选项可以方便看到 AI 的最新回复
* 适用：长对话很有用，默认是打开的

#### Auto-apply to files outside context（自动应用到上下文外的文件）

* 作用：允许在编辑模式下自动修改当前上下文外的文件
* 建议：如果需要改动多个文件，建议打开
* 注意：可能会改到不相关的文件，要小心，也是默认打开的

### 2\. 高级设置

#### Enable yolo mode（启用 yolo 模式）

* 作用：让 Agent 直接执行命令和写文件，不需要确认
* 适用：想让 AI 自动完成任务时，比如新建项目
* 风险：可能造成文件意外修改，要小心使用
* 建议：新手最好关闭
* 说明：默认是关闭的，后面会详细介绍 agent + yolo 模式

#### Large context（大上下文窗口）

* 作用：使用更长的上下文窗口
* 好处：可以更好地理解代码
* 坏处：会用掉更多请求次数
* 建议：处理大项目时可以打开
* 说明：这是 Cursor 0.45 版本新加的功能，默认关闭

### 3\. 界面设置

#### Collapse input box pills（折叠输入框标签）

* 作用：在输入框中折叠标签
* 目的：节省屏幕空间
* 适用：屏幕小时很有用

#### Iterate on lints（自动修复 lint 错误）

* 作用：自动修复代码中的 lint 错误
* 好处：提高代码质量
* 建议：保持打开，默认打开状态

### 4\. 智能功能

#### Review changes（审查更改）- Beta

* 作用：列出并分组显示聊天中的所有更改
* 用途：方便查看代码变动
* 设置：可以自定义显示按钮位置

#### Web Search Tool（网络搜索工具）- Beta

* 作用：允许 Agent 模式下搜索网络获取信息，相当于手动 @web 搜索
* 好处：可以获取最新信息
* 适用：需要查找新技术或解决方案时

### 配置建议

1. **新手设置**：

   * ✅ 打开：自动滚动、自动应用、自动修复错误
   * ❌ 关闭：yolo 模式、大上下文、测试版功能
   * 目的：安全稳定，避免出错
   * 说明：按照默认状态设置即可

2. **高级用户设置**：

   * ✅ 打开：所有自动功能、大上下文、网络搜索
   * 🤔 视情况：yolo 模式、界面设置
   * 目的：提高效率，充分使用高级功能

3. **团队协作设置**：

   * ✅ 打开：审查更改、自动修复错误
   * ❌ 关闭：yolo 模式
   * 统一：界面设置
   * 目的：确保代码质量和团队合作

这些设置可以根据你的习惯和需要来调整，选择最适合你的工作方式。

## 使用技巧

* 使用 `⌘ + I` 打开 Chat 窗口 Agent 模式
* 使用 `⌘ + N` 创建新的 Chat 会话，这个命令是建立在 Chat 窗口中的，如果当前没有打开 Chat 窗口，则无法使用。
* 使用 `⌘ + .` 切换 Ask/Edit/Agent 模式
* 通过 `@` 符号添加特定上下文
* 使用检查点（Checkpoints）功能随时回退更改
* 只是提问问题，建议 Ask 模式
* 需要 Agent 执行任务，建议 Agent 模式，例如有文件的修改、命令的执行等

## 总结

Agent 模式让 Cursor 不仅是一个代码编辑器，更是一个真正的编程伙伴，能够理解你的意图，主动思考解决方案，并自动执行必要的操作。掌握 Agent 模式，将极大提升你的编程效率和体验。