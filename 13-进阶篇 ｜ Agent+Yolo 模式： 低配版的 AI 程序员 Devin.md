在前面我们介绍了 Cursor 的 Agent 模式，它像一个真实的编程助手，可以主动帮你完成各种复杂的编程任务。现在，让我们来了解一下 Cursor 在 0.44 版本中新增的 Yolo 模式。

## Yolo 模式是什么？

Yolo 模式是一个让 Agent 更加自动化的功能。之前介绍的 Agent 模式，Agent 会根据你的提示，判断是否需要执行命令，如果需要执行命令，会提示你确认。

Yolo 模式则更进一步，Agent 将无需确认就能执行命令和文件操作，朝着"全自动驾驶"又迈进了一步。开启 Yolo 模式后，Cursor 编辑器能够：

* 文件的增删改查控制权利更大
* 执行代码所需的命令
* 修复可能出现的问题
* 重复执行这些操作

而你只需要留意它正在做什么就可以了。

## 如何启用 Yolo 模式？

1. 打开 Cursor 设置
2. 进入 `Features` 部分
3. 找到并启用 `Enable auto-run mode`（以前是叫 `Enable yolo mode`）选项

第一次启动会有警告提示，毕竟这种全自动模式还需要一定时间的验证。

![image.png](https://p6-juejin.byteimg.com/tos-cn-i-k3u1fbpfcp/e729b63383614520b7674631b7c15f22~tplv-k3u1fbpfcp-jj-mark:1600:0:0:0:q75.jpg#?w=477&h=178&s=17389&e=png&b=151515) 在启动 Yolo 模式后，你可以配置以下选项：

* `Auto-run prompt`：描述哪些命令应自动执行，由模型判断。例如："仅限编译命令、git 命令和其他安全命令"
* `Command allowlist`：如果只有特定命令应自动执行，可以在此添加
* `Command denylist`：永远不应自动执行的命令
* `Delete file protection`：如果启用，将阻止 Agent 自动删除文件
* `MCP tools protection`：如果启用，将阻止 Agent 使用 MCP 工具

![image.png](https://p9-juejin.byteimg.com/tos-cn-i-k3u1fbpfcp/da77ac68f2d24b10a0ed423f12672fab~tplv-k3u1fbpfcp-jj-mark:1600:0:0:0:q75.jpg#?w=931&h=676&s=78988&e=png&b=1a1a1a) `Command denylist` 这个选项，建议配置 rm 命令，防止误删文件。

![image.png](https://p9-juejin.byteimg.com/tos-cn-i-k3u1fbpfcp/6cd15dba624b458fb8024d46e07d97b6~tplv-k3u1fbpfcp-jj-mark:1600:0:0:0:q75.jpg#?w=490&h=127&s=10631&e=png&b=181818)

但是，还是要注意，开启 Yolo 模式后，建议及时使用 git 提交代码，防止误删后找不回来。此前笔者就遇到过误删文件的情况，幸好有 git 提交的代码，否则就找不回来了。在企业级项目中，建议不要开启 Yolo 模式。

## 实战案例

让我们通过一个实际案例来体验 Cursor Agent + Yolo 模式的强大之处。假设我们要创建一个简单的 React 项目，并添加一个计数器组件。

1. 首先，打开 Chat 窗口，选择 Agent 模式（默认模式），并确保 Yolo 模式已开启
2. 告诉 Agent 我们的需求：

```markdown
请帮我创建一个新的 React 项目，包含一个计数器组件，要求：
1. 使用 Vite 创建项目
2. 创建一个 Counter 组件，包含增加和减少按钮
3. 添加一些基本的样式
4. 运行项目并确保一切正常
```

有了 Yolo 模式，Agent 会自动：

1. 运行 `npm create vite@latest my-counter-app -- --template react` 创建项目
2. 创建必要的组件文件
3. 编写组件代码和样式
4. 安装依赖
5. 启动开发服务器

![image.png](https://p3-juejin.byteimg.com/tos-cn-i-k3u1fbpfcp/10e12cba277d45bf8e4c6dcd1701f7e8~tplv-k3u1fbpfcp-jj-mark:1600:0:0:0:q75.jpg#?w=806&h=948&s=129503&e=png&b=161616)

整个过程中，你不需要手动确认任何命令，Agent 会自动处理一切。

如下所示，一个完整的项目初始化完成后，Agent 会自动启动开发服务器，并输出项目地址。

![image.png](https://p3-juejin.byteimg.com/tos-cn-i-k3u1fbpfcp/e9779b2353c0439e9c8613f4aa8bb4ae~tplv-k3u1fbpfcp-jj-mark:1600:0:0:0:q75.jpg#?w=1708&h=1018&s=276797&e=png&b=151515)

浏览器访问 `http://localhost:5173` 即可看到项目效果。

![image.png](https://p1-juejin.byteimg.com/tos-cn-i-k3u1fbpfcp/2e7521fb4a7b44b88aa3817e44e171e7~tplv-k3u1fbpfcp-jj-mark:1600:0:0:0:q75.jpg#?w=667&h=347&s=10036&e=png&b=fcfcfc)

让我们看看生成的 Counter 组件代码：

![image.png](https://p3-juejin.byteimg.com/tos-cn-i-k3u1fbpfcp/11dcf0b5272d4a99b3de3785a1f4eaa7~tplv-k3u1fbpfcp-jj-mark:1600:0:0:0:q75.jpg#?w=1393&h=871&s=219547&e=png&b=323725)

这个示例展示了 Yolo 模式如何帮助我们快速创建一个完整的 React 组件，包括样式和交互功能。

## 使用建议

虽然 Yolo 模式非常强大，但在使用时还是需要注意以下几点：

1. **谨慎使用**

   * 建议在新项目或简单的 Demo 项目中使用
   * 对于重要的生产项目，可以关闭此模式，防止误删、误改文件或者开启后，每次修改之后都要做下 Review
   * 确保设置了合适的命令白名单/黑名单

2. **监控执行过程**

   * 虽然是自动执行，但要留意 Agent 的操作
   * 如果发现不当操作，及时终止
   * 保持文件的备份

3. **渐进式采用**

   * 先在小项目中尝试
   * 熟悉了工作方式后再在更大的项目中使用
   * 根据项目需求调整配置

## 总结

Cursor 的 Yolo 模式为 Agent 带来了更高程度的自动化，特别适合快速创建原型或 Demo 项目。虽然这个功能还在发展中，但已经展现出了强大的潜力。就像有人说的，这可能就是一个 "低配版的 Devin"（一个每月收费 500 美元的 AI 程序员）。

当然，这种高度自动化的功能需要谨慎使用，在享受便利的同时也要注意潜在的风险。随着功能的不断完善和稳定，相信 Cursor Agent + Yolo 模式在未来会成为开发者工具箱中的一个重要工具。

AI新手网，https://aixinshou.com/  全站9.9元终身免费下载！