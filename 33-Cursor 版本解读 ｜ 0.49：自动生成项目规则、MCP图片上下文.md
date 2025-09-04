AI新手网，https://aixinshou.com/  全站9.9元终身免费下载！

Cursor 0.49 版本近日刚刚发布，Cursor 每次都会先推送一部分用户，相信有的已经收到了更新。

本文主要介绍 Cursor 0.49 版本的主要新功能和改进。这个版本带来了许多实用的更新，下文给大家介绍每个新功能的使用。

本次更新内容
------

*   规则生成更智能
*   聊天历史更易访问
*   代码审查更简单
*   MCP 支持图片上下文
*   改进的终端控制
*   全局忽略文件
*   新增模型支持，AI 能力全面升级
*   项目结构上下文支持（Beta）

规则生成更智能
-------

在新版本中，你可以直接在对话中使用 `/Generate Cursor Rules` 命令生成规则，不需要离开聊天界面就能定义 AI 助手的行为方式。

我觉得这个功能很棒，AI 应该是让我们越来越简化，而不是越来越复杂，一开始就配置很多复杂的规则。

### 1\. 自动生成规则

我们基于第三个实战项目 "文生图微信小程序"，来测试这个功能，正好这个项目也是基于 Cursor 0.49 版本开发的。

打开右侧 Chat 面板，创建一个新对话，输入 `/` 后，会看到一个命令列表，选择 `Generate Cursor Rules` 命令，按回车键即可，无需多余的提示词。

