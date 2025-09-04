AI新手网，https://aixinshou.com/  全站9.9元终身免费下载！

Cursor 是一款革命性的 AI 驱动代码编辑器，它不仅继承了 VS Code 的强大功能，还集成了先进的 AI 能力。本章将指导您完成 Cursor 的账号注册、安装配置，并介绍其基本功能和使用技巧，帮助您快速上手这个强大的开发工具。

## 1\. 注册 Cursor 账号

1. 访问 Cursor 官网：[www.cursor.com/](https://www.cursor.com/ "https://www.cursor.com/")

2. 点击 "Sign in" 按钮，进行登录，可以选择从 Google 或者 Github 进行登录。

![image.png](https://p6-juejin.byteimg.com/tos-cn-i-k3u1fbpfcp/23f66eab43de4b259613a7425ba52452~tplv-k3u1fbpfcp-jj-mark:1600:0:0:0:q75.jpg#?w=1778&h=1130&s=74263&e=png&b=090909)

3. 也可以选择 "Sign up" 按钮，进行注册，邮箱可以用国内邮箱，比如 QQ 邮箱，163 邮箱，126 邮箱等。

![image.png](https://p1-juejin.byteimg.com/tos-cn-i-k3u1fbpfcp/713510ff88144cc797508359a31789ab~tplv-k3u1fbpfcp-jj-mark:1600:0:0:0:q75.jpg#?w=2010&h=1302&s=95144&e=png&b=080808)

4. 注册完成后，会自动登录到 Cursor 个人设置页面，该页面会显示您的账号信息和额度信息，因为我付费了 Cursor 的 Pro 版本，所以有 500 额度，新用户默认也有体验额度，可以免费使用 15 天。

![image.png](https://p3-juejin.byteimg.com/tos-cn-i-k3u1fbpfcp/6045384bf9c54a2c83e1921ade2b28f8~tplv-k3u1fbpfcp-jj-mark:1600:0:0:0:q75.jpg#?w=2718&h=1398&s=268074&e=png&b=060606)

## 2\. Cursor 收费计划

Cursor 提供三种不同的订阅计划，可以选择按月付费或按年付费（年付可节省 20%）：

![image.png](https://p3-juejin.byteimg.com/tos-cn-i-k3u1fbpfcp/1f53b7f062134159bc275f908e22c9b4~tplv-k3u1fbpfcp-jj-mark:1600:0:0:0:q75.jpg#?w=2640&h=1184&s=360476&e=png&b=080808)

### Hobby 版本（免费）

完全免费使用，包含以下功能：

* Pro 版本两周免费试用
* 2000 次代码补全额度
* 50 次慢速高级请求额度（之前还是 250 次的快速请求）

注意：免费计划官方可能会随时调整政策。

### Pro 版本（$20/月）

包含 Hobby 版本所有功能，另外还有：

* 无限制的代码补全
* 每月 500 次快速高级请求额度，深度使用用户这个额度可能不太够，建议省着点！
* 无限制的慢速高级请求，虽说是无限制，但是当用完 500 次后，Cladu Sonnet 3.7 模型会限制使用次数。
* 每天 10 次 o1-mini 使用额度

### Business 版本（$40/用户/月）

包含 Pro 版本所有功能，另外还有：

* 组织级别的隐私模式强制执行
* 集中式团队账单管理
* 带有使用统计的管理仪表板
* SAML/OIDC SSO 支持

注：快速高级请求是指使用 AI 进行代码补全、代码生成等功能时的请求，响应速度更快。

以上所有版本都可以访问 Cursor 的核心功能，个人开发者推荐使用 Pro 版本。如果觉得费用很高，可以先多整几个邮箱使用，或通过万能的某宝上面购买账号，这种好像是共用的，差不多每月十几块钱。

Cursor 付费目前国内的信用卡都不支持，需要 VSIA 信用卡，有一种双币信用卡，可以支持美元和人民币，可以备一张。

以上规则可能会随时变化，请以官网最新内容为准，参考 [Cursor 官网 - 定价](https://www.cursor.com/pricing "https://www.cursor.com/pricing")。

## 3\. 安装指南

### Windows/macOS 系统安装

1. 访问 Cursor 官网：[www.cursor.com/](https://www.cursor.com/ "https://www.cursor.com/")

2. 点击 "Download" 按钮下载安装包，Cursor 会根据您的操作系统自动选择合适的安装包。

![image.png](https://p3-juejin.byteimg.com/tos-cn-i-k3u1fbpfcp/61a602e190df4148adc7a067f4f1ca11~tplv-k3u1fbpfcp-jj-mark:1600:0:0:0:q75.jpg#?w=2740&h=1098&s=2172852&e=png&b=040404)

3. 运行下载的安装文件（Windows 是 .exe 文件，macOS 是 .dmg 文件）

4. 按照安装向导提示完成安装

第一次安装时，Cursor 会检测你的系统是否安装了 VS Code，如果安装了会询问是否使用 VS Code 配置，如果选择使用，会自动使用 VS Code 的配置，包括主题、字体、缩进，还有一些插件等都可以导入。

Cursor 是基于 VS Code 开源版本进行开发的，如果是从 VS Code 切换到 Cursor 可以很快的适应。

## 4\. Cursor 主界面

看几个 Cursor 主界面的主要部分：

* 顶部菜单栏: 这个是 Cursor 工具自带的菜单栏
* 左侧导航栏: 主要展示项目目录文件，可以进行文件的创建、删除、重命名、移动等操作
* 右侧导航栏: 主要展示文件的详细内容，可以进行文件的编辑、保存等操作,这个教程的实战项目中我们不太需要直接操作文件, 主要通过指令让 AI 帮我们操作
* 右侧 AI 聊天区域: 主要展示 AI 的聊天记录，可以进行 AI 的聊天、代码生成等操作(通过快捷键盘 `Cmd+i` 打开)

![image.png](https://p6-juejin.byteimg.com/tos-cn-i-k3u1fbpfcp/60762666bf1145ecbb3466a0fd967e54~tplv-k3u1fbpfcp-jj-mark:1600:0:0:0:q75.jpg#?w=1548&h=966&s=163123&e=png&b=181818)

## 5\. 基础配置

Cursor 设置界面（Settings）包含四个主要部分：

1. **General（通用设置）**：主要用于基础编辑器配置，在这里可以导入 VS Code 配置、管理账号登陆信息、快捷键设置等

2. **Features（功能特性）**：管理 Cursor 的核心功能，如代码补全和智能提示等

3. **Models（模型设置）**：负责 AI 相关的配置，包括模型选择和 API 密钥管理

4. **Rules（规则设置）**：管理项目规则文件，之前是在 Features 功能特性中，0.46 版本后单独出来了

5. **MCP（模型上下文协议）**：这个可能会让很多朋友感觉难以理解，后续会有一章节进行讲解

6. **Beta（测试功能）**：提供最新的实验性功能和测试特性

![image.png](https://p1-juejin.byteimg.com/tos-cn-i-k3u1fbpfcp/a70b2d40c8304753aa8cb8fb5d0c9868~tplv-k3u1fbpfcp-jj-mark:1600:0:0:0:q75.jpg#?w=1067&h=356&s=101589&e=png&b=1c1c1c)

以上图片中的 Account 和网页中的 Cursor 账号是联动的，所以大家如果注册了 Cursor 账号，在设置中会自动显示出来。编辑器里如果退出了，网页中的 Cursor 账号也会自动退出。

刚开始使用时，大家可以先使用默认配置，在后续课程会根据实际的场景，分别介绍不同的配置。

## 6\. 安装历史版本

Cursor 版本更新还是比较频繁的，此前 Cursor 会自动升级到最新版本，但有时新版本不太稳定，会遇到一些问题，也有的用户更习惯使用旧版本的体验， Cursor 也提供了安装历史版本的功能。

Cursor 官方只支持 0.45 及之后的版本，并且每个版本默认最后一个 hotfix 版本.

![image.png](https://p3-juejin.byteimg.com/tos-cn-i-k3u1fbpfcp/61d90309c1f54275bdeeb4ac47e3022e~tplv-k3u1fbpfcp-jj-mark:1600:0:0:0:q75.jpg#?w=1447&h=1037&s=99602&e=png&b=090909)

Github 上有个开源的仓库，维护了 0.36.2 版本之后所有 Cursor 的历史版本，还支持每个版本对应的所有 hotfix 版本，地址：[github.com/oslook/curs…](https://github.com/oslook/cursor-ai-downloads "https://github.com/oslook/cursor-ai-downloads")

![image.png](https://p6-juejin.byteimg.com/tos-cn-i-k3u1fbpfcp/b1026c3d488747fca4f580f883787927~tplv-k3u1fbpfcp-jj-mark:1600:0:0:0:q75.jpg#?w=684&h=518&s=87832&e=png&b=ffffff)

## 7\. 隐私问题

大家在使用 AI 工具时可能关心隐私方面的问题，Cursor 会不会收集我的代码？会不会有代码泄露的风险？

参考 [Cursor 隐私政策](https://www.cursor.com/privacy "https://www.cursor.com/privacy")，是提供了隐私模式（Privacy Mode）来保护用户数据，默认是禁用状态，需要手动开启。

![image.png](https://p9-juejin.byteimg.com/tos-cn-i-k3u1fbpfcp/56bc153720674ea8a72b413c318272ab~tplv-k3u1fbpfcp-jj-mark:1600:0:0:0:q75.jpg#?w=1333&h=612&s=81057&e=png&b=1a1a1a)

1. **开启隐私模式的效果**

   * 零数据保留：所有代码都不会被存储
   * 不会用于训练：您的代码不会被 Cursor 或任何第三方用于训练
   * 临时缓存：文件内容仅在请求期间临时缓存，且使用客户端生成的唯一密钥加密

2. **关闭隐私模式时的数据收集**

   * 收集遥测和使用数据
   * 可能包含提示词、编辑器操作、代码片段等
   * 用于评估和改进 AI 功能
   * 自动补全时，推理提供商可能收集提示词以提高推理速度

3. **其他重要说明**

   * 即使使用自己的 API Key，请求仍会通过 Cursor 后端进行最终的提示词构建
   * 代码库索引时，代码会以小块形式上传到服务器计算嵌入，但纯文本代码在请求结束后不会保留（有关代码库的索引，后续会详细介绍）
   * 仅保存代码库的元数据（如哈希值、文件名）

建议：如果您处理敏感代码或有严格的数据隐私要求，建议开启隐私模式。

## 6\. 总结

本章介绍了 Cursor 的安装、注册、配置和隐私设置，帮助大家快速上手 Cursor 并开始使用。在后续章节中，我们将深入探讨 Cursor 的各种功能和使用技巧，助您在 AI 驱动的开发旅程中游刃有余。