AI新手网，https://aixinshou.com/  全站9.9元终身免费下载！

本章我们将从零开始搭建翻译助手浏览器插件项目，并完成设置页面的实现。通过 Cursor 的 Yolo 模式，我们可以快速完成项目初始化和基础功能开发，大大提高开发效率。本文将详细介绍从项目搭建、页面开发到打包测试的完整流程，帮助你掌握浏览器插件开发的基本技能。

## 使用 Yolo 模式快速初始化项目

项目开始前，我们可以打开 Cursor 的 Yolo 模式。这样 Cursor 会自动完成整个初始化过程，我们几乎不需要参与。设置路径是：`Cursor` -> `首选项` -> `Cursor Settings` -> `Features` -> `Yolo`。

建议在禁止命令中添加 rm 命令，因为之前曾发生过误删整个项目的情况。这也是我们一直强调版本控制重要性的原因。

![image.png](https://p9-juejin.byteimg.com/tos-cn-i-k3u1fbpfcp/3998d4153f7949868f3721bbda7cab3c~tplv-k3u1fbpfcp-jj-mark:1600:0:0:0:q75.jpg#?w=1229&h=748&s=101682&e=png&b=1f1f1f)

接下来，我们需要：

1. 打开实现步骤文档，选中"阶段一：基础架构搭建"部分

![image.png](https://p9-juejin.byteimg.com/tos-cn-i-k3u1fbpfcp/1270d2dae1fa4e8eae1f2efb86af4dfb~tplv-k3u1fbpfcp-jj-mark:1600:0:0:0:q75.jpg#?w=798&h=226&s=64093&e=png&b=1c1c1c)

2. 使用 Command + i 快捷键，将选中内容添加到右侧聊天窗口

3. 选择 Agent 模式，推荐使用 `Claude 3.7 Sonnet` 或 `Claude 3.5 Sonnet` 模型

4. 输入简单提示词：

   ```swift
   根据 @需求文档.md @技术方案.md 完成阶段一：基础架构搭建
   ```

![image.png](https://p1-juejin.byteimg.com/tos-cn-i-k3u1fbpfcp/aec7901054494ddcbcb4567f7089eecd~tplv-k3u1fbpfcp-jj-mark:1600:0:0:0:q75.jpg#?w=489&h=184&s=25845&e=png&b=272727)

初始化过程中，你可能需要确认一些信息，按提示操作即可。整个过程很少需要人工干预。

下图展示了初始化完成后的项目目录结构和 Cursor 给出的总结：

![image.png](https://p3-juejin.byteimg.com/tos-cn-i-k3u1fbpfcp/41ce886be4dd41bea5ffc86492a14a4b~tplv-k3u1fbpfcp-jj-mark:1600:0:0:0:q75.jpg#?w=1394&h=912&s=193827&e=png&b=191919)

## 实现翻译助手的设置功能

完成基础架构后，我们开始实现设置页面：

1. 打开实现步骤文档，选中"阶段二：设置管理与设置页面"部分

![image.png](https://p6-juejin.byteimg.com/tos-cn-i-k3u1fbpfcp/60ad2709a8ec4fbd9002089bd58ae371~tplv-k3u1fbpfcp-jj-mark:1600:0:0:0:q75.jpg#?w=764&h=175&s=70265&e=png&b=1c1c1c)

2. 使用 Command + i 快捷键，将内容添加到聊天窗口

![image.png](https://p1-juejin.byteimg.com/tos-cn-i-k3u1fbpfcp/4c651f208b2d404eba95ea6c77d9ee42~tplv-k3u1fbpfcp-jj-mark:1600:0:0:0:q75.jpg#?w=871&h=193&s=37347&e=png&b=262626)

3. 根据页面与功能的关联关系，将相关页面文件和模块文件拖到聊天窗口中

![image.png](https://p3-juejin.byteimg.com/tos-cn-i-k3u1fbpfcp/171d788759654aceb33e72e487d518b9~tplv-k3u1fbpfcp-jj-mark:1600:0:0:0:q75.jpg#?w=742&h=264&s=65855&e=png&b=1e1e1e)

4. 等待 Cursor 完成任务

## 打包浏览器插件

Cursor 完成代码编写后，我们需要将项目打包成 Chrome 浏览器插件格式。

虽然可以直接用 `npm run build` 命令打包，但建议先让 Cursor 帮我们完成这个任务。如果打包过程出现错误，Cursor 会自动修复。

打包步骤：

1. 准备一个图片作为插件图标，命名为 `icon.png` 并放到项目根目录（icon 是 Chrome 浏览器插件的必须文件）

2. 在 Cursor 聊天窗口输入提示词，并将图标拖入输入框：

   ```css
    打包文件需要上传 Chrome 浏览器进行测试，icon 请使用 @icon.png
   ```

打包完成后，项目根目录下会生成 `dist` 文件夹，里面包含所有打包文件。

![image.png](https://p6-juejin.byteimg.com/tos-cn-i-k3u1fbpfcp/05cc24c82248494dbadc2fa568011ea5~tplv-k3u1fbpfcp-jj-mark:1600:0:0:0:q75.jpg#?w=439&h=398&s=36377&e=png&b=181818)

## 在 Chrome 中安装和测试插件

安装步骤：

1. 在 Chrome 浏览器打开 `chrome://extensions/` 页面
2. 点击"加载已解压的扩展程序"按钮
3. 选择项目根目录下的 `dist` 文件夹（不需要压缩，直接选择即可）

![image.png](https://p6-juejin.byteimg.com/tos-cn-i-k3u1fbpfcp/00460f9b878947ada1d8585fd2ec79a1~tplv-k3u1fbpfcp-jj-mark:1600:0:0:0:q75.jpg#?w=578&h=314&s=32604&e=png&b=1d1e20)

![image.png](https://p1-juejin.byteimg.com/tos-cn-i-k3u1fbpfcp/7a6ab61c9ea747ea8898f0c1726b1638~tplv-k3u1fbpfcp-jj-mark:1600:0:0:0:q75.jpg#?w=798&h=433&s=80637&e=png&b=23211e)

安装完成后，你可以在 Chrome 扩展程序列表中看到我们的插件。插件名称和描述是 Cursor 在打包时自动提取的项目信息。如需修改，可以在聊天窗口中提示 Cursor 帮忙调整。

![image.png](https://p6-juejin.byteimg.com/tos-cn-i-k3u1fbpfcp/5900795de82b4794a3147ed75a7b17f4~tplv-k3u1fbpfcp-jj-mark:1600:0:0:0:q75.jpg#?w=425&h=271&s=30206&e=png&b=252528)

## 测试翻译助手设置页面

现在我们来测试插件功能：

1. 打开 Chrome 浏览器，找一个英文网页（我们主要测试英译中功能），我的测试用网页：[`https://article.arunangshudas.com/how-do-you-monitor-a-node-js-application-in-production-7a14cfc41367`](https://article.arunangshudas.com/how-do-you-monitor-a-node-js-application-in-production-7a14cfc41367 "https://article.arunangshudas.com/how-do-you-monitor-a-node-js-application-in-production-7a14cfc41367")

2. 点击浏览器地址栏右侧的"扩展程序"图标，然后点击"DeepSeek翻译助手"

![image.png](https://p3-juejin.byteimg.com/tos-cn-i-k3u1fbpfcp/139784e40eee46c9a0d4186d3c7e4fc0~tplv-k3u1fbpfcp-jj-mark:1600:0:0:0:q75.jpg#?w=538&h=193&s=34503&e=png&b=242424)

3. 首先会打开翻译助手主页面。虽然我们只计划先做设置页面，但 Cursor 也已经帮我们实现了主页面

![image.png](https://p3-juejin.byteimg.com/tos-cn-i-k3u1fbpfcp/ec003451393e4e7192257d9612a6d695~tplv-k3u1fbpfcp-jj-mark:1600:0:0:0:q75.jpg#?w=261&h=337&s=16984&e=png&b=ffffff)

4. 点击"设置"按钮，进入设置页面

5. 在设置页面中，我们可以看到实现的功能与之前设计的布局很接近，但还有一些细节需要调整

6. 输入 DeepSeek API Key 后，设置成功保存（获取 API Key 的方法请参考之前文章 [TODO]()）

![image.png](https://p1-juejin.byteimg.com/tos-cn-i-k3u1fbpfcp/459cee16bcd1498a99cb4c39dac5f4cc~tplv-k3u1fbpfcp-jj-mark:1600:0:0:0:q75.jpg#?w=678&h=1137&s=74860&e=png&b=ffffff)

## 总结与展望

在本章中，我们成功完成了翻译助手浏览器插件的基础架构搭建和设置页面实现。通过 Cursor 的 Yolo 模式，我们大大简化了开发流程，让 AI 辅助我们完成了大部分代码编写工作。

我们的主要成果包括：

1. 使用 Yolo 模式快速初始化项目架构
2. 实现了设置页面，支持 DeepSeek API Key 的配置和保存
3. 完成了插件打包和安装流程
4. 初步测试了插件的基本功能

目前我们已经完成了设置页面的实现，但还不能测试翻译功能。在下一章中，我们将继续开发翻译功能模块，实现网页内容的实时翻译，并优化用户体验。通过这个项目，你将全面掌握浏览器插件开发的完整流程和技巧。