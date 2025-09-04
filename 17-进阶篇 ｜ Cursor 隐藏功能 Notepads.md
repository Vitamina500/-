AI新手网，https://aixinshou.com/  全站9.9元终身免费下载！

在开发软件时，我们常常需要记录和分享各种信息。这些信息包括项目规则、代码样例、设计决定和团队规定。Cursor NotePads 工具可以帮助我们更好地管理这些信息，提高工作效率。

Cursor 一直就有一个隐藏的功能，那就是 NotePads，它可以帮助我们记录和共享各种信息。目前的 NotePads 功能还处于测试阶段，不确定未来会不会被废弃，但是在 Cursor 最新文档中还单独介绍了这个功能，这里大家可以了解下是做什么的。

## 什么是 NotePads？

Cursor 编辑器中的 NotePads 不只是一个简单的笔记工具。它是一个连接各种开发场景的工具。你可以把它看作是一个增强版的上下文分享工具，它的功能比传统的 `.cursorrules` 文件更强大。

## NotePads 的主要特点

**1\. 灵活的上下文共享**

在 0.46 版本之前，NotePads 可以在写代码（Composers）和 AI 对话（Chat）之间轻松切换。

但是 0.46 版本之后，Chat 界面做了合并，Agent 也能获取到 Ask 模式的上下文，所以 NotePads 的上下文分享功能变弱了。但如果你把 Ask 模式对话内容保存到 NotePads 中，这个内容在其它 Chat 窗口中也是可以看到的。

**2\. 丰富的内容支持**

* 支持动态引用已有的内容，使用 `@` 语法快速引用
* 支持文件附件，方便引用文档和参考资料
* 使用 Markdown 格式实现清晰的内容结构
* 可以包含代码片段、架构图等多种形式的内容

## 使用场景

### 1\. 项目模板管理

* 存储常用的代码模板
* 定义项目框架规则
* 维护统一的代码结构指南

### 2\. 技术文档中心

* 前端开发规范
* 后端接口文档
* 数据模型说明
* 系统架构图

### 3\. 团队规范制定

* 编码标准
* 命名规则
* Git 提交规范

## Cursor 中使用 NotePads

默认情况下 NotePads 是隐藏的，我们需要手动开启。

![image.png](https://p3-juejin.byteimg.com/tos-cn-i-k3u1fbpfcp/e22bf9e0fc074d509c593c89d5372142~tplv-k3u1fbpfcp-jj-mark:1600:0:0:0:q75.jpg#?w=891&h=415&s=55223&e=png&b=191919)

开启后，在左侧栏会多出一个 NotePads 的按钮，点击后就可以创建和编辑 NotePads。

![image.png](https://p6-juejin.byteimg.com/tos-cn-i-k3u1fbpfcp/c40689d74c414b079ba1068fc95687e8~tplv-k3u1fbpfcp-jj-mark:1600:0:0:0:q75.jpg#?w=358&h=109&s=6232&e=png&b=151515)

参考官方文档：[NotePads](https://docs.cursor.com/beta/notepads "https://docs.cursor.com/beta/notepads") 提供的例子，我们创建一个开发规范的 NotePads。

![image.png](https://p3-juejin.byteimg.com/tos-cn-i-k3u1fbpfcp/5d8463801d254bce81d2588cc56e0a03~tplv-k3u1fbpfcp-jj-mark:1600:0:0:0:q75.jpg#?w=759&h=490&s=59888&e=png&b=181818)

打开 Chat 窗口，描述我们的需求，@NotePads 就可以引用我们创建的 NotePads 内容。

![image.png](https://p9-juejin.byteimg.com/tos-cn-i-k3u1fbpfcp/b2b5248a874041038344c6b895b7faf3~tplv-k3u1fbpfcp-jj-mark:1600:0:0:0:q75.jpg#?w=888&h=1046&s=97830&e=png&b=161616)

现在 NotePads 还有一个问题是，多人合作时，如果一个成员创建了 NotePads，其它成员是看不到的。因为 NodePads 不会被 Git 管理，所以无法通过 Git 同步到其它成员的电脑上。

因为 NotePads 支持 @ 其它资源，你可以把 NotePads 内容放到可以被 Git 管理的工作区，在 NodePads 中作为 @ 资源引用。

## 最佳实践

### 1\. 内容组织

* 使用清晰的标题和分节
* 保持内容的重点
* 定期更新和维护

### 2\. 使用建议

* 避免存储临时性的笔记
* 不要包含敏感信息
* 需要纳入版本控制（如 git）的信息不要写到 NotePads 中

## 注意事项

虽然 NotePads 功能强大，但现在仍在测试阶段，在使用时需要注意：

1. 定期备份重要内容
2. 关注官方更新通知
3. 提供使用反馈以帮助改进

## 总结

NotePads 它的边界现在有点模糊，如果是一些项目开发规范，我是推荐放到项目规则文件中，按照官方的场景描述，类似项目管理模版、技术文档、代码片段等，这些内容可以放到 NotePads 中。目前的 NotePads 功能还处于测试阶段，不确定未来会不会被废弃，但是官方文档中还专门介绍了这个功能，自关注以来已经有一段时间了。所以我们可以了解一下它的用途。