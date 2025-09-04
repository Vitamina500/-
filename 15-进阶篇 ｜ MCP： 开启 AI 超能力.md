这一章我们会学习 MCP。MCP 是一个重要的工具，它可以帮助 AI 更好地理解和使用你的程序。通过 MCP，AI 可以读取文件、运行命令、使用各种工具。这些功能让 AI 能更好地帮助你写代码。

## 什么是 MCP？

MCP 的全称是"模型上下文协议"。它是一个开放的协议，它可以让程序给 AI 模型提供信息。

我们可以把 MCP 想成一个 USB-C 接口。就像 USB-C 可以连接各种设备一样，MCP 可以让 AI 连接各种数据和工具。

### MCP 的主要作用

MCP 可以帮我们用 AI 做更多事情。它提供了这些好处：

* 预建集成列表，让 LLM 可以直接使用
* 在不同 LLM 提供商和供应商之间切换的灵活性
* 在基础设施中保护数据的最佳实践

### MCP 的基本结构

MCP 用客户端和服务器的方式工作。一个程序可以连接多个服务器：

![image.png](https://p1-juejin.byteimg.com/tos-cn-i-k3u1fbpfcp/516bfe4801c740e88c9f10109d5a2353~tplv-k3u1fbpfcp-jj-mark:1600:0:0:0:q75.jpg#?w=789&h=559&s=49787&e=png&b=f8f8f8)

图参考：[MCP 架构图](https://modelcontextprotocol.io/introduction#general-architecture "https://modelcontextprotocol.io/introduction#general-architecture")

* **MCP 主机**：比如 Claude Desktop、Cursor 等程序，它们想用 MCP 来访问数据
* **MCP 客户端**：与服务器保持 1:1 连接的协议客户端
* **MCP 服务器**：通过标准化的模型上下文协议提供特定功能的轻量级程序
* **本地数据源**：MCP 服务器可以安全访问的计算机文件、数据库和服务
* **远程服务**：MCP 服务器可以连接的互联网上的外部系统（如 API）

## Cursor 中的 MCP

Cursor 里面有 MCP，所以 AI 助手可以：

1. 读写你电脑上的文件
2. 搜索网络信息
3. 运行命令
4. 使用数据库
5. 使用各种工具

这样 AI 助手就不只是看懂你的代码，还能帮你做很多事情。

## 如何在 Cursor 中设置 MCP

你可以用两种方法设置 MCP：

### 1\. 用配置文件

MCP 用 JSON 文件来设置，有两种设置：

#### 所有项目都能用的设置

* 文件位置：`~/.cursor/mcp.json`
* 用途：你想在所有项目中都用的 MCP 服务器
* 这些工具在所有 Cursor 项目中都能用

#### 单个项目的设置

* 文件位置：项目里的 `.cursor/mcp.json`
* 用途：只给这个项目用的 MCP 服务器
* 这些工具只在这个项目里能用

配置文件示例：

```json
{
  "mcpServers": {
    "server-name": {
      "command": "npx",
      "args": ["-y", "mcp-server"],
      "env": {
        "API_KEY": "your-api-key"
      }
    }
  }
}
```

配置说明：

* `command`：运行服务器的命令
* `args`：命令行参数
* `env`：环境变量，用于存储 API 密钥等敏感信息

设置好后的界面如图所示：

![image.png](https://p1-juejin.byteimg.com/tos-cn-i-k3u1fbpfcp/30685de8566d4571974af5b20cf87aff~tplv-k3u1fbpfcp-jj-mark:1600:0:0:0:q75.jpg#?w=1172&h=598&s=98171&e=png&b=1c1c1c)

### 2\. 用界面设置（不推荐）

虽然 Cursor 有界面设置，但是不建议用，因为：

1. 不能设置环境变量
2. 每个项目都要重新设置
3. 不好管理

0.47 版本的设置界面如下：

![image.png](https://p6-juejin.byteimg.com/tos-cn-i-k3u1fbpfcp/1f687f4189854ab99376c46dbc8177fd~tplv-k3u1fbpfcp-jj-mark:1600:0:0:0:q75.jpg#?w=785&h=343&s=49774&e=png&b=1a1a1a)

当点击 `Add new global MCP server` 按钮时，弹出的还是一个 JSON 文件，唯一的好处于你可以直接在这里打开这个全局 MCP 的 JSON 文件，不需要再手动从目录里查找打开。还能看到所有配置的 MCP 服务器。

![image.png](https://p9-juejin.byteimg.com/tos-cn-i-k3u1fbpfcp/658f581cd574434fa8bf1b7a77552ac8~tplv-k3u1fbpfcp-jj-mark:1600:0:0:0:q75.jpg#?w=587&h=231&s=18183&e=png&b=1a1a1a)

Cursor 团队应该用 Cursor 做一个好用的 MCP 编辑界面。

## MCP 服务器案例

MCP 有许多服务器实现，下面介绍几个简单易懂的例子：

### 案例一：Everything 服务器

Everything 服务器是一个测试服务器，它实现了 MCP 协议的所有特性，包括工具、资源、采样等功能。虽然它主要用于测试，但通过它我们可以很好地理解 MCP 的各种能力。

提供了以下功能：

* `echo`：回显输入的消息
* `add`：计算两个数字的和
* `printEnv`：打印所有环境变量
* `longRunningOperation`：演示长时间运行操作的进度通知
* `sampleLLM`：展示 LLM 采样能力
* `getTinyImage`：返回测试图片
* `annotatedMessage`：展示如何使用注释提供内容元数据

详细信息在这里：[Everything Server](https://github.com/modelcontextprotocol/server-everything "https://github.com/modelcontextprotocol/server-everything")

#### 设置方法：

```json
{
  "mcpServers": {
    "everything": {
      "command": "npx",
      "args": ["-y", "@modelcontextprotocol/server-everything"]
    }
  }
}
```

#### 使用示例：

1. **基础计算** 当你问 AI："帮我计算 123 + 456"，AI 会使用 `add` 工具进行计算。

![image.png](https://p3-juejin.byteimg.com/tos-cn-i-k3u1fbpfcp/db8d3e62b070446e85731d9334929b1a~tplv-k3u1fbpfcp-jj-mark:1600:0:0:0:q75.jpg#?w=822&h=537&s=45098&e=png&b=1a1a1a)

2. **环境检查** 当你问 AI："请帮我检查 MCP 的环境配置是否正确"或"显示当前 MCP 的所有环境变量"，AI 会使用 `printEnv` 工具列出所有环境变量，帮助你进行配置调试。

![image.png](https://p1-juejin.byteimg.com/tos-cn-i-k3u1fbpfcp/bbf2f584711a48c9874247e58f0ad759~tplv-k3u1fbpfcp-jj-mark:1600:0:0:0:q75.jpg#?w=1070&h=910&s=152829&e=png&b=141414)

### 案例二：Playwright 服务器

Playwright MCP 服务器提供了浏览器自动化能力，让 AI 能够直接操作网页、截图和执行 JavaScript。这使得 AI 助手能够帮助我们进行网页测试、数据抓取等任务。

#### 主要功能：

1. **浏览器自动化**

   * 控制真实浏览器进行网页交互
   * 支持多种浏览器（Chrome、Firefox、Safari）
   * 可执行点击、输入、滚动等操作

2. **网页截图**

   * 捕获整个页面或特定元素的截图
   * 支持多种图片格式

3. **JavaScript 执行**

   * 在页面上下文中执行 JavaScript 代码
   * 获取页面元素和数据

#### 设置方法：

```json
{
  "mcpServers": {
    "playwright": {
      "command": "npx",
      "args": ["-y", "@executeautomation/playwright-mcp-server"]
    }
  }
}
```

#### 使用示例：

以下是两个使用 Playwright MCP 的示例：

1. **数据抓取场景**

提示词：

```markdown
请帮我从 https://www.cursor.com/cn 抓取产品信息：
1. 获取产品的名称、价格和描述
2. 介绍产品特点和优势
```

![image.png](https://p9-juejin.byteimg.com/tos-cn-i-k3u1fbpfcp/471ce5abb7b04efdafa86907615ccc05~tplv-k3u1fbpfcp-jj-mark:1600:0:0:0:q75.jpg#?w=900&h=1165&s=150435&e=png&b=171717)

2. **测试页面跳转和截图**

提示词：

```markdown
请帮我测试网站 https://juejin.cn/ 的 “插件” 页面跳转功能：
1. 在顶部导航栏点击 “插件” 按钮
2.  给我一张插件页面的截图，放到当前 images 目录下，并命名为 mcp-playwright-example-plugin.png
```

![image.png](https://p3-juejin.byteimg.com/tos-cn-i-k3u1fbpfcp/da948348993c45b1bd4fc7b82afd9343~tplv-k3u1fbpfcp-jj-mark:1600:0:0:0:q75.jpg#?w=874&h=984&s=120235&e=png&b=1a1a1a)

![image.png](https://p1-juejin.byteimg.com/tos-cn-i-k3u1fbpfcp/0a061b7d00664e4fa9a95961c50bbd0a~tplv-k3u1fbpfcp-jj-mark:1600:0:0:0:q75.jpg#?w=878&h=878&s=135632&e=png&b=1a1a1a)

![image.png](https://p1-juejin.byteimg.com/tos-cn-i-k3u1fbpfcp/8ca05b9ca57d46b9b8e073cb3e5ec0e0~tplv-k3u1fbpfcp-jj-mark:1600:0:0:0:q75.jpg#?w=704&h=586&s=145641&e=png&b=f9f9f9)

这些例子展示了如何用 Playwright 服务器做自动化任务。AI 助手可以理解你的要求，用 Playwright 来完成任务。

## MCP 学习资源

Github 上有个 [servers](https://github.com/modelcontextprotocol/servers "https://github.com/modelcontextprotocol/servers") 仓库，里面有很多 MCP 服务器的代码。你可以找到喜欢的服务器来用。

访问 [MCP 官网文档](https://modelcontextprotocol.io/ "https://modelcontextprotocol.io/") 了解更多关于该协议的一些内容。

MCP 客户端有很多，Cursor 只是其中一个，另外 MCP 支持很多功能，在 Cursor 中目前只支持 Tools，支持比较好的是 Claude 的客户端。感兴趣的也可以尝试下哦。

![image.png](https://p3-juejin.byteimg.com/tos-cn-i-k3u1fbpfcp/1db888f89fd14fd4b756b3fca1d03ce2~tplv-k3u1fbpfcp-jj-mark:1600:0:0:0:q75.jpg#?w=811&h=491&s=68195&e=png&b=fefefe)

Cline 也是个好用的 MCP 客户端，它有 MCP 商店，你可以直接安装想用的服务器。也许 Cursor 以后也会有这个功能。

## 总结

MCP 是一个很有用的工具，它让 AI 能做更多事情。通过 MCP，AI 可以：

1. 读写文件
2. 运行命令
3. 使用各种工具
4. 控制浏览器
5. 获取网络数据

在 Cursor 中，我们可以用配置文件来设置 MCP。我们介绍了两个例子：Everything 服务器和 Playwright 服务器。这些例子展示了 MCP 的基本用法。

如果你想学习更多，可以看 MCP 的官方文档和 Github 上的代码。随着 AI 技术的发展，MCP 会变得越来越重要。

AI新手网，https://aixinshou.com/  全站9.9元终身免费下载！