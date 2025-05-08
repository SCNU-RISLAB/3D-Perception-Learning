# GitHub 命令行使用教程

## 目录
- [介绍](#介绍)
- [安装 Git](#安装-git)
- [基本配置](#基本配置)
- [创建仓库](#创建仓库)
- [提交更改](#提交更改)
- [分支管理](#分支管理)
- [远程仓库操作](#远程仓库操作)
- [版本管理](#版本管理)
- [协作功能](#协作功能)
- [常见问题解决](#常见问题解决)
- [进阶技巧](#进阶技巧)

## 介绍

GitHub 是一个基于 Git 的代码托管平台，允许开发者存储和管理他们的代码，并与他人协作。本教程将帮助您学习如何使用命令行与 GitHub 交互，即使您是计算机小白，也能轻松掌握。

### 为什么要学习 GitHub 命令行？

- **更高效**：命令行操作通常比 GUI 界面更快速
- **更强大**：命令行提供更多高级功能
- **自动化**：可以编写脚本实现自动化操作
- **职业技能**：这是软件开发领域的必备技能

## 安装 Git

在开始使用 GitHub 之前，我们需要先安装 Git。

### Windows 系统

1. 访问 [Git 官网](https://git-scm.com/download/win)
2. 下载安装包并运行
3. 安装过程中保持默认设置即可
4. 安装完成后，打开"命令提示符"或"PowerShell"，输入：
   ```
   git --version
   ```
   如果显示 Git 版本号，则安装成功

### macOS 系统

1. 打开终端
2. 如果您已安装 Homebrew，输入：
   ```
   brew install git
   ```
3. 或者，您可以下载 [Git 安装包](https://git-scm.com/download/mac)
4. 验证安装：
   ```
   git --version
   ```

### Linux 系统

对于 Ubuntu/Debian：
```
sudo apt-get update
sudo apt-get install git
```

对于 Fedora：
```
sudo dnf install git
```

验证安装：
```
git --version
```

## 基本配置

安装 Git 后，首先需要进行基本配置：

### 设置用户名和邮箱

```bash
git config --global user.name "您的用户名"
git config --global user.email "您的邮箱@example.com"
```

这些信息将与您的提交关联。

### 检查配置

```bash
git config --list
```

### 设置默认编辑器

例如，设置 VS Code 为默认编辑器：
```bash
git config --global core.editor "code --wait"
```

## 创建仓库

有两种创建仓库的方法：初始化新仓库或克隆现有仓库。

### 初始化新仓库

1. 创建一个新文件夹：
   ```bash
   mkdir my-project
   cd my-project
   ```

2. 初始化 Git 仓库：
   ```bash
   git init
   ```
   
   现在您的文件夹中会出现一个隐藏的 `.git` 目录，表示这是一个 Git 仓库。

### 克隆现有仓库

如果您想获取已有的项目副本：

```bash
git clone https://github.com/用户名/仓库名.git
```

例如，克隆一个示例仓库：
```bash
git clone https://github.com/octocat/Hello-World.git
```

这会在当前目录下创建一个名为 "Hello-World" 的文件夹，其中包含仓库内容。

## 提交更改

在 Git 中，我们通过"提交"来保存项目的快照。

### 工作流程

Git 的基本工作流程包含三个区域：
- **工作区**：您的文件夹中的文件
- **暂存区**：准备提交的更改
- **仓库**：已提交的历史记录

### 检查状态

随时检查文件状态：
```bash
git status
```

### 添加文件到暂存区

添加单个文件：
```bash
git add 文件名
```

添加所有更改：
```bash
git add .
```

### 提交更改

```bash
git commit -m "描述这次更改的信息"
```

提交信息应该简明扼要地描述您所做的更改。

### 修改最后一次提交

如果您需要修改最后一次提交：
```bash
git commit --amend
```

## 分支管理

分支允许您在不影响主项目的情况下开发功能或修复问题。

### 查看分支

```bash
git branch
```

当前分支会用星号(*)标记。

### 创建新分支

```bash
git branch 分支名称
```

### 切换分支

```bash
git checkout 分支名称
```

或者，创建并切换到新分支：
```bash
git checkout -b 新分支名称
```

### 合并分支

首先切换到目标分支（通常是 main 或 master）：
```bash
git checkout main
```

然后合并：
```bash
git merge 源分支名称
```

### 删除分支

删除已合并的分支：
```bash
git branch -d 分支名称
```

强制删除未合并的分支：
```bash
git branch -D 分支名称
```

## 远程仓库操作

远程仓库是托管在互联网上的您的项目的版本。

### 创建 GitHub 账户

1. 访问 [GitHub](https://github.com)
2. 点击 "Sign up" 并按提示操作
3. 验证您的电子邮件

### 在 GitHub 上创建仓库

1. 登录 GitHub
2. 点击右上角的 "+" 图标，选择 "New repository"
3. 填写仓库名称和描述
4. 选择是否公开仓库
5. 点击 "Create repository"

### 添加远程仓库

如果您已经在本地初始化了仓库：
```bash
git remote add origin https://github.com/用户名/仓库名.git
```

### 推送到远程仓库

首次推送并设置跟踪关系：
```bash
git push -u origin main
```

之后的推送：
```bash
git push
```

### 从远程仓库拉取更新

```bash
git pull
```

这相当于 `git fetch` 和 `git merge` 的组合。

### 查看远程仓库信息

```bash
git remote -v
```

## 版本管理

### 查看提交历史

```bash
git log
```

简洁版本：
```bash
git log --oneline
```

图形化显示：
```bash
git log --graph --oneline --all
```

### 比较差异

比较工作区与暂存区：
```bash
git diff
```

比较暂存区与最后一次提交：
```bash
git diff --staged
```

比较两个提交：
```bash
git diff 提交ID1 提交ID2
```

### 回退到之前的版本

回到特定提交：
```bash
git reset --hard 提交ID
```

注意：这将丢失所有未提交的更改！

### 撤销更改

撤销工作区的更改：
```bash
git checkout -- 文件名
```

或使用新命令（Git 2.23+）：
```bash
git restore 文件名
```

撤销暂存区的更改：
```bash
git reset HEAD 文件名
```

或使用新命令：
```bash
git restore --staged 文件名
```

## 协作功能

### 复刻(Fork)项目

在 GitHub 上，打开您想复刻的项目，点击右上角的 "Fork" 按钮。

### 创建拉取请求(Pull Request)

1. 在 GitHub 上，导航到您的复刻
2. 点击 "Pull request" 按钮
3. 选择基础分支和比较分支
4. 填写标题和描述
5. 点击 "Create pull request"

### 与上游同步

添加上游仓库：
```bash
git remote add upstream https://github.com/原作者/原仓库.git
```

获取上游更新：
```bash
git fetch upstream
```

合并到本地分支：
```bash
git merge upstream/main
```

## 常见问题解决

### 解决合并冲突

当 Git 无法自动合并更改时，会出现冲突。文件中会出现类似的标记：

```
<<<<<<< HEAD
您的更改
=======
其他人的更改
>>>>>>> 分支名
```

1. 打开冲突文件
2. 编辑文件解决冲突（删除标记，保留您想要的内容）
3. 保存文件
4. 使用 `git add` 标记为已解决
5. 完成合并 `git commit`

### 恢复已删除的文件

```bash
git checkout HEAD -- 文件名
```

### 撤销公共提交

使用 revert 创建一个新的提交来撤销之前的提交：
```bash
git revert 提交ID
```

## 进阶技巧

### 使用别名简化命令

```bash
git config --global alias.co checkout
git config --global alias.br branch
git config --global alias.ci commit
git config --global alias.st status
```

之后就可以使用简化命令，比如 `git co` 代替 `git checkout`。

### 使用 .gitignore 忽略文件

创建 `.gitignore` 文件，列出您不想跟踪的文件模式：

```
# 忽略所有 .log 文件
*.log

# 忽略 build 目录
/build/

# 忽略 config.json 文件
config.json
```

### 使用 GitHub CLI

GitHub 提供了官方命令行工具，可以从命令行直接操作 GitHub：

1. 安装 GitHub CLI：
   - Windows: `winget install --id GitHub.cli`
   - macOS: `brew install gh`
   - Linux: 见 [官方文档](https://github.com/cli/cli#installation)

2. 登录：
   ```bash
   gh auth login
   ```

3. 创建仓库：
   ```bash
   gh repo create 仓库名 --public
   ```

4. 创建拉取请求：
   ```bash
   gh pr create
   ```

### 使用 SSH 连接 GitHub

使用 SSH 可以避免每次推送时输入密码：

1. 生成 SSH 密钥：
   ```bash
   ssh-keygen -t ed25519 -C "您的邮箱@example.com"
   ```

2. 复制公钥：
   - Windows: `type C:\Users\您的用户名\.ssh\id_ed25519.pub | clip`
   - macOS: `pbcopy < ~/.ssh/id_ed25519.pub`
   - Linux: `cat ~/.ssh/id_ed25519.pub`

3. 添加到 GitHub：
   - 登录 GitHub
   - 点击右上角头像，选择 "Settings"
   - 点击左侧的 "SSH and GPG keys"
   - 点击 "New SSH key"
   - 粘贴公钥并保存

4. 测试连接：
   ```bash
   ssh -T git@github.com
   ```

## 总结

通过本教程，您已经学习了 GitHub 命令行的基本使用方法：
- 设置 Git 环境
- 创建和克隆仓库
- 提交更改
- 使用分支
- 与远程仓库交互
- 解决常见问题
- 一些进阶技巧

随着大量实践，这些命令将变得更加熟悉。记住，Git 和 GitHub 是强大的工具，掌握它们需要时间，但会极大地提高您的工作效率和协作能力。

## 附录：常用命令速查表

| 功能 | 命令 |
|------|------|
| 安装 Git | 见前文安装章节 |
| 配置用户信息 | `git config --global user.name "用户名"` <br> `git config --global user.email "邮箱"` |
| 初始化仓库 | `git init` |
| 克隆仓库 | `git clone URL` |
| 检查状态 | `git status` |
| 添加文件 | `git add 文件名` 或 `git add .` |
| 提交更改 | `git commit -m "消息"` |
| 查看历史 | `git log` |
| 创建分支 | `git branch 分支名` |
| 切换分支 | `git checkout 分支名` 或 `git switch 分支名`(新版) |
| 合并分支 | `git merge 分支名` |
| 拉取更新 | `git pull` |
| 推送更改 | `git push` |
| 解决冲突 | 手动编辑文件后使用 `git add` 和 `git commit` |

祝您在 GitHub 的旅程愉快！
