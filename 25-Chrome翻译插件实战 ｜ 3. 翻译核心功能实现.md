AI新手网，https://aixinshou.com/  全站9.9元终身免费下载！

本章我们将实现翻译助手的核心功能，包括弹出窗口界面、内容提取、翻译处理和结果展示。这些功能构成了插件的核心价值，让用户能够便捷地获取多语言内容的翻译。通过分步骤实现，我们将逐步构建一个功能完整的翻译工具。

## 阶段三：弹出窗口与基本控制

我们按照实现步骤指南，让 Cursor 根据示意图完善翻译助手的主页面。

首先选中"阶段三：弹出窗口与基本控制"内容。

![image.png](https://p6-juejin.byteimg.com/tos-cn-i-k3u1fbpfcp/4f76a469a070418b8a53464a321712f4~tplv-k3u1fbpfcp-jj-mark:1600:0:0:0:q75.jpg#?w=664&h=179&s=56336&e=png&b=1b1b1b)

然后用 Command + i 快捷键把选中内容添加到右侧聊天窗口。和之前一样，选择 Agent 模式，用 `Claude 3.7 Sonnet` 或 `Claude 3.5 Sonnet` 模型。记得要新打开一个窗口。

![image.png](https://p9-juejin.byteimg.com/tos-cn-i-k3u1fbpfcp/37aa3631739c4e59af048b71e5450c7d~tplv-k3u1fbpfcp-jj-mark:1600:0:0:0:q75.jpg#?w=520&h=206&s=31911&e=png&b=272727)

下面是实现的页面效果，它和示意图基本一致，不需要调整。

![image.png](https://p1-juejin.byteimg.com/tos-cn-i-k3u1fbpfcp/bc4cc6d453fa421e85c113195dacedcc~tplv-k3u1fbpfcp-jj-mark:1600:0:0:0:q75.jpg#?w=284&h=309&s=16213&e=png&b=fefefe)

示意图如下，可以对比看看：

```lua
+----------------------------------+
|       Chrome翻译插件             |
+----------------------------------+
|                                  |
| 语言选择:                        |
| +------------+  +------------+   |
| | 源语言 ▼   |  | 目标语言 ▼ |   |
| +------------+  +------------+   |
|                                  |
| +------------------------------+ |
| |        一键翻译页面         | |
| +------------------------------+ |
|                                  |
| 下载选项:                        |
| +------------+  +------------+   |
| |  Markdown  |  |    PDF     |   |
| +------------+  +------------+   |
|                                  |
| +------------------------------+ |
| |           设置             | |
| +------------------------------+ |
|                                  |
+----------------------------------+
```

## 阶段四和阶段五：翻译功能实现

阶段四是内容提取与初步显示，阶段五是翻译处理与结果展示。我们把这两个阶段一起实现，这样更容易在页面上查看效果。

选中 "阶段四：内容提取与初步显示" 和 "阶段五：翻译处理与结果展示" 的内容。

![image.png](https://p9-juejin.byteimg.com/tos-cn-i-k3u1fbpfcp/b41cbba1d7604c5ca711f0dfcfa10328~tplv-k3u1fbpfcp-jj-mark:1600:0:0:0:q75.jpg#?w=719&h=261&s=92354&e=png&b=1b1b1b)

新开一个窗口，把选中内容添加到右侧聊天窗口。输入下面的提示词，告诉 Cursor 要实现的模块功能和对应示意图。核心翻译功能用通过 `@doc` 命令指定 DeepSeek API 实现。

```perl
根据 @需求文档.md @技术方案.md 

分别实现：
1. 阶段四：内容提取与初步显示@04-示意图-内容页面.md @06-模块-内容提取.md 
2.  阶段五：翻译处理与结果展示 @07-模块-翻译处理.md 实现翻译的 DeepSeek API 文档 @Deepseek 
```

![image.png](https://p6-juejin.byteimg.com/tos-cn-i-k3u1fbpfcp/45c517aa27984665b3ef594b43ff4448~tplv-k3u1fbpfcp-jj-mark:1600:0:0:0:q75.jpg#?w=510&h=272&s=47660&e=png&b=2b2b2b)

这个阶段是整个插件的核心，也是最复杂的部分。Cursor 写页面很厉害，但多个模块交互时，很难一次完成，需要多次调整。

完成上述任务后，我们遇到第一个问题：点击"一键翻译页面"按钮后，按钮一直转圈，页面没反应。

我们可以把页面截图给 Cursor，告诉它问题。也可以提示可能的原因，让它排查。

![image.png](https://p1-juejin.byteimg.com/tos-cn-i-k3u1fbpfcp/124bea39f4944c8ca8c009b4e603a74b~tplv-k3u1fbpfcp-jj-mark:1600:0:0:0:q75.jpg#?w=853&h=169&s=26737&e=png&b=2a2a2a)

下面是生成的效果：

![image.png](https://p1-juejin.byteimg.com/tos-cn-i-k3u1fbpfcp/4644a49c73d94d218e04b4d82050a3e8~tplv-k3u1fbpfcp-jj-mark:1600:0:0:0:q75.jpg#?w=1258&h=319&s=100028&e=png&b=fcfcfc)

现在 DeepSeek 翻译面板已经显示出来，但页面内容没有正常渲染，显示的是 HTML 代码。不过翻译的中文内容已经显示出来了。这一步的目的已经达到，我们先提交一次，然后进行下一阶段。

## 阶段六：翻译面板完善与渲染优化

选中"阶段六：翻译面板完善与渲染优化"内容。

![image.png](https://p6-juejin.byteimg.com/tos-cn-i-k3u1fbpfcp/42b2d8ad7f654cd7be6381680bcfce51~tplv-k3u1fbpfcp-jj-mark:1600:0:0:0:q75.jpg#?w=630&h=195&s=68813&e=png&b=1b1b1b)

新开一个窗口，把选中内容添加到右侧聊天窗口，告诉 Cursor 要实现的功能和示意图。

![image.png](https://p1-juejin.byteimg.com/tos-cn-i-k3u1fbpfcp/649731fc6c3541c5b577449ba43b212f~tplv-k3u1fbpfcp-jj-mark:1600:0:0:0:q75.jpg#?w=618&h=222&s=37511&e=png&b=252525)

下面是初步实现的效果：

![image.png](https://p1-juejin.byteimg.com/tos-cn-i-k3u1fbpfcp/7864c3e6fc594b8f8c0af03332b408e3~tplv-k3u1fbpfcp-jj-mark:1600:0:0:0:q75.jpg#?w=1379&h=870&s=230964&e=png&b=fdfdfd)

我们发现几个问题：

1. 翻译内容虽然正常渲染了，但结果不完整
2. 控制台有警告："content.js:1 文本长度(29158)超过最大限制(8000)，将被截断"，这导致翻译不完整的原因
3. 发送给 DeepSeek API 的请求内容过长，都是 HTML 代码

如果只是简单说翻译内容不完整，Cursor 很难修复好。我们需要告诉它具体原因：文本内容过长超过了限制。我们可以建议用分批发送的方法，保证翻译结果完整。还要先把 HTML 内容转为 Markdown 格式再发送。

提示词如下：

```css
出现报错 “content.js:1 文本长度(29158)超过最大限制(8000)，将被截断”，之后导致翻译不完整

你应该在截断之后，分批次发送，如果内容过长，可以分次发送，保证最终的翻译结果是完整的

请先将提取的 HTML 内容转为 Markdown 格式发送到翻译接口，翻译面板要对 Markdown 内容做转换展示
```

优化后的效果如下：

![image.png](https://p3-juejin.byteimg.com/tos-cn-i-k3u1fbpfcp/c01a3e19887f4e2e937a338ef3c98c37~tplv-k3u1fbpfcp-jj-mark:1600:0:0:0:q75.jpg#?w=1372&h=780&s=219423&e=png&b=fdfdfd)

现在发送给翻译接口的内容已经从 HTML 转为 Markdown 格式了。根据控制台日志，也实现了分批发送。但我们发现一个新问题：翻译结果面板的图片没有正确加载。

我们先提交当前实现，再修复图片不显示的问题。

将当前实现打一个提交记录，再进行图片不展示问题修复。

## 图片不展示问题修复

修复这个 bug 时，我新开了一个聊天窗口。看似是个小问题，但花了最长的时间。Cursor 一直解决不了，让我很着急。

如果直接修改代码可能更快，但我想完全用 Cursor 实现，只能慢慢引导它。

我让 Cursor 打印关键日志信息，不断把这些信息粘贴给它，让它排查问题。最后干脆让它重写代码。

![image.png](https://p6-juejin.byteimg.com/tos-cn-i-k3u1fbpfcp/c7a96f2eef6d4954851ca2a513afadcf~tplv-k3u1fbpfcp-jj-mark:1600:0:0:0:q75.jpg#?w=744&h=236&s=33494&e=png&b=2b2b2b)

![image.png](https://p3-juejin.byteimg.com/tos-cn-i-k3u1fbpfcp/a994dd508cd34033b9d5c936c25964b1~tplv-k3u1fbpfcp-jj-mark:1600:0:0:0:q75.jpg#?w=747&h=248&s=31512&e=png&b=2b2b2b)

![image.png](https://p6-juejin.byteimg.com/tos-cn-i-k3u1fbpfcp/c4450646cbaa4fb385244da0a0ca31da~tplv-k3u1fbpfcp-jj-mark:1600:0:0:0:q75.jpg#?w=760&h=390&s=51163&e=png&b=2b2b2b)

![image.png](https://p6-juejin.byteimg.com/tos-cn-i-k3u1fbpfcp/d17c086ce5de4d2db7949b9b560c5af5~tplv-k3u1fbpfcp-jj-mark:1600:0:0:0:q75.jpg#?w=757&h=117&s=16460&e=png&b=2b2b2b)

尝试多次后仍未解决，我放弃了这次会话，点击右下角的 “Reject all” 不接受修改。

![image.png](https://p3-juejin.byteimg.com/tos-cn-i-k3u1fbpfcp/b099e4f84cab46518ce5b0e018bb08fc~tplv-k3u1fbpfcp-jj-mark:1600:0:0:0:q75.jpg#?w=756&h=212&s=20189&e=png&b=252525)

## 换个思路解决图片渲染问题

前面我们在响应过程中解析结果处理图片，现在换个思路。

让 Cursor 在所有内容翻译完成后，根据图片占位符规则替换为真实图片链接并显示。同时提醒它在写入图片占位符时保存提取的图片，替换时调用这些图片。

之前 Cursor 虽然保存了图片映射关系，但替换时没有调用，而是重新提取，导致对不上。这说明即使是简单逻辑，当模块多了后，对 AI 也有挑战。

这次交互两次后终于成功了。

![image.png](https://p1-juejin.byteimg.com/tos-cn-i-k3u1fbpfcp/b1f8021733b2448eb5f9a15f42b7777a~tplv-k3u1fbpfcp-jj-mark:1600:0:0:0:q75.jpg#?w=752&h=250&s=46043&e=png&b=2b2b2b)

![image.png](https://p6-juejin.byteimg.com/tos-cn-i-k3u1fbpfcp/58350a0a9add45929a0fd67537c9c430~tplv-k3u1fbpfcp-jj-mark:1600:0:0:0:q75.jpg#?w=749&h=384&s=63782&e=png&b=2c2c2c)

最终翻译面板效果如下，左侧是原文，右侧是我们插件的翻译结果：

![image.png](https://p9-juejin.byteimg.com/tos-cn-i-k3u1fbpfcp/bc92337ade50449ea70937140f5f457d~tplv-k3u1fbpfcp-jj-mark:1600:0:0:0:q75.jpg#?w=1264&h=1123&s=532721&e=png&b=fdfdfd)

翻译面板的主要功能已经完成。当然还有些细节可以优化，让界面更美观，但这需要更多时间和 Cursor 交互。下一节我们将实现导出功能。

## 总结与思考

在本章中，我们成功实现了翻译助手的核心功能：

1. **弹出窗口界面**：创建了直观的用户界面，包括语言选择、翻译按钮和下载选项
2. **内容提取**：从网页中提取需要翻译的内容
3. **翻译处理**：通过 DeepSeek API 实现多语言翻译
4. **结果展示**：优化了翻译结果的显示，包括正确渲染 Markdown 内容和图片

在实现过程中，我们遇到并解决了几个关键问题：

* 文本长度超限问题：通过分批发送解决
* HTML 转 Markdown：提高了翻译质量和渲染效果
* 图片渲染问题：通过占位符和映射关系实现

这个过程也展示了使用 AI 辅助编程的优势和挑战。Cursor 在页面实现方面表现出色，但在复杂逻辑和多模块交互时需要更多引导。有时简单的问题反而需要更多时间解决，这提醒我们在使用 AI 工具时要灵活调整策略，有时直接修改代码可能更高效。

下一章我们将继续完善翻译助手，实现导出功能，让用户能够以不同格式保存翻译结果。