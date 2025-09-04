AI新手网，https://aixinshou.com/  全站9.9元终身免费下载！

很多人觉得 3D 建模很难学。我也不懂 3D 建模，但我用 AI 工具做出了模型。这篇文章我会告诉你怎么用 Cursor、MCP 和 Blender 做 3D 模型。我用了半天时间学会了这个方法。你按照我说的步骤做，也能很快学会。

## 什么是 Blender 和 MCP？

### Blender 是什么

Blender 是一个免费的 3D 软件。它可以做模型、渲染和动画。专业人员和爱好者都能用它。

Blender 可以在 Windows、Mac 和 Linux 上运行。想了解更多可以看 [Blender 官网](https://www.blender.org/features/ "https://www.blender.org/features/")。

### MCP 是什么

MCP 是 Model Context Protocol 的缩写。它是一个连接 AI 和其他软件的工具。我们前面已经说过了。参见上一节介绍。

### BlenderMCP 有什么用

本身 Blender 和 Cursor 是没有关联的，BlenderMCP 这个开源项目厉害的地方在于其借助 MCP 协议，把 Blender 和 AI（比如 Cursor、Claude）连接起来。

![image.png](https://p9-juejin.byteimg.com/tos-cn-i-k3u1fbpfcp/10153513a28d4c36adc6000c6b2c88f5~tplv-k3u1fbpfcp-jj-mark:1600:0:0:0:q75.jpg#?w=1259&h=816&s=164610&e=png&b=ffffff)

这样，你可以用文字在 Cursor 中告诉 AI 你想要什么样的 3D 模型，AI 就会帮你在 Blender 中创建出来。大大降低了 3D 建模的门槛。连我一个什么都不懂的小白，都能做一个简单的 3D 模型。

## 安装步骤

要用 BlenderMCP，你需要：

1. 安装 Blender（3.0 或更新版本）
2. 安装 Python（3.10 或更新版本）
3. 安装 uv 包管理器

### 安装 Blender

Blender 很容易安装。你去官网下载安装包就行。

官网下载地址 [www.blender.org/download/](https://www.blender.org/download/ "https://www.blender.org/download/")

下载推荐的安装包，然后按提示安装。很简单。

![image.png](https://p1-juejin.byteimg.com/tos-cn-i-k3u1fbpfcp/c9f7511ff53248a38000b3a62ec812ab~tplv-k3u1fbpfcp-jj-mark:1600:0:0:0:q75.jpg#?w=732&h=297&s=259701&e=png&b=112441)

### 安装 uv 包管理器

uv 包管理器用来管理 Python 包。安装说明在 [docs.astral.sh/uv/getting-…](https://docs.astral.sh/uv/getting-started/installation/%E3%80%82 "https://docs.astral.sh/uv/getting-started/installation/%E3%80%82")

**Mac 用户：**

```
brew install uv
```

**Windows 用户：**

```arduino
powershell -c "irm https://astral.sh/uv/install.ps1 | iex" 
```

然后：

```ini
set Path=C:\Users
ntra\.local\bin;%Path%
```

这一步很简单。如果你不会安装，打开 Cursor 的 Chat 窗口，问："我用的是 XX 系统，怎么安装 uv 包管理器？"如果有错误，把错误信息复制给 AI，它会帮你解决。

### 安装 Blender 插件

**1\. 下载 `addon.py` 文件**

点击图中圈出的 `addon.py` 文件，下载到你的电脑。你只需要这一个文件。

![image.png](https://p3-juejin.byteimg.com/tos-cn-i-k3u1fbpfcp/8d7b192067bb4176bf0242a6051c7e4f~tplv-k3u1fbpfcp-jj-mark:1600:0:0:0:q75.jpg#?w=1287&h=625&s=125570&e=png&b=ffffff)

**2\. 打开 Blender**

双击打开 Blender。就是下面这个图标。

![image.png](https://p9-juejin.byteimg.com/tos-cn-i-k3u1fbpfcp/3774b702c779486498d3bc77755f612a~tplv-k3u1fbpfcp-jj-mark:1600:0:0:0:q75.jpg#?w=382&h=154&s=33861&e=png&b=3b371e)

**3\. 点击"编辑 > 首选项 > 插件"**

![image.png](https://p6-juejin.byteimg.com/tos-cn-i-k3u1fbpfcp/2e131893c29e4096a371e4ee26005379~tplv-k3u1fbpfcp-jj-mark:1600:0:0:0:q75.jpg#?w=489&h=306&s=75520&e=png&b=292929)

**4\. 安装下载的 addon.py 文件**

点击 `"Install from file Disk..."` 之后会打开一个文件选择框

选择下载的 `addon.py` 文件

![image.png](https://p9-juejin.byteimg.com/tos-cn-i-k3u1fbpfcp/34b3984887c54da1b9fb2ec95fe7fa9c~tplv-k3u1fbpfcp-jj-mark:1600:0:0:0:q75.jpg#?w=655&h=310&s=44496&e=png&b=2a2a2a)

**5\. 勾选 "Blender MCP" 启用插件**

![image.png](https://p6-juejin.byteimg.com/tos-cn-i-k3u1fbpfcp/9cc10fa31114453bbdf40374ec7c5e6f~tplv-k3u1fbpfcp-jj-mark:1600:0:0:0:q75.jpg#?w=651&h=274&s=72499&e=png&b=2b2b2a)

### 启动 Blender MCP 服务器

**6\. 在 Blender 中创建新的 3D 视图**

![image.png](https://p1-juejin.byteimg.com/tos-cn-i-k3u1fbpfcp/0291d6f0bc74484f91d41cc560f9aee5~tplv-k3u1fbpfcp-jj-mark:1600:0:0:0:q75.jpg#?w=647&h=370&s=120579&e=png&b=292929)

**7\. 启动 BlenderMCP**

先点击右侧图标，打开设置窗口。这个图标很隐蔽，我找了很久才找到。

![image.png](https://p9-juejin.byteimg.com/tos-cn-i-k3u1fbpfcp/0bfe220ef6c241258675908d2698b01c~tplv-k3u1fbpfcp-jj-mark:1600:0:0:0:q75.jpg#?w=505&h=270&s=82725&e=png&b=323231)

按下图步骤点击 "Start MCP Server" 按钮，启动服务器。

![image.png](https://p3-juejin.byteimg.com/tos-cn-i-k3u1fbpfcp/650493a794994138a56b3047c4cec8e1~tplv-k3u1fbpfcp-jj-mark:1600:0:0:0:q75.jpg#?w=985&h=384&s=251725&e=png&b=353535)

启动后的效果如下，默认端口是 9876。

![image.png](https://p1-juejin.byteimg.com/tos-cn-i-k3u1fbpfcp/23f162bfce0445aab5f5568ddff95dd9~tplv-k3u1fbpfcp-jj-mark:1600:0:0:0:q75.jpg#?w=478&h=275&s=89197&e=png&b=373737)

注意，用 Cursor 时，Blender 必须一直开着。

### 在 Cursor 中设置 MCP

1. 打开 Cursor
2. 进入设置 > MCP，按下面内容配置（不会设置的看上一节 MCP 介绍）

```json
{
  "mcpServers": {
    "blender": {
      "command": "uvx",
      "args": ["blender-mcp"]
    }
  }
}
```

配置成功会有个绿色小点。

![image.png](https://p1-juejin.byteimg.com/tos-cn-i-k3u1fbpfcp/ca4d6bb0d459468a9f14fff83dd28b20~tplv-k3u1fbpfcp-jj-mark:1600:0:0:0:q75.jpg#?w=940&h=196&s=24471&e=png&b=1d1d1d)

我开始遇到下面的错误。我关了 Blender 的 MCP 服务器，关了 Cursor 项目，还是不行。

![image.png](https://p1-juejin.byteimg.com/tos-cn-i-k3u1fbpfcp/c3a0ba48e1934f9cb85c5322c14bcdae~tplv-k3u1fbpfcp-jj-mark:1600:0:0:0:q75.jpg#?w=927&h=157&s=13162&e=png&b=1d1d1d) 后来我完全关闭 Blender，重新打开并启动 MCP 服务器，再打开 Cursor 项目，就好了。

如果你有问题解决不了，可以去 [github.com/ahujasid/bl…](https://github.com/ahujasid/blender-mcp/issues "https://github.com/ahujasid/blender-mcp/issues") 看看。可能有人遇到过同样的问题。

## 案例一：创建简单场景

连接好后，你可以在 Cursor 中输入指令，让 AI 创建 3D 模型。下面是 [blender-mcp](https://github.com/ahujasid/blender-mcp "https://github.com/ahujasid/blender-mcp") 提供的例子：

![image.png](https://p3-juejin.byteimg.com/tos-cn-i-k3u1fbpfcp/974b74fbc043483a967111db4d4c2229~tplv-k3u1fbpfcp-jj-mark:1600:0:0:0:q75.jpg#?w=838&h=633&s=127326&e=png&b=ffffff)

如果你不知道怎么用，可以用官方例子。

打开 Cursor 的 Chat 窗口，输入：“通过 Hyper3D 生成一个花园小精灵的 3D 模型”，模型我直接选择的 Claude 3.7 Sonne，平常写代码用的多，感觉这个还是不错的。

你会看到 Cursor 不停调用 MCP 工具进行 3D 建模。

![image.png](https://p9-juejin.byteimg.com/tos-cn-i-k3u1fbpfcp/cf7ee2a5105445dca7f4feaf1fc5fc8c~tplv-k3u1fbpfcp-jj-mark:1600:0:0:0:q75.jpg#?w=708&h=993&s=129167&e=png&b=161616)

下面是初步建模的效果。看起来有点简单，我们继续调整。

![image.png](https://p1-juejin.byteimg.com/tos-cn-i-k3u1fbpfcp/18a4bc03412d4d0fa0244c4354ab970c~tplv-k3u1fbpfcp-jj-mark:1600:0:0:0:q75.jpg#?w=963&h=617&s=236345&e=png&b=383838)

你可以把当前模型截图给 Cursor，继续优化。

![image.png](https://p3-juejin.byteimg.com/tos-cn-i-k3u1fbpfcp/502bb41404d54f91b0258cd41f32de9f~tplv-k3u1fbpfcp-jj-mark:1600:0:0:0:q75.jpg#?w=713&h=846&s=181021&e=png&b=161616)

下面是完成的模型，比之前好看多了，细节也多了。

![image.png](https://p6-juejin.byteimg.com/tos-cn-i-k3u1fbpfcp/ae3a3be51d6243e5ac6bcdd95d72e8e0~tplv-k3u1fbpfcp-jj-mark:1600:0:0:0:q75.jpg#?w=916&h=631&s=590851&e=png&b=566949)

完成后，在 Blender 中保存。点击 "File" 菜单，选择 "Save As..." 或 "Save"。

![image.png](https://p1-juejin.byteimg.com/tos-cn-i-k3u1fbpfcp/37e99f66d8be4d7f9fc78117eda2366d~tplv-k3u1fbpfcp-jj-mark:1600:0:0:0:q75.jpg#?w=1216&h=717&s=229844&e=png&b=282828)

如果你想创建其他内容，按上面"启动 Blender MCP 服务器"的步骤，创建新项目，记得开启 MCP 服务器。

## 案例二：创建房子和小院篱笆

打开 Cursor 的 Chat 窗口，输入：“使用 Blender 进行 3D 建模：一个小房子，房子院子周围有篱笆，色彩要丰富”，按照自己想法先尝试去做，再后续一步一步的优化。

这次的元素更多，你会看到 Cursor 不停调用 MCP 工具建模。

![image.png](https://p3-juejin.byteimg.com/tos-cn-i-k3u1fbpfcp/45c0faec04b649b4914f84cafe70dbb4~tplv-k3u1fbpfcp-jj-mark:1600:0:0:0:q75.jpg#?w=808&h=1051&s=115764&e=png&b=171717)

![image.png](https://p3-juejin.byteimg.com/tos-cn-i-k3u1fbpfcp/08bbd6cbc3344d1a9e605f2f46c230bb~tplv-k3u1fbpfcp-jj-mark:1600:0:0:0:q75.jpg#?w=805&h=767&s=102788&e=png&b=171717) 下面是初步建模的效果。

![image.png](https://p9-juejin.byteimg.com/tos-cn-i-k3u1fbpfcp/38d1b137dcbc4ab5bf600466044b0171~tplv-k3u1fbpfcp-jj-mark:1600:0:0:0:q75.jpg#?w=840&h=574&s=575791&e=png&b=393939)

中间我优化了几次。有时结果不是你想要的，你可以告诉 AI 你想要的效果，重新调整。

![image.png](https://p6-juejin.byteimg.com/tos-cn-i-k3u1fbpfcp/3f8564d5ae3e4d66a167845a8a1c1d92~tplv-k3u1fbpfcp-jj-mark:1600:0:0:0:q75.jpg#?w=802&h=115&s=12610&e=png&b=191919)

![image.png](https://p3-juejin.byteimg.com/tos-cn-i-k3u1fbpfcp/4d91631141694b00a298203565e36305~tplv-k3u1fbpfcp-jj-mark:1600:0:0:0:q75.jpg#?w=873&h=270&s=74104&e=png&b=1a1a1a)

下面是最终效果，看起来不错。

![image.png](https://p9-juejin.byteimg.com/tos-cn-i-k3u1fbpfcp/a50a03c9b5a64237bef4d2af286d3817~tplv-k3u1fbpfcp-jj-mark:1600:0:0:0:q75.jpg#?w=1072&h=743&s=1004781&e=png&b=5c8b54)

![image.png](https://p1-juejin.byteimg.com/tos-cn-i-k3u1fbpfcp/1872f1ac8f854820b15d8c2a86c6650d~tplv-k3u1fbpfcp-jj-mark:1600:0:0:0:q75.jpg#?w=1043&h=691&s=1056561&e=png&b=20331c)

## 总结

BlenderMCP 和 Cursor 让 3D 建模变得简单。即使你是新手，也能用文字指令创建 3D 模型。建议把复杂的要求分成小步骤，一步一步来做。这样你能得到更好的结果。

通过本文的学习，你已经掌握了：

1. 安装和配置 Blender 与 MCP
2. 连接 Cursor 和 Blender
3. 用 AI 创建简单的 3D 模型
4. 优化和保存你的作品

方法都是一样的，同样你也可以探索一些自己喜欢的 MCP Server 来和 Cursor 结合，做一些有意思的事情。