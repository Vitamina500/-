AI新手网，https://aixinshou.com/  全站9.9元终身免费下载！

本章介绍如何利用 AI 工具快速生成高质量的需求文档、技术方案、页面布局示意图。通过 Cursor 这一强大的 AI 编程助手，我们可以大幅提高文档编写效率，减少重复工作，让开发者把更多精力放在创造性工作上。下面我们以一个浏览器翻译插件为例，展示整个文档生成过程。

注：这个项目使用的是 Claude 3.7 Sonnet 模型。

## 创建项目

大家先创建一个项目，例如 `ai-chrome-deepseek-translate-plugin`，然后用 Cursor 打开这个项目，后续我们也会在该目录搭建项目。

建议通过章节 [版本控制]() 中介绍的方式，从 Github 创建，然后克隆到本地。并且全程一定要用版本控制，及时做提交，避免 Cursor 给我们改出来问题，还能通过版本控制回退。

## 需求分析文档

打开 Cursor 聊天窗口，输入下面的提示词，生成需求分析文档。

```markdown
实现一个 Chrome 浏览器翻译插件，需求是
1. 可以对一篇文章进行完整翻译
2. 可以对翻译后的文章进行下载，下载的格式包括 Mardkown、PDF
3. 核心翻译实现使用 DeepSeek API
4. 页面功能简约，主要围绕文章一键翻译和下载
5. 翻译过的文章不需要保存为历史记录

帮我实现需求文档，这个只是需求文档，不包含技术实现。结果保存到 docs 目录下的 需求文档.md
```

