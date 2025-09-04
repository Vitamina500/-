AI新手网，https://aixinshou.com/  全站9.9元终身免费下载！

Node.js 是一个跨平台的 JavaScript 运行时环境，它让我们能够在浏览器之外运行 JavaScript 代码。在本教程中，我们将使用 Node.js 作为开发环境，因此需要先安装配置好 Node.js。

## 傻瓜式安装

对于初学者，最简单的是直接从官网下载安装包进行安装。

1. 访问 Node.js 官网：[nodejs.org/en/download](https://nodejs.org/en/download "https://nodejs.org/en/download")

2. 下载安装包：

   * Windows 系统：选择 `.msi` 安装包
   * macOS 系统：选择 `.pkg` 安装包
   * Linux 系统：选择 `.tar.gz` 二进制包

![image.png](https://p9-juejin.byteimg.com/tos-cn-i-k3u1fbpfcp/0c78998eae974fb3bb07e103321a4d91~tplv-k3u1fbpfcp-jj-mark:1600:0:0:0:q75.jpg#?w=819&h=324&s=56772&e=png&b=ffffff)

3. 选择版本：

   * LTS (Long Term Support)：长期支持版，生产环境一般都使用这个，大家直接选择这个就可以了。
   * Current：最新版本，包含最新特性，简答理解为体验、测试、不稳定的版本。

4. 运行安装程序：

   * Windows：双击 `.msi` 文件，按照安装向导完成安装
   * macOS：双击 `.pkg` 文件，按照安装向导完成安装
   * Linux：解压 `.tar.gz` 文件，配置环境变量

5. 验证安装：

打开终端，输入以下命令：

```bash
# 检查 Node.js 版本
node -v

# 检查 npm 版本
npm -v
```

推荐使用 Cursor 编辑器自带终端

![image.png](https://p3-juejin.byteimg.com/tos-cn-i-k3u1fbpfcp/4536a25a855f4ca7a065cd0f55ecdac5~tplv-k3u1fbpfcp-jj-mark:1600:0:0:0:q75.jpg#?w=1030&h=576&s=75542&e=png&b=161616)

如果能看到版本号，说明安装成功。

注意事项：

* 安装过程中建议使用默认配置
* Windows 用户安装完成后可能需要重启电脑
* 安装包会自动配置环境变量，无需手动配置
* npm 包管理器会随 Node.js 一起安装

---

## 版本管理安装步骤

### 为什么选择版本管理工具安装 Node.js？

虽然可以直接从 Node.js 官网下载安装包进行安装，但作为专业的开发者，更推荐使用版本管理工具来安装和管理 Node.js。原因如下：

1. **多版本管理**：不同项目可能需要不同的 Node.js 版本，版本管理工具让你能够轻松切换
2. **更新方便**：可以轻松升级或降级 Node.js 版本
3. **团队协作**：确保团队成员使用相同的 Node.js 版本

### macOS/Linux 系统

1. 安装 nvm：

```bash
# 使用 curl 安装
curl -o- https://raw.githubusercontent.com/nvm-sh/nvm/v0.40.1/install.sh | bash

# 或使用 wget 安装
wget -qO- https://raw.githubusercontent.com/nvm-sh/nvm/v0.39.0/install.sh | bash
```

2. 配置环境变量：

```bash
# 将以下内容添加到 ~/.bash_profile, ~/.zshrc, ~/.profile, 或 ~/.bashrc
# 一个简单的方式是通过命令 echo $0 来判断当前终端类型
# 例如，我这里在终端执行命令 echo $0，输出结果为 /bin/zsh，那我就需要将以下内容写入文件 ~/.zshrc

export NVM_DIR="$([ -z "${XDG_CONFIG_HOME-}" ] && printf %s "${HOME}/.nvm" || printf %s "${XDG_CONFIG_HOME}/nvm")"
[ -s "$NVM_DIR/nvm.sh" ] && \. "$NVM_DIR/nvm.sh"

# 通过命令将内容追加到文件，例如
echo 'export NVM_DIR="$([ -z "${XDG_CONFIG_HOME-}" ] && printf %s "${HOME}/.nvm" || printf %s "${XDG_CONFIG_HOME}/nvm")"
[ -s "$NVM_DIR/nvm.sh" ] && \. "$NVM_DIR/nvm.sh"' >> ~/.zshrc
```

执行命令 `nvm -v` 查看 nvm 版本，如果显示版本号，说明安装成功。

![image.png](https://p9-juejin.byteimg.com/tos-cn-i-k3u1fbpfcp/8a6030107d254344ad5952d74eb7745f~tplv-k3u1fbpfcp-jj-mark:1600:0:0:0:q75.jpg#?w=533&h=171&s=10698&e=png&b=000000)

3. 安装 Node.js：

```bash
# 查看可用的 Node.js 版本
nvm ls-remote

# 安装最新的长期支持版本(LTS)
nvm install --lts

# 使用已安装的版本
nvm use --lts
```

## 验证安装

安装完成后，打开终端输入以下命令验证：

```bash
# 检查 Node.js 版本
node -v

# 检查 npm 版本(Node.js 的包管理器)
npm -v
```

如果能看到版本号，说明安装成功。

![image.png](https://p9-juejin.byteimg.com/tos-cn-i-k3u1fbpfcp/dd6647dc3fcf455db75b4394ad75e0a1~tplv-k3u1fbpfcp-jj-mark:1600:0:0:0:q75.jpg#?w=472&h=179&s=15407&e=png&b=010101)

注意 npm 不需要手动安装，Node.js 自带的。

### Windows 系统

Windows 系统下我们使用 fnm (Fast Node Manager) 作为 Node.js 版本管理工具。fnm 是一个跨平台的 Node.js 版本管理器，使用 Rust 编写，具有快速、轻量的特点。

1. 安装 fnm：

有多种方式可以安装 fnm，推荐使用 winget：

```bash
# 使用 winget 安装 fnm
winget install Schniz.fnm

# 安装指定版本的 Node.js
fnm install 22

# 使用已安装的版本
fnm use 22

# 验证 Node.js 版本
node -v  # 应显示 "v22.14.0"

# 验证 npm 版本
npm -v   # 应显示 "10.9.2"
```

## 常用 nvm 命令

```bash
nvm list                # 列出已安装的版本
nvm current             # 显示当前使用的版本
nvm install <version>   # 安装指定版本
nvm use <version>      # 切换到指定版本
nvm alias default <version>  # 设置默认版本
```

## npm 镜像配置

在国内使用 npm 可能会比较慢，建议配置国内镜像：

```bash
# 使用淘宝镜像
npm config set registry https://registry.npmmirror.com

# 查看当前镜像
npm config get registry
```

## 牛刀小试

使用 Command + i 快捷键打开 Cursor Chat 窗口，输入

```js
写一个 JS 文件输出 “你好，欢迎来到 Cursor 课程学习
```

自动生成代码，并运行代码，是不是很神奇？这些内容在后续的课程中会详细介绍。

![image.png](https://p6-juejin.byteimg.com/tos-cn-i-k3u1fbpfcp/90bfa2d500684c399e39eee1982e64f9~tplv-k3u1fbpfcp-jj-mark:1600:0:0:0:q75.jpg#?w=770&h=865&s=160763&e=png&b=161616)

## 总结

通过版本管理工具安装 Node.js 不仅专业，而且能让我们在后续的开发中更加灵活地管理不同版本。在本教程后续的实践中，我们会使用 AI 来生成 JavaScript 代码，有了 Node.js 环境，我们就能直接运行和测试这些代码了。

记住，虽然我们会依赖 AI 来生成代码，但良好的开发环境配置仍然是必不可少的基础设施。