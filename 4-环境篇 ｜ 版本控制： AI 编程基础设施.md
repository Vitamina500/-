AI新手网，https://aixinshou.com/  全站9.9元终身免费下载！

在使用 Cursor 进行 AI 辅助开发时，版本控制系统（特别是 Git）是一个不可或缺的工具。让我们深入了解为什么版本控制如此重要，以及如何在 AI 开发流程中更好地使用它。

## 为什么在 Cursor 中需要版本控制？

1. **AI 生成代码的安全网**

AI 可能生成实验性的代码，如果你对当前的代码感到满意，可以先提交到远程仓库，这样就有一个备份。

后续的代码如果出现问题，也不用担心，可以随时回退到之前的稳定版本。

2. **团队协作的基础**

多人同时使用 AI 协助开发时的代码同步，避免代码冲突和覆盖，清晰记录每个人的贡献。

3. **实验的自由度**

可以创建分支尝试不同的 AI 建议，成功的实验可以合并到主分支，失败的尝试可以安全回滚。

## Git 和 Github & Gitee 区别

Git 是版本控制系统，Github & Gitee 是基于 Git 的代码托管平台

通俗的理解，Git 就像一个代码管理员，负责记录和管理代码的每一次修改。而 Github & Gitee 就像是一个网上的代码仓库，你可以把代码存放在上面，方便多人查看和使用。

打个比方，Git 就像是一个记账本，记录每一笔收支，而 Github & Gitee 就像是银行，可以把钱存在那里，还能和别人进行交易。

[Github](https://github.com/ "https://github.com/") & [Gitee](https://gitee.com/ "https://gitee.com/") 提供了更丰富的功能，比如 Issue、Pull Request、CI/CD 等，前者是国外的，后者是国内的，大家根据自己的喜好选择。

## 安装 Git

Git 的安装方式因操作系统而异，详情可以参考 [Git 官网](https://git-scm.com/downloads "https://git-scm.com/downloads") 的安装教程，都是傻瓜式安装，一路下一步就可以了。

![image.png](https://p6-juejin.byteimg.com/tos-cn-i-k3u1fbpfcp/a56af3e366384d05be4c92da51e00f99~tplv-k3u1fbpfcp-jj-mark:1600:0:0:0:q75.jpg#?w=1396&h=594&s=198894&e=png&b=f6f6f2)

### 验证安装

安装完成后，在终端输入以下命令验证：

```bash
git --version
```

如果显示 Git 版本号，说明安装成功。

### 初始配置

安装完成后，需要进行基本配置，配置用户名和邮箱，方便后续提交代码时记录是谁提交的。

```bash
# 配置用户名和邮箱
git config --global user.name "你的名字"
git config --global user.email "你的邮箱"

# 查看配置
git config --list
```

## 远程仓库使用

### 平台选择

* Github：全球最大的代码托管平台。
* Gitee：最大的优势是不需要魔法，每个人都可以使用。
* 私有 Git 服务器：适合企业使用，例如 Gitlab

这里我使用的是 Github，我之前写的项目也都托管在 Github 上。

### SSH 密钥配置

本地和远程仓库联通时，SSH 密钥可以让你不用每次都输入用户名和密码。配置步骤如下：

1. **生成 SSH 密钥**

```bash
# 生成 SSH 密钥，将邮箱替换为你的 Github 账号邮箱
ssh-keygen -t ed25519 -C "your_email@example.com"

# 如果你使用的是不支持 Ed25519 算法的旧系统，使用：
# ssh-keygen -t rsa -b 4096 -C "your_email@example.com"
```

按照提示操作：

* 直接回车使用默认路径保存密钥
* 可以设置密码短语（passphrase），也可以直接回车跳过

2. **启动 SSH 代理**

```bash
# 启动 ssh-agent
eval "$(ssh-agent -s)"

# 添加私钥到 ssh-agent
ssh-add ~/.ssh/id_ed25519  # 如果使用 RSA，则是 ~/.ssh/id_rsa
```

3. **复制公钥**

```bash

# macOS 复制公钥到剪贴板
pbcopy < ~/.ssh/id_ed25519.pub

# Windows 复制公钥到剪贴板
clip < ~/.ssh/id_ed25519.pub
```

4. **添加到 Github**

* 登录 Github
* 点击右上角头像 -> Settings
* 左侧菜单选择 "SSH and GPG keys"
* 点击 "New SSH key"
* 填写标题（如：我的笔记本）
* 粘贴公钥内容
* 点击 "Add SSH key"

![image.png](https://p1-juejin.byteimg.com/tos-cn-i-k3u1fbpfcp/41dfb8e65bae4742b01bbe3190652901~tplv-k3u1fbpfcp-jj-mark:1600:0:0:0:q75.jpg#?w=2466&h=856&s=171027&e=png&b=ffffff)

5. **测试连接**

```bash
# 测试 SSH 连接
ssh -T git@github.com
```

如果看到 "Hi username! You've successfully authenticated" 的消息，说明配置成功。

## 创建和克隆仓库

### 1\. **在 Github 上创建**

* 登录 Github 账号
* 点击右上角 "+" -> "New repository"
* 填写仓库名称和描述
* 选择是否公开（Public）或私有（Private）
* 可以选择初始化 README 文件
* 点击 "Create repository"

![image.png](https://p3-juejin.byteimg.com/tos-cn-i-k3u1fbpfcp/9794811c3c884dd6bc7f0bbc38eb6562~tplv-k3u1fbpfcp-jj-mark:1600:0:0:0:q75.jpg#?w=2328&h=1574&s=260256&e=png&b=ffffff)

### 2\. **本地初始化并推送**

```bash
# 进入项目目录
cd your-project

# 初始化 Git 仓库
git init

# 添加远程仓库
git remote add origin git@github.com:username/repository.git
```

### 3\. **推送到远程仓库**

**代码形式推送：**

```bash
# 添加文件到暂存区
git add .

# 提交更改
git commit -m "Initial commit"

# 推送到远程仓库
git push -u origin main  # 或 master，取决于你的默认分支名
```

**Cursor 编辑器图形化界面推送：**

Cursor 提供了便捷的图形化界面来进行代码提交和推送：

1. 点击左侧源代码管理图标（类似分支的图标）打开 Git 面板
2. 在更改列表中查看修改的文件
3. 在消息框中输入提交信息（可以使用 Generate Commit Message 功能自动生成，有点像星星的那个图标）
4. 点击"提交"按钮完成提交
5. 使用同步按钮将更改推送到远程仓库

如下图所示，

![image.png](https://p1-juejin.byteimg.com/tos-cn-i-k3u1fbpfcp/f113b130e00045f4b8889dae0916facf~tplv-k3u1fbpfcp-jj-mark:1600:0:0:0:q75.jpg#?w=930&h=430&s=36087&e=png&b=1d1d1d)

> 提示：使用 Generate Commit Message 功能可以让 AI 根据你的代码更改自动生成符合规范的提交信息。

## Git 常用命令

以下是经常使用的命令，更多命令可以参考 [Git 官网](https://git-scm.com/docs "https://git-scm.com/docs")。

```bash
git add .           # 暂存更改
git commit -m ""    # 提交更改
git push            # 推送到远程
git pull            # 拉取最新代码
git branch          # 查看分支
git checkout        # 切换分支
git merge           # 合并分支
git status          # 查看状态
git log             # 查看提交历史
```

## 总结

通过合理使用版本控制，我们可以让 AI 辅助开发更加安全、高效，同时保持代码库的整洁和可维护性。这不仅能提高个人开发效率，也能促进团队协作，是现代软件开发不可或缺的技能。