![](https://p3-juejin.byteimg.com/tos-cn-i-k3u1fbpfcp/2d4ca90825704f82af428f676ff7428c~tplv-k3u1fbpfcp-jj-mark:1600:0:0:0:q75.jpg#?w=650&h=256&s=24506&e=png&b=181818)

如果发现项目根目录没有 `.cursor/rules` 目录，AI 会自动创建一个（前提是要开启 Yolo 模式）。

以下展示部分的生成过程。

首先，Cursor 会检索项目目录结构，进一步检查一些主要的文件，进行规则的生成。

![](https://p3-juejin.byteimg.com/tos-cn-i-k3u1fbpfcp/1fbe85c352e9473d8a9f266e88a2b68f~tplv-k3u1fbpfcp-jj-mark:1600:0:0:0:q75.jpg#?w=654&h=843&s=113668&e=png&b=161616)

![](https://p3-juejin.byteimg.com/tos-cn-i-k3u1fbpfcp/be0bf9d5fc9c4ca286159cc50a35553a~tplv-k3u1fbpfcp-jj-mark:1600:0:0:0:q75.jpg#?w=650&h=501&s=120668&e=png&b=141414)

以下为生成的规则文件。

结果相对还是准确的，这个项目是完全基于 Cursor 开发的，我们没有手动改过一行代码，因此里面的一些代码风格，编写习惯，AI 助手都能很好的理解。

![](https://p3-juejin.byteimg.com/tos-cn-i-k3u1fbpfcp/f12dba12898a4b69aaea3f2f7d29739e~tplv-k3u1fbpfcp-jj-mark:1600:0:0:0:q75.jpg#?w=1121&h=601&s=163602&e=png&b=181818)

我在另一个团队合作的大项目中做了测试，那个项目的文件数都有大概 1000 个左右，Cursor 的自动生成规则，第一次只是粗略的生成，效果一般，可能和项目复杂度有关，因为这个项目不是一个人开发的，团队多人合作，虽然也要求了编码风格，但是每个人写的代码风格还是不一样，这样的项目对 AI 助手来说，理解成本也很高。

第一次生成之后，如果你继续执行 `/Generate Cursor Rules` 命令，它也会继续完善规则。

### 2\. 加以描述生成规则

我们还可以加以描述，让 AI 助手生成更符合我们需求的规则。例如，之前我们在 "文生图微信小程序" 项目的需求分析一章节中，就专门做了样式设计，因此我们就可以让 AI 助手帮助我们生成样式设计规则。

输入以下提示词：

```css
我对当前项目的样式设计比较满意，请你写一下当前项目设计规则，以供迭代参考 /Generate Cursor Rules 
```

![](https://p3-juejin.byteimg.com/tos-cn-i-k3u1fbpfcp/855d5b979e3240278051fab13bb77457~tplv-k3u1fbpfcp-jj-mark:1600:0:0:0:q75.jpg#?w=650&h=158&s=22988&e=png&b=191919)

部分生成结果如下：

![](https://p3-juejin.byteimg.com/tos-cn-i-k3u1fbpfcp/ea8d813fb48940a7b24e86f8847720fa~tplv-k3u1fbpfcp-jj-mark:1600:0:0:0:q75.jpg#?w=636&h=650&s=104507&e=png&b=161616) ![](https://p3-juejin.byteimg.com/tos-cn-i-k3u1fbpfcp/4e13d08aa2a54f2a95dfb5eb8789e069~tplv-k3u1fbpfcp-jj-mark:1600:0:0:0:q75.jpg#?w=646&h=908&s=205416&e=png&b=141414)

看下最终的生成结果，UI 规范和样式设计规则都有了。

![](https://p3-juejin.byteimg.com/tos-cn-i-k3u1fbpfcp/a4b4db44a379456c9c6f87409acca28f~tplv-k3u1fbpfcp-jj-mark:1600:0:0:0:q75.jpg#?w=1295&h=1143&s=272210&e=png&b=171717)

### 3\. 规则类型的一些优化

*   对于设置了路径模式的 `Auto Attached` 规则，AI 助手现在会在读取或写入文件时自动应用正确的规则。
*   标记为 `Always` 的规则现在能在更长的对话中持续生效，规则编辑也更加可靠了。

规则类型的一些解释，参见之前文章：[Cursor 规则类型](https://juejin.cn/book/7493106499665788940/section/7493165389642579980#heading-2 "https://juejin.cn/book/7493106499665788940/section/7493165389642579980#heading-2")

聊天历史更易访问
--------

聊天历史现在被移到了命令面板中。你可以通过 Chat 面板中的 "显示历史按钮" 来访问它。

![](https://p3-juejin.byteimg.com/tos-cn-i-k3u1fbpfcp/18a2412e7ff548dc9232a366cf6a34e8~tplv-k3u1fbpfcp-jj-mark:1600:0:0:0:q75.jpg#?w=1609&h=337&s=53500&e=png&b=1e1e1e)

或 `Command + Shift + P` 后输入 `Show Chat History` 命令

![](https://p3-juejin.byteimg.com/tos-cn-i-k3u1fbpfcp/cdfb803b134f4980b7cae1c50c2c5c10~tplv-k3u1fbpfcp-jj-mark:1600:0:0:0:q75.jpg#?w=722&h=340&s=61046&e=png&b=1f1f1f)

这样一来，查找以前的对话内容变得更加方便，不会打断你的工作流程。

代码审查更简单
-------

在每次对话结束时，Cursor 现在提供了内置的差异视图，让审查 AI 生成的代码变得更加简单。

你只需点击对话结束时的"Review changes"按钮，就能清晰地看到代码的变化。

![](https://p3-juejin.byteimg.com/tos-cn-i-k3u1fbpfcp/b2d51055c40e4e89b168469313a417c0~tplv-k3u1fbpfcp-jj-mark:1600:0:0:0:q75.jpg#?w=2367&h=994&s=500407&e=png&b=1f1f1f)

MCP 支持图片上下文
-----------

现在你可以在 MCP 服务器中传递图片作为上下文的一部分。例如屏幕截图、UI或其它具有视觉效果的内容。

Cursor 官方的 ChangeLog 中给了一个示例演示，描述了一句话，然后 AI 助手根据这句话，调用 MCP 工具 `screenshot_desktop` 获取屏幕截图，然后根据截图，生成 React代码。

![](https://p3-juejin.byteimg.com/tos-cn-i-k3u1fbpfcp/29160d7a665641a4a9f634dff27604ac~tplv-k3u1fbpfcp-jj-mark:1600:0:0:0:q75.jpg#?w=351&h=139&s=19911&e=png&b=191919) ![](https://p3-juejin.byteimg.com/tos-cn-i-k3u1fbpfcp/0d54327718b54fdda5a2e98e7d8ed079~tplv-k3u1fbpfcp-jj-mark:1600:0:0:0:q75.jpg#?w=338&h=305&s=81139&e=png&b=191919)

`screenshot_desktop` 工具对应的 MCP Server 我没有找到～，我使用的是 `@modelcontextprotocol/server-puppeteer` 这个 MCP Server 做为测试。

输入提示词：

```css
制作一个 Cursor 官网的截图并用 html 实现
```

![](https://p3-juejin.byteimg.com/tos-cn-i-k3u1fbpfcp/80c05f43cd184764af1b124c91ed0865~tplv-k3u1fbpfcp-jj-mark:1600:0:0:0:q75.jpg#?w=922&h=190&s=21636&e=png&b=191919)

以下是执行过程，首先 AI 助手会访问 Cursor 官网，获取截图，然后根据截图内容，按照我们的提示词要求，生成 HTML 代码。这里你也可以生成 React 代码，或者其它你想要的代码。

![](https://p3-juejin.byteimg.com/tos-cn-i-k3u1fbpfcp/063874c1eecc4285a226dee7d6984db8~tplv-k3u1fbpfcp-jj-mark:1600:0:0:0:q75.jpg#?w=900&h=921&s=431752&e=png&b=161616)

看下 html 代码效果，只能说某种程度上相似，但很难还原原图。

不过能直接截图并写识别图片内容写代码，这个功能还是很棒的。

![](https://p3-juejin.byteimg.com/tos-cn-i-k3u1fbpfcp/87caf7939cc74839bc8417b70e247307~tplv-k3u1fbpfcp-jj-mark:1600:0:0:0:q75.jpg#?w=1817&h=1098&s=723895&e=png&b=7b25be)

官方演示例子中所用到的 `screenshot_desktop`，如果有知道是哪个 MCP Server 的，欢迎留言哈。

改进的终端控制
-------

Cursor 增加了对 AI 助手启动的终端工作流程的更多控制。

现在你可以在命令运行前编辑它们，或者完全跳过它们。(如果开启 Yolo 模式，则不会出现这个提示，因为 Yolo 模式下，AI 助手会自动执行命令)

![](https://p3-juejin.byteimg.com/tos-cn-i-k3u1fbpfcp/7910719e5dbc49dea78c52a6ccd7880b~tplv-k3u1fbpfcp-jj-mark:1600:0:0:0:q75.jpg#?w=573&h=342&s=32329&e=png&b=242424)

"Pop-out" 按钮也被重命名为"Move to background"，更好地反映了其功能。这个是命令执行过程中有个按钮提示。

![](https://p3-juejin.byteimg.com/tos-cn-i-k3u1fbpfcp/95cf605ece654185833a1fbc3717e80f~tplv-k3u1fbpfcp-jj-mark:1600:0:0:0:q75.jpg#?w=558&h=145&s=23331&e=png&b=1a1a1a)

全局忽略文件
------

你现在可以通过用户级设置定义适用于所有项目的忽略模式。

这样可以将构建输出或机密等嘈杂或敏感的文件排除在提示之外，而不需要每个项目单独配置。

![](https://p3-juejin.byteimg.com/tos-cn-i-k3u1fbpfcp/50e72f477ff74622a699ae4680bd8c2b~tplv-k3u1fbpfcp-jj-mark:1600:0:0:0:q75.jpg#?w=1516&h=703&s=89297&e=png&b=1e1e1e)

新增模型支持，AI 能力全面升级
----------------

Cursor 0.49 新增了对多个强大 AI 模型的支持：

*   Gemini 2.5 Pro
*   Grok 3 和 Grok 3 Mini
*   GPT-4.1
*   o3 和 o4-mini

![](https://p3-juejin.byteimg.com/tos-cn-i-k3u1fbpfcp/c92a0dc147a04492a4c204e7d75bc7af~tplv-k3u1fbpfcp-jj-mark:1600:0:0:0:q75.jpg#?w=991&h=572&s=61140&e=png&b=000000)

项目结构上下文支持（Beta）
---------------

Cursor 引入了将项目结构包含在上下文中的选项，这会将你的目录结构添加到提示中。

这个官方的 ChangeLog 没有说明，应该是下面这个。

![](https://p3-juejin.byteimg.com/tos-cn-i-k3u1fbpfcp/59ef0886350c46c9b9ca0b421fed4ca1~tplv-k3u1fbpfcp-jj-mark:1600:0:0:0:q75.jpg#?w=993&h=204&s=30278&e=png&b=1e1e1e)

AI 助手现在能更清晰地了解你的项目是如何组织的。

如何更早体验到新版本
----------

1.  打开 Cursor 的设置，在 `Beta` 选项卡中，找到 `Update frequency` 选项，选择 `Early Access` 选项。

![](https://p3-juejin.byteimg.com/tos-cn-i-k3u1fbpfcp/3bf7ce07854247a580a533d8ae5d91d3~tplv-k3u1fbpfcp-jj-mark:1600:0:0:0:q75.jpg#?w=917&h=318&s=40189&e=png&b=1a1a1a)

这种方式还是需要等待 Cursor 官方给你灰度发布，才能收到更新。

2.  Github 上有个开源的仓库，维护了 0.36.2 版本之后所有 Cursor 的历史版本，地址：[github.com/oslook/curs…](https://github.com/oslook/cursor-ai-downloads%EF%BC%8C%E5%A6%82%E6%9E%9C%E6%9C%89%E7%89%88%E6%9C%AC%E6%9B%B4%E6%96%B0%EF%BC%8C%E5%8F%AF%E4%BB%A5%E6%89%8B%E5%8A%A8%E4%B8%8B%E8%BD%BD%E5%AE%89%E8%A3%85%E3%80%82 "https://github.com/oslook/cursor-ai-downloads%EF%BC%8C%E5%A6%82%E6%9E%9C%E6%9C%89%E7%89%88%E6%9C%AC%E6%9B%B4%E6%96%B0%EF%BC%8C%E5%8F%AF%E4%BB%A5%E6%89%8B%E5%8A%A8%E4%B8%8B%E8%BD%BD%E5%AE%89%E8%A3%85%E3%80%82")

![](https://p3-juejin.byteimg.com/tos-cn-i-k3u1fbpfcp/134872e78d9a4e8cb618812e1832715c~tplv-k3u1fbpfcp-jj-mark:1600:0:0:0:q75.jpg#?w=704&h=381&s=81676&e=png&b=ffffff)

* * *

_详情请参考 Cursor 官方更新日志：[www.cursor.com/cn/changelo…](https://www.cursor.com/cn/changelog/0-49 "https://www.cursor.com/cn/changelog/0-49")_

* * *