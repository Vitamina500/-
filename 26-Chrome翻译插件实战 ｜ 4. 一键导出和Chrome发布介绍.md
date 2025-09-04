AI新手网，https://aixinshou.com/  全站9.9元终身免费下载！

这一章我们要实现翻译助手的导出功能，主要包括 Markdown 和 PDF 两种格式。这是翻译工具的最后一部分。

## 阶段七：文件导出与下载功能

我们先按照步骤指南，选中"阶段七：文件导出与下载功能"内容。

![image.png](https://p9-juejin.byteimg.com/tos-cn-i-k3u1fbpfcp/11371b0cec3c458eb567ed2fdda37420~tplv-k3u1fbpfcp-jj-mark:1600:0:0:0:q75.jpg#?w=891&h=180&s=68580&e=png&b=1b1b1b)

然后打开一个新窗口，用 Command + i 快捷键把选中内容添加到右侧聊天窗口。我们输入提示词，告诉 Cursor 要实现的功能。因为导出只需要两个按钮，而且 Cursor 之前已经实现了，所以不需要示意图。

![image.png](https://p9-juejin.byteimg.com/tos-cn-i-k3u1fbpfcp/9a43fe24a8f84a19bc47fb8aa62a81c1~tplv-k3u1fbpfcp-jj-mark:1600:0:0:0:q75.jpg#?w=696&h=204&s=32412&e=png&b=252525)

## 遇到的问题和解决过程

### 问题一：下载功能不工作

完成上面的任务后，我们发现两个问题：

1. 点击翻译助手主页面下面的下载 Markdown 按钮时，控制台有请求日志，但页面没有反应
2. 翻译结果右上角的下载按钮被一个白色长方形块挡住了

![image.png](https://p6-juejin.byteimg.com/tos-cn-i-k3u1fbpfcp/25f44c6336fb4a0ca421418240adb28d~tplv-k3u1fbpfcp-jj-mark:1600:0:0:0:q75.jpg#?w=1340&h=310&s=83293&e=png&b=fdfdfd)

我向 Cursor 发送提示词，但没有解决任何问题。这里我总结了两点经验：

1. 每次让 Cursor 只专注修复一个问题
2. 描述问题时要尽可能详细，比如那个白色长方形块上有文字，这些信息可以帮助 AI 快速定位

![image.png](https://p9-juejin.byteimg.com/tos-cn-i-k3u1fbpfcp/5a7fa7ef32df44609c1e5d47ec52a322~tplv-k3u1fbpfcp-jj-mark:1600:0:0:0:q75.jpg#?w=708&h=188&s=34306&e=png&b=282828)

### 解决长方形块遮挡问题

我直接告诉 Cursor 长方形块上的文字内容，让它修复这个问题。

![image.png](https://p9-juejin.byteimg.com/tos-cn-i-k3u1fbpfcp/62a5baa15e0f44de9a76ac0efd3bf714~tplv-k3u1fbpfcp-jj-mark:1600:0:0:0:q75.jpg#?w=683&h=125&s=18215&e=png&b=2a2a2a)

这次 Cursor 很快找到了问题位置，成功删除了长方形块。这说明提供足够的特征信息可以帮助 AI 快速定位问题。

![image.png](https://p6-juejin.byteimg.com/tos-cn-i-k3u1fbpfcp/8256b9fc82794d0dbc397a76b12f98f1~tplv-k3u1fbpfcp-jj-mark:1600:0:0:0:q75.jpg#?w=732&h=142&s=15438&e=png&b=fcfcfc)

### 修复下载 Markdown 功能

修复长方形块后，我们发现翻译结果面板右上角的下载按钮正常工作，但翻译助手主页面下方的下载按钮还是不正常。

我让 Cursor 复用翻译结果面板的下载功能，并修复主页面下方按钮的功能。

![image.png](https://p6-juejin.byteimg.com/tos-cn-i-k3u1fbpfcp/7dff6ea9d95c44db94769301cd508f02~tplv-k3u1fbpfcp-jj-mark:1600:0:0:0:q75.jpg#?w=677&h=247&s=34086&e=png&b=2b2b2b)

Cursor 很快就修复了这个问题。下面是导出的 Markdown 文件效果：

![image.png](https://p3-juejin.byteimg.com/tos-cn-i-k3u1fbpfcp/664bdf0489fc4d149a41dffb94f71ebb~tplv-k3u1fbpfcp-jj-mark:1600:0:0:0:q75.jpg#?w=1819&h=1330&s=733167&e=png&b=1b1b1b)

### 修复 PDF 导出功能

我们测试 PDF 导出功能时，发现下载的 PDF 是空白页面。

![image.png](https://p6-juejin.byteimg.com/tos-cn-i-k3u1fbpfcp/19f6621066f348f79608aaa0765c8c6b~tplv-k3u1fbpfcp-jj-mark:1600:0:0:0:q75.jpg#?w=2148&h=442&s=39023&e=png&b=fefefe)

根据 Cursor 的总结，PDF 导出功能每次都是重新提取 HTML 再转为 PDF，但不确定哪里出了问题。尝试了多次修复但都没成功。

最后我想到，既然导出 Markdown 功能正常，那么可以先导出 Markdown 文件，再转换为 PDF。我把这个想法告诉 Cursor，让它选择合适的库来实现。

![image.png](https://p9-juejin.byteimg.com/tos-cn-i-k3u1fbpfcp/c8a991326f8548f7a7f823dc2e001784~tplv-k3u1fbpfcp-jj-mark:1600:0:0:0:q75.jpg#?w=696&h=401&s=69799&e=png&b=292929)

这个过程也不是一次就成功的。每次有报错，我就把错误信息发给 Cursor，或者告诉它具体问题，让它修复。

![image.png](https://p9-juejin.byteimg.com/tos-cn-i-k3u1fbpfcp/28c743e47edc475eb21322035afe8f2b~tplv-k3u1fbpfcp-jj-mark:1600:0:0:0:q75.jpg#?w=687&h=402&s=52882&e=png&b=2b2b2b)

![image.png](https://p1-juejin.byteimg.com/tos-cn-i-k3u1fbpfcp/918e97ad6e084e14bce4949ed6c87dfb~tplv-k3u1fbpfcp-jj-mark:1600:0:0:0:q75.jpg#?w=682&h=126&s=12759&e=png&b=2a2a2a)

最终，我们成功实现了 PDF 导出功能，效果如下：

![image.png](https://p3-juejin.byteimg.com/tos-cn-i-k3u1fbpfcp/aac93ed1741c412eba3196a11920f108~tplv-k3u1fbpfcp-jj-mark:1600:0:0:0:q75.jpg#?w=2006&h=1310&s=407413&e=png&b=fdfdfd)

从导出的效果看，PDF 导出功能正常，但样式不如导出的 Markdown 我通过本地其它插件查看的效果好，这和实现时选择三方库有关，大家在做的时候想优化的，可以根据具体问题，向 Cursor 提问。

## 发布 Chrome 插件

如果插件只是自己使用就按照咱们目前开发的这种方式即可。如果想分享给朋友使用，可以将打包后的文件发送给对方。

但是如果要发布到 Chrome 浏览器应用商店，需要先注册 Chrome 网上应用店开发者账号。

1. 访问 [Chrome 应用商店开发者](https://chrome.google.com/webstore/devconsole/register "https://chrome.google.com/webstore/devconsole/register") 注册账号。
2. 使用您的 Google 账号登录。
3. 如果是首次使用，您需要支付一次性的开发者注册费（$5.00 USD）。

![image.png](https://p9-juejin.byteimg.com/tos-cn-i-k3u1fbpfcp/1751708c548247caa273b417a2ac186a~tplv-k3u1fbpfcp-jj-mark:1600:0:0:0:q75.jpg#?w=2022&h=1106&s=173786&e=png&b=ffffff)

这个支付的地区不支持中国大陆，所以需要使用国外的信用卡。Visa 信用卡显示支持，但我使用的时候提示卡无效...

如果有此需求的，注册这个账号会有一些麻烦。

当账号注册好之后，可以参考 Chrome 浏览器提供的这个[发布指南](https://support.google.com/chrome/a/answer/2714278?hl=zh-Hans "https://support.google.com/chrome/a/answer/2714278?hl=zh-Hans")。

## 总结与思考

在本章中，我们成功实现了翻译助手的导出功能，包括 Markdown 和 PDF 两种格式。通过这个过程，我们学到了几个重要经验：

1. **问题描述的重要性**：向 AI 描述问题时，提供详细的特征信息可以帮助它快速定位问题所在。

2. **分步解决问题**：将复杂问题拆分为小问题，让 AI 每次只专注解决一个问题，效率更高。

3. **灵活变通思路**：当一种方法不奏效时，尝试换一种思路。比如我们将 PDF 导出改为先导出 Markdown 再转换，成功解决了问题。

4. **错误信息的价值**：遇到错误时，将完整的错误信息提供给 AI，可以帮助它更准确地诊断和解决问题。

至此，我们的翻译助手已经完成了所有核心功能的开发，包括翻译、历史记录和导出功能。

在实际应用中，你可能还需要考虑更多导出格式，或者优化 PDF 的样式效果。这些都可以作为后续迭代的方向。