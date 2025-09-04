Cursor 作为一款强大的 AI 编程助手，其 Pro 版本每月需要支付 20 美元。通过接入第三方模型（如 DeepSeek），我们可以用更经济的方式使用 Cursor 的部分功能。本文将介绍如何在 Cursor 中接入 DeepSeek，以及使用过程中需要注意的功能限制。

## 为什么选 DeepSeek？

DeepSeek 是一个由国内团队开发的大语言模型，具有以下优势：

1. **价格便宜，还有错峰优惠**：
   * 输入每百万字 2 元
   * 输出每百万字 8 元
   * 比 Cursor Pro 每月 20 美元便宜

参参考官方价格表 [DeepSeek 价格](https://api-docs.deepseek.com/zh-cn/quick_start/pricing "https://api-docs.deepseek.com/zh-cn/quick_start/pricing")

![image.png](https://p9-juejin.byteimg.com/tos-cn-i-k3u1fbpfcp/8c036ef92c2341788ee703c2db160930~tplv-k3u1fbpfcp-jj-mark:1600:0:0:0:q75.jpg#?w=754&h=553&s=72441&e=png&b=fcfcfc)

2. **能力强**：
   * 支持中文和英文
   * 代码能力好
   * 性能接近 Claude-3.5-Sonnet 和 GPT-4
   * 新出的 R1 模型推理更强

## 功能限制说明

用第三方 API 时，Cursor 有些功能不能用：

1. **能用的功能**：

   * Chat 对话
   * 文件内聊天
   * Tab 智能补全

2. **不能用的功能**：

   * Agent/Edit 模式
   * 其他高级功能

## 获取 DeepSeek API Key

此前 DeepSeek 爆火之后，曾一段时间暂停了 API 服务充值。当时有用过硅基流动的 API，因此下面介绍两种方式。

### 方式一：用硅基流动的 API Key

硅基流动目前支持接入 DeepSeek 的模型，并且支持通过 API 接口来使用 DeepSeek 的模型。同时还支持接入多个模型，参见[硅基流动的 API 文档](https://docs.siliconflow.cn/cn/api-reference/chat-completions/chat-completions "https://docs.siliconflow.cn/cn/api-reference/chat-completions/chat-completions") 。

![image.png](https://p6-juejin.byteimg.com/tos-cn-i-k3u1fbpfcp/42ab0014161447ccb8ffbc88fb227684~tplv-k3u1fbpfcp-jj-mark:1600:0:0:0:q75.jpg#?w=1441&h=1003&s=333134&e=png&b=ffffff) 访问：[cloud.siliconflow.cn/account/ak](https://cloud.siliconflow.cn/account/ak "https://cloud.siliconflow.cn/account/ak") 创建 API Key。

![image.png](https://p3-juejin.byteimg.com/tos-cn-i-k3u1fbpfcp/dd10b2536e634ef0b57bdd3428e97d87~tplv-k3u1fbpfcp-jj-mark:1600:0:0:0:q75.jpg#?w=1091&h=590&s=185962&e=png&b=fefcfc)

用这个 API Key 在 Cursor 中设置 DeepSeek 模型：

1. 打开 Cursor 设置
2. 选择 "Models"
3. 添加新模型：
   * 模型名称：`deepseek-ai/DeepSeek-R1` 或 `deepseek-ai/DeepSeek-V3`
   * API 地址：`https://api.siliconflow.cn/v1`
   * 粘贴你的 API Key
4. 点击验证并保存，验证前需要先把其它模型勾掉

![image.png](https://p3-juejin.byteimg.com/tos-cn-i-k3u1fbpfcp/c5dfda9b165c418ea09ab5cdb110f3db~tplv-k3u1fbpfcp-jj-mark:1600:0:0:0:q75.jpg#?w=676&h=610&s=72234&e=png&b=181818)

### 方式二：用 DeepSeek 官方 API Key

1. 访问 [DeepSeek 平台](https://platform.deepseek.com/api_keys "https://platform.deepseek.com/api_keys")
2. 注册/登录账号
3. 进入 API Keys 页面创建新的密钥
4. 复制生成的 API Key（请妥善保管，注意 API Key 只有在创建时显示一次，之后无法查看）

![image.png](https://p6-juejin.byteimg.com/tos-cn-i-k3u1fbpfcp/6096e57ecfb445a4a2c6e218d3f4e722~tplv-k3u1fbpfcp-jj-mark:1600:0:0:0:q75.jpg#?w=1001&h=802&s=64939&e=png&b=c8c8c8)

deepseek-chat 模型已升级为 DeepSeek-V3，用 `model='deepseek-chat'` 就能调用 V3 模型。

![image.png](https://p1-juejin.byteimg.com/tos-cn-i-k3u1fbpfcp/c5cba3210f2244b6838e98405903d0ed~tplv-k3u1fbpfcp-jj-mark:1600:0:0:0:q75.jpg#?w=991&h=235&s=21299&e=png&b=1a1a1a)

近期爆火的推理模型 DeepSeek-R1 通过指定 `model='deepseek-reasoner'` 即可调用 DeepSeek-R1 模型。

![image.png](https://p6-juejin.byteimg.com/tos-cn-i-k3u1fbpfcp/915de08a1943436cb3133d602b5ff903~tplv-k3u1fbpfcp-jj-mark:1600:0:0:0:q75.jpg#?w=961&h=228&s=20511&e=png&b=1a1a1a)

接口调用保持不变，仍为 [api.deepseek.com/v1。](https://api.deepseek.com/v1%E3%80%82 "https://api.deepseek.com/v1%E3%80%82") 此处的 v1 是出于同 OpenAI API 兼容考虑，和 deepseek 本身的模型没有关系。

![image.png](https://p3-juejin.byteimg.com/tos-cn-i-k3u1fbpfcp/9102dc43cb5040d0ba8f9b75bcddb0d6~tplv-k3u1fbpfcp-jj-mark:1600:0:0:0:q75.jpg#?w=956&h=232&s=22972&e=png&b=1a1a1a)

以上配置的模型名字不要写错（第一次要把其它模型关掉，只保留 `'deepseek-chat'` 或 `'deepseek-reasoner'` 才能成功）。

## 体验 DeepSeek 模型

打开 Cursor 的 Chat 对话模式，就能用 DeepSeek 模型了。

### 1\. Ask 问答模式

输入："推荐 10 本励志书单"，Cursor 会给你推荐书单。

自定义模型不支持 Agent/Edit 模式，要切换到 Ask 模式。Cursor 会提示你升级到 Pro 版。

![image.png](https://p3-juejin.byteimg.com/tos-cn-i-k3u1fbpfcp/273c96e365514b788a38a24dcb54c4fc~tplv-k3u1fbpfcp-jj-mark:1600:0:0:0:q75.jpg#?w=606&h=235&s=26241&e=png&b=191919)

切换到 Ask 模式，试试 DeepSeek R1 模型。发现 R1 模型在 Cursor 中支持不好。

![image.png](https://p9-juejin.byteimg.com/tos-cn-i-k3u1fbpfcp/ffd79356a0ba4df5b67c4a2b03aa407e~tplv-k3u1fbpfcp-jj-mark:1600:0:0:0:q75.jpg#?w=600&h=283&s=29491&e=png&b=191919)

只有 V3 模型能正常使用。

![image.png](https://p6-juejin.byteimg.com/tos-cn-i-k3u1fbpfcp/7a5afd7cd8164130943e07a5c03dfaaa~tplv-k3u1fbpfcp-jj-mark:1600:0:0:0:q75.jpg#?w=648&h=438&s=69887&e=png&b=151515)

### 2\. Ask 模式写代码

用自定义模型在 Ask 窗口写贪吃蛇游戏也可以，但不会自动创建文件，需要自己创建文件复制代码。没有文件时，Apply 按钮点击没反应。

输入："写一个贪吃蛇游戏，使用 JavaScript 技术栈"。

![image.png](https://p6-juejin.byteimg.com/tos-cn-i-k3u1fbpfcp/00c7055a38e042febcffe2e562036b44~tplv-k3u1fbpfcp-jj-mark:1600:0:0:0:q75.jpg#?w=802&h=640&s=83684&e=png&b=191919)

### 3\. 智能补全

Cursor 的智能补全功能，也是支持的。这点很棒！

![image.png](https://p1-juejin.byteimg.com/tos-cn-i-k3u1fbpfcp/35094a710aa244ee83db174adfc39897~tplv-k3u1fbpfcp-jj-mark:1600:0:0:0:q75.jpg#?w=478&h=144&s=9203&e=png&b=181818)

### 4\. 内联聊天

内联聊天功能也能用。

![image.png](https://p3-juejin.byteimg.com/tos-cn-i-k3u1fbpfcp/5c81c4a6400c4e93bd6cf9251af16028~tplv-k3u1fbpfcp-jj-mark:1600:0:0:0:q75.jpg#?w=868&h=430&s=99639&e=png&b=171717)

## 体验硅基流动的 DeepSeek 模型

我们用硅基流动的 DeepSeek R1 模型，发现能正常回应。

注意，推理过程不会显示，所以感觉有点慢！Cursor 原生支持的 R1 做了优化，推理过程会实时显示。

![image.png](https://p1-juejin.byteimg.com/tos-cn-i-k3u1fbpfcp/5342e04b4e8143e8aad1e5edcef32f3b~tplv-k3u1fbpfcp-jj-mark:1600:0:0:0:q75.jpg#?w=790&h=712&s=141011&e=png&b=151515)

其它的能力同以上演示的 DeepSeek 官方模型是一样的。

## 总结

通过本文介绍的方法，我们可以在 Cursor 中使用 DeepSeek 模型，这样能省钱又能用到 Cursor 的主要功能。虽然有些高级功能不能用，但也能满足一部分需求。习惯了 Agent 模式的朋友们可能会不太适应。

AI新手网，https://aixinshou.com/  全站9.9元终身免费下载！