![image.png](https://p6-juejin.byteimg.com/tos-cn-i-k3u1fbpfcp/e2fb7e9c23154afca7d96d795120d871~tplv-k3u1fbpfcp-jj-mark:1600:0:0:0:q75.jpg#?w=714&h=319&s=50323&e=png&b=282828)

![image.png](https://p1-juejin.byteimg.com/tos-cn-i-k3u1fbpfcp/be4852b611844ffbb733c1c5533f8cdc~tplv-k3u1fbpfcp-jj-mark:1600:0:0:0:q75.jpg#?w=1662&h=1252&s=294335&e=png&b=1f1f1f)

看了上面的需求分析结果，发现还少一些内容，输入下面的提示词来完善

```markdown
1. “翻译控制” 不需要
2. 下载只需要下载全文一种格式
3. 文件命名自动从原文标题生成合适的文件名，不需要自定义
4. 翻译过程采用流式响应，类似于 ChatGPT 的形式
```

![image.png](https://p3-juejin.byteimg.com/tos-cn-i-k3u1fbpfcp/d5bf93d4e2b94fdead404b523f0d58d7~tplv-k3u1fbpfcp-jj-mark:1600:0:0:0:q75.jpg#?w=1666&h=796&s=244090&e=png&b=1f1f1f)

## 添加 DeepSeek API 文档

这个是为我们下面的技术方案和后续实现翻译核心功能准备，让 AI 对 DeepSeek API 有更深入的了解。

我们写代码前要先看文档，Cursor 也需要这样。在 Docs 中加入 DeepSeek API 文档后，Cursor 可以快速找到 DeepSeek 相关内容。

先打开 Cursor Docs 设置。路径是：`Cursor` -> `首选项` -> `Cursor Settings` -> `Features` -> `Docs`，下面是设置好的界面。

![image.png](https://p1-juejin.byteimg.com/tos-cn-i-k3u1fbpfcp/c83b34c8c7d9450492fb648082caac79~tplv-k3u1fbpfcp-jj-mark:1600:0:0:0:q75.jpg#?w=1068&h=445&s=80008&e=png&b=1f1f1f)

点击 `Add new doc` 按钮，加入新文档，如图所示

![image.png](https://p9-juejin.byteimg.com/tos-cn-i-k3u1fbpfcp/6cfcff04b178486da205ae80a2bb23e3~tplv-k3u1fbpfcp-jj-mark:1600:0:0:0:q75.jpg#?w=759&h=292&s=21156&e=png&b=222222)

这个文档会在后面的翻译功能实现中用到。

## 技术方案文档

新开一个聊天窗口，输入下面的提示词，生成技术方案文档。

```swift
根据  @需求文档.md  生成一个技术方案文档，以 Chrome 浏览器插件的方式实现，包含项目目录结构。

翻译采用 DeepSeek API，文档参见 @DeepSeek

注意，这只是一个技术方案文档，不需要写具体代码实现，只需要写技术方案即可。

结果保存到 docs/技术方案.md 文件中
```

输入 @ 符号，会让你选择文件或文档，`@DeepSeek` 是我们前面添加的文档，前面有个书的图标，表示这是文档。

![image.png](https://p3-juejin.byteimg.com/tos-cn-i-k3u1fbpfcp/ef1dfbbbf1214e6f8307d974253a4bd2~tplv-k3u1fbpfcp-jj-mark:1600:0:0:0:q75.jpg#?w=1208&h=538&s=97183&e=png&b=313131)

说实话这技术方案文档比我写的还专业。

![image.png](https://p9-juejin.byteimg.com/tos-cn-i-k3u1fbpfcp/0b4a05173f3b43efbc4137db9e831750~tplv-k3u1fbpfcp-jj-mark:1600:0:0:0:q75.jpg#?w=951&h=793&s=133524&e=png&b=1d1d1d)

看了前面生成的技术方案文档，我们还可以加一些功能描述，这个文档是给 Cursor 看的，要详细一些。

文档描述越详细，Cursor 生成的代码越符合我们的需求。

```markdown
1. 翻译后的内容渲染展示方式可以在右侧展示一个面板，展示翻译后的内容。
2. 翻译后的内容要和原文的页面排版格式保持一致。
3. 如果涉及到一些图片资源，图片不需要翻译，但是图片也应该一同在翻译后的面板展示
4. 下载的内容也应该包含图片信息
```

每次对前文的修改 Cursor 会用 git diff 的方式显示出来，如下图所示。

红色背景表示删除，绿色背景表示新增。

![image.png](https://p1-juejin.byteimg.com/tos-cn-i-k3u1fbpfcp/e86859b48a314123ae24956fef865c02~tplv-k3u1fbpfcp-jj-mark:1600:0:0:0:q75.jpg#?w=824&h=1037&s=238909&e=png&b=1d1d1d)

如果满意，点击 Cursor 聊天窗口右下角的 Accept 按钮，也要用版本管理工具及时保存。

![image.png](https://p9-juejin.byteimg.com/tos-cn-i-k3u1fbpfcp/6b2dffbf64f74e0281382124bcbf59bb~tplv-k3u1fbpfcp-jj-mark:1600:0:0:0:q75.jpg#?w=420&h=202&s=15905&e=png&b=1b1b1b)

## 规划页面布局和实现步骤

Cursor 不会直接出原型，但我们可以用提示词让 Cursor 用 ASCII 字符画出页面布局。这个 ASCII 字符画的页面布局，Cursor 在后面的代码实现中会参考。

这类需求，你描述越详细，Cursor 生成的代码越符合你的需求。我们让 Cursor 分文件、按顺序保存，给我们规划实现步骤。

新开一个聊天窗口，输入下面的提示词，规划页面布局和实现步骤。

```swift
根据 @需求文档.md @技术方案.md   文档，规划实现的步骤，按页面、功能模块划分，用ASCII字符画出页面布局。

结果要分文件，例如：示意图-页面.md 或 示意图-页面-模块.md 等等。按照实现步骤对文件加上序号。

页面设计简约，不需要冗余的功能，主要突出对网页文章的一键翻译和下载。

结果以 Markdown 格式写入到 docs/ 目录下。
```

![image.png](https://p9-juejin.byteimg.com/tos-cn-i-k3u1fbpfcp/a9ccec62344c4d398278f044d14cdfa1~tplv-k3u1fbpfcp-jj-mark:1600:0:0:0:q75.jpg#?w=851&h=336&s=60131&e=png&b=2a2a2a)

下面是 Cursor 生成的页面布局示意图和实现步骤。

![image.png](https://p9-juejin.byteimg.com/tos-cn-i-k3u1fbpfcp/8e5235595aee49aaa8df99254e399b6a~tplv-k3u1fbpfcp-jj-mark:1600:0:0:0:q75.jpg#?w=407&h=577&s=37169&e=png&b=1d1d1d)

![image.png](https://p3-juejin.byteimg.com/tos-cn-i-k3u1fbpfcp/487f9155a5744f1eb1dfd26e29fdaec6~tplv-k3u1fbpfcp-jj-mark:1600:0:0:0:q75.jpg#?w=1020&h=978&s=248332&e=png&b=1c1c1c)

我们需要审核 Cursor 生成的内容，按它的规划先做核心模块，再写页面，这样前面核心模块做完后，我们不知道效果如何。另外根据我之前的使用，功能模块 Cursor 很少能一次生成让你很满意的。

提出我们的疑问，输入下面的提示词。

```
页面和模块是不是应该关联？如果先完成核心模块，在写页面，也看不到效果
```

![image.png](https://p1-juejin.byteimg.com/tos-cn-i-k3u1fbpfcp/f3b255923d58458c87624eb2970a9f37~tplv-k3u1fbpfcp-jj-mark:1600:0:0:0:q75.jpg#?w=721&h=568&s=86783&e=png&b=1c1c1c)

这次的规划更合理，页面和相关功能模块一起实现，这样我们能看到效果。

下面是最终生成的页面布局和实现步骤。

![image.png](https://p1-juejin.byteimg.com/tos-cn-i-k3u1fbpfcp/24af1443415744579ba129d8eb8414f1~tplv-k3u1fbpfcp-jj-mark:1600:0:0:0:q75.jpg#?w=782&h=1005&s=217701&e=png&b=1e1e1e)

## 总结

通过本章的实践，我们看到了 AI 在软件开发前期文档生成方面的强大能力。使用 Cursor 这样的 AI 工具，我们可以：

1. 快速生成符合标准的需求分析文档
2. 高效创建详细的技术方案文档
3. 直观规划页面布局和实现步骤
4. 不断优化和完善文档内容

这种方式不仅提高了开发效率，也保证了文档的质量和一致性。在实际项目中，我们可以把更多时间用于思考产品核心价值和用户体验，而不是花费大量时间在文档编写上。随着 AI 技术的不断发展，这种协作方式将成为未来软件开发的重要趋势。

前面这些清晰的文档设计，对于后续的代码实现非常有帮助。同时也会后期的维护带来便利。