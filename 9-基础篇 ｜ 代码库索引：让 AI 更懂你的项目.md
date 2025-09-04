AI新手网，https://aixinshou.com/  全站9.9元终身免费下载！

代码库索引是 Cursor 最强大的功能之一。它通过为代码文件创建嵌入向量（Embeddings），帮助 AI 全面理解你的项目。这个功能让 AI 能够"看见"整个代码库，而不仅仅是当前打开的文件。本章将详细介绍如何使用这一功能，提升你的开发效率。

## 什么是代码库索引？

代码库索引是 Cursor 的核心功能。它会：

* 为代码文件创建嵌入向量
* 把索引数据存储在云端
* 保持代码本身只在本地存储
* 确保项目安全性

## 为什么需要代码库索引？

在传统开发中，开发者需要记住整个项目结构。使用代码库索引后：

* ✅ AI 回答更准确，因为它能基于当前项目的索引库回答问题
* ✅ 文件搜索更快
* ✅ AI 能更好地理解跨文件的关系
* ✅ 重构建议更精准

## 使用效果对比

### 版本变化

在 Cursor 0.45 版本及之前，Chat 窗口有两个提交按钮：

* submit 按钮：不使用代码库索引
* codebase 提交按钮：使用代码库索引

![image.png](https://p3-juejin.byteimg.com/tos-cn-i-k3u1fbpfcp/4adb2701d39247d9bd6112020653fcfc~tplv-k3u1fbpfcp-jj-mark:1600:0:0:0:q75.jpg#?w=772&h=239&s=22210&e=png&b=1c1c1c)

从 0.46 版本开始，Cursor 只保留了一个"send"按钮。Ask 模式下默认情况下不会使用代码库索引，只有按下 Ctrl/Command + Enter 时才会使用。这个变化让功能变得更隐蔽了。

![image.png](https://p1-juejin.byteimg.com/tos-cn-i-k3u1fbpfcp/7df1a8ac802e45498fbcdbcd6a59c1b6~tplv-k3u1fbpfcp-jj-mark:1600:0:0:0:q75.jpg#?w=1400&h=294&s=36016&e=png&b=2f2f2f)

### 实际效果对比

我在本地有一个`sort.js`文件，我问 Cursor："解释下目前已实现的排序算法"

不使用代码库索引的回答：

![image.png](https://p1-juejin.byteimg.com/tos-cn-i-k3u1fbpfcp/b4f749086f0a4334b01e4c79502b1d44~tplv-k3u1fbpfcp-jj-mark:1600:0:0:0:q75.jpg#?w=2426&h=1658&s=680580&e=png&b=1e1e1e)

使用代码库索引的回答：

![image.png](https://p3-juejin.byteimg.com/tos-cn-i-k3u1fbpfcp/c202f08f4bcc44c4970798068dbd1c66~tplv-k3u1fbpfcp-jj-mark:1600:0:0:0:q75.jpg#?w=2454&h=1686&s=478742&e=png&b=202020)

对比可以看出：

* 使用代码库索引时，AI 先搜索了项目中的文件，然后根据文件内容回答
* AI 准确指出`sort.js`文件中实现了冒泡排序和选择排序
* 不使用代码库索引时，AI 只能从一般角度回答常见排序算法，没有针对项目的具体情况

## 如何配置代码库索引

### 基本设置

Cursor 默认会自动索引新打开的文件夹。设置步骤：

1. 打开`Cursor Settings`
2. 进入`Features` > `Codebase Indexing`
3. 查看同步状态指示条（显示索引进度）
4. 可用操作：
   * 【Resync Index】重新同步索引
   * 【Delete Index】删除现有索引
   * 【Hide Settings/Show Settings】隐藏/显示详细设置

![image.png](https://p6-juejin.byteimg.com/tos-cn-i-k3u1fbpfcp/5239541ad02e4b198eaac1e2aceac853~tplv-k3u1fbpfcp-jj-mark:1600:0:0:0:q75.jpg#?w=1958&h=1148&s=211434&e=png&b=202020)

### 重要配置选项

#### 1\. 自动索引新文件夹

`Index new folders by default`选项默认开启。开启后，Cursor 会自动索引新打开的文件夹。

注意：超过 10,000 个文件的文件夹不会自动索引。

下图显示了正在索引的项目，可以看到索引进度条：

![image.png](https://p1-juejin.byteimg.com/tos-cn-i-k3u1fbpfcp/757383739132480bbd049f51e70b5ec3~tplv-k3u1fbpfcp-jj-mark:1600:0:0:0:q75.jpg#?w=988&h=642&s=84085&e=png&b=202020)

#### 2\. 忽略文件设置

`Ignore files`选项用于配置索引时要忽略的文件。这些规则会补充`.gitignore`中的规则。

你可以：

* 点击`Configure ignored files`按钮设置规则
* 创建`.cursorignore`文件配置规则

![image.png](https://p3-juejin.byteimg.com/tos-cn-i-k3u1fbpfcp/7979ab3753c24ffda021132bb9357501~tplv-k3u1fbpfcp-jj-mark:1600:0:0:0:q75.jpg#?w=1450&h=278&s=61772&e=png&b=1d1d1d)

点击`See all included files`按钮可以查看所有被索引的文件：

![image.png](https://p1-juejin.byteimg.com/tos-cn-i-k3u1fbpfcp/5a5cf97d5054475caf8a5a22bbcaa5bc~tplv-k3u1fbpfcp-jj-mark:1600:0:0:0:q75.jpg#?w=1202&h=516&s=59508&e=png&b=1f1f1f)

#### 3\. Git 关系图

`Git graph file relationships`选项默认开启。开启后，Cursor 会索引 git 历史记录，帮助 AI 理解文件间的关系。

## 实际应用：快速理解项目

以一个图片压缩项目为例：`https://github.com/qufei1993/compressor`

如果你是初学者，想快速了解这个项目，可以：

1. 打开项目
2. 在 Chat 窗口中切换到 Ask 模式，使用代码库索引功能，输入问题

例如，输入：

```text
介绍下这个项目的作用和使用的技术栈
```

以下的输出结果显示了 AI 的代码库搜索和思考过程，回答结果还是很准确的。

![image.png](https://p1-juejin.byteimg.com/tos-cn-i-k3u1fbpfcp/ab4b7896c96b47b7896eb757e6526c2a~tplv-k3u1fbpfcp-jj-mark:1600:0:0:0:q75.jpg#?w=1504&h=1226&s=320307&e=png&b=1c1c1c)

![image.png](https://p3-juejin.byteimg.com/tos-cn-i-k3u1fbpfcp/dd94f48e110d44d384ab643b785b8105~tplv-k3u1fbpfcp-jj-mark:1600:0:0:0:q75.jpg#?w=1500&h=1058&s=156967&e=png&b=1c1c1c)

## 最佳实践

为了更好地使用代码库索引功能：

1. 定期检查索引状态（通过进度条）
2. 合理设置忽略规则，避免索引无关文件
3. 大型项目考虑模块化索引
4. 团队统一`.cursorignore`配置
5. 使用代码库索引功能快速理解项目

## 常见问题解决

### 索引不同步或失败问题

* 点击`Delete Index`删除索引，然后重新打开项目
* 或者点击`Resync Index`重新同步

![image.png](https://p1-juejin.byteimg.com/tos-cn-i-k3u1fbpfcp/fb9cd0c300d44ea48d36be32ebe2a476~tplv-k3u1fbpfcp-jj-mark:1600:0:0:0:q75.jpg#?w=1144&h=476&s=51282&e=png&b=1f1f1f)

如下图所示，索引被删除时，需要点击"Compute Index"重新计算：

![image.png](https://p3-juejin.byteimg.com/tos-cn-i-k3u1fbpfcp/d852902ce25841179a0251ed76f0164d~tplv-k3u1fbpfcp-jj-mark:1600:0:0:0:q75.jpg#?w=1788&h=569&s=126233&e=png&b=191919)

### 索引进度条卡住

如果索引进度条卡住（一直显示 Pause Indexing）：

![image.png](https://p9-juejin.byteimg.com/tos-cn-i-k3u1fbpfcp/0ed68b0bdc06457195f07d7a2dc4a444~tplv-k3u1fbpfcp-jj-mark:1600:0:0:0:q75.jpg#?w=1168&h=346&s=45630&e=png&b=202020)

如果出现这种情况，要确定下网络是否正常，之前层遇到过网络连接问题导致索引卡住。或 者尝试删除索引，重新计算。

### 代码安全问题

关于代码安全，Cursor 的[隐私政策](https://www.cursor.com/privacy "https://www.cursor.com/privacy")说明：

* 代码会分成小块上传到服务器计算嵌入向量
* 所有明文代码在请求完成后立即删除
* 只有嵌入向量和元数据（如哈希值、文件名）会存储在数据库中
* 源代码本身不会被保存

## 总结

代码库索引是 Cursor 中提升 AI 理解能力的关键功能。通过正确配置和使用这一功能，你可以：

* 让 AI 更准确地回答项目相关问题
* 加快文件搜索速度
* 提升 AI 对项目整体结构的理解
* 获得更精准的代码建议和重构方案

合理使用代码库索引功能，将大大提高你的开发效率，让 AI 成为你更得力的编程助手。