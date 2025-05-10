# 📚 GitHub 命令行使用教程

## 📋 目录
- [介绍](#介绍)
- [安装 Git](#安装-git)
- [基本配置](#基本配置)
- [创建仓库](#创建仓库)
- [提交更改](#提交更改)
- [分支管理](#分支管理)
- [远程仓库操作](#远程仓库操作)
- [版本管理](#版本管理)
- [协作功能](#协作功能)
- [认证方式详解](#认证方式详解)
  - [Personal Access Token认证](#personal-access-token认证)
  - [SSH密钥认证](#ssh密钥认证)
- [实例教程：从零开始的 GitHub 操作](#实例教程从零开始的-github-操作)
- [常见问题解决](#常见问题解决)
- [进阶技巧](#进阶技巧)

## 👋 介绍

GitHub 是一个基于 Git 的代码托管平台，允许开发者存储和管理他们的代码，并与他人协作。本教程将帮助您学习如何使用命令行与 GitHub 交互，即使您是计算机小白，也能轻松掌握。

### 🤔 为什么要学习 GitHub 命令行？

- **更高效**：命令行操作通常比 GUI 界面更快速
- **更强大**：命令行提供更多高级功能
- **自动化**：可以编写脚本实现自动化操作
- **职业技能**：这是软件开发领域的必备技能

## 🔧 安装 Git

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

### 🍎 macOS 系统

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

### 🐧 Linux 系统

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

## ⚙️ 基本配置

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

## 📁 创建仓库

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

## 💾 提交更改

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

## 🌿 分支管理

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

## 🔄 远程仓库操作

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

## 📊 版本管理

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

## 👥 协作功能

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

## 🔐 认证方式详解

在使用 GitHub 时，您需要进行身份验证以访问您的仓库。GitHub 现在提供了多种认证方式，下面详细介绍两种常用的认证方法。

### 🔑 Personal Access Token认证

由于安全原因，GitHub 已于2021年8月13日开始逐步淘汰密码认证，并要求使用 Personal Access Token (PAT) 或 SSH 密钥进行认证。下面是设置和使用 PAT 的完整指南。

#### 什么是 Personal Access Token？

Personal Access Token 是一串字符，用于替代您的密码，可以设置特定的权限和有效期，比直接使用密码更安全。

#### 创建 Personal Access Token

1. **登录 GitHub**
   访问 [GitHub](https://github.com) 并登录您的账户。

2. **进入设置页面**
   点击右上角的个人头像，选择 "Settings"（设置）。

3. **开发者设置**
   在左侧边栏底部，点击 "Developer settings"（开发者设置）。

4. **Personal Access Tokens**
   在左侧边栏中，选择 "Personal access tokens"，然后点击 "Tokens (classic)"。

5. **生成新的令牌**
   点击 "Generate new token"（生成新令牌），然后选择 "Generate new token (classic)"。

6. **输入令牌名称**
   在 "Note" 字段中，输入一个描述性名称，例如 "Git 命令行访问"。

7. **设置有效期**
   从下拉菜单中选择令牌的有效期。出于安全考虑，建议选择较短的期限，如 30 天、60 天或 90 天。

8. **选择权限范围**
   根据您的需求选择权限。如果仅用于基本的 Git 操作（克隆、推送、拉取），通常只需要选择 "repo" 权限即可。

   常用权限范围：
   - **repo**: 完整的仓库访问权限
   - **read:org**: 读取组织信息
   - **user**: 用户资料访问
   - **admin:repo_hook**: 仓库钩子管理（用于 CI/CD）

9. **生成令牌**
   滚动到页面底部，点击 "Generate token"（生成令牌）按钮。

10. **保存令牌**
    生成后，您将看到一个由字母和数字组成的长字符串。**立即复制并安全保存**这个令牌，因为它只会显示一次。如果您忘记保存，需要重新生成新的令牌。

#### 使用 Personal Access Token

有多种方式可以使用您的 Personal Access Token 与 GitHub 交互：

##### 方法1：在 HTTPS URL 中使用

当您克隆仓库或设置远程仓库时，可以在 URL 中直接使用令牌：

```bash
git clone https://用户名:个人访问令牌@github.com/用户名/仓库名.git
```

例如：
```bash
git clone https://johndoe:ghp_xxxxxxxxxxxxxxxx@github.com/johndoe/my-repo.git
```

##### 方法2：配置凭证管理器（推荐）

Git 提供了凭证管理功能，可以安全地存储您的凭证：

1. **启用凭证助手**

   在 Windows 上：
   ```bash
   git config --global credential.helper wincred
   ```

   在 macOS 上：
   ```bash
   git config --global credential.helper osxkeychain
   ```

   在 Linux 上：
   ```bash
   git config --global credential.helper cache
   # 设置缓存时间（例如，缓存8小时）
   git config --global credential.helper 'cache --timeout=28800'
   ```

2. **首次使用时输入令牌**

   当您第一次推送到远程仓库时，Git 会询问您的用户名和密码。输入您的 GitHub 用户名，并在密码字段中输入您的 Personal Access Token。

   ```bash
   git push origin main
   ```

   系统会提示：
   ```
   Username: 您的GitHub用户名
   Password: 您的个人访问令牌（而不是GitHub密码）
   ```

   凭证助手会记住这些信息，下次您就不需要再次输入。

##### 方法3：使用环境变量

您也可以设置环境变量来存储您的令牌：

```bash
# Windows Command Prompt
set GITHUB_TOKEN=您的个人访问令牌

# Windows PowerShell
$env:GITHUB_TOKEN="您的个人访问令牌"

# macOS/Linux
export GITHUB_TOKEN=您的个人访问令牌
```

然后在您的 Git 操作中使用这个环境变量：

```bash
git clone https://${GITHUB_TOKEN}@github.com/用户名/仓库名.git
```

#### 更新或撤销 Personal Access Token

出于安全考虑，定期更新您的个人访问令牌是一个好习惯：

1. **撤销旧令牌**
   - 登录 GitHub，前往 Settings > Developer settings > Personal access tokens
   - 找到您想要撤销的令牌
   - 点击 "Delete"（删除）按钮

2. **生成新令牌**
   - 按照之前的步骤生成一个新的令牌
   - 更新您存储的凭证

#### 安全最佳实践

1. **设置合适的有效期**：根据您的需求设置合适的有效期，避免使用"无限期"选项。

2. **限制权限范围**：只授予令牌执行必要任务所需的最小权限。

3. **使用不同的令牌**：为不同的应用程序或用途创建单独的令牌。

4. **定期轮换**：即使令牌没有过期，也要定期更换新的令牌。

5. **安全存储**：不要在公共代码库或不安全的地方存储您的令牌。

6. **令牌泄露处理**：如果您怀疑令牌已泄露，立即在 GitHub 上撤销该令牌并生成新的令牌。

### 🔒 SSH密钥认证

SSH（Secure Shell）是一种安全的网络协议，可用于安全地连接到远程服务器。使用 SSH 密钥认证是与 GitHub 交互的另一种常用方法，比使用 HTTPS 认证更为安全和便捷。

#### SSH 认证的优势

1. **无需重复输入密码**：配置好后，您无需每次与远程仓库交互时输入用户名和密码。
2. **更高的安全性**：SSH 密钥比密码更安全，不容易被破解。
3. **可以使用密钥保护**：您可以为 SSH 密钥设置密码以增加额外的安全层。

#### 生成 SSH 密钥对

SSH 使用一对密钥：私钥（保存在您的计算机上）和公钥（上传到 GitHub）。以下是详细的步骤：

1. **检查现有 SSH 密钥**

   在生成新密钥前，先检查是否已有 SSH 密钥：
   ```bash
   ls -la ~/.ssh
   ```

   如果目录中有 `id_rsa.pub`、`id_ecdsa.pub`、`id_ed25519.pub` 等文件，则表示您已经有 SSH 密钥。

2. **生成新的 SSH 密钥**

   如果没有现有的密钥或想创建新密钥，使用以下命令：
   
   ```bash
   ssh-keygen -t ed25519 -C "您的邮箱@example.com"
   ```
   
   注：如果您使用的是不支持 Ed25519 算法的旧系统，可以使用：
   ```bash
   ssh-keygen -t rsa -b 4096 -C "您的邮箱@example.com"
   ```

3. **设置密钥存储位置**

   系统会提示您设置保存密钥的位置，默认是 `~/.ssh/id_ed25519`（或 `~/.ssh/id_rsa`）。如无特殊需求，直接按 Enter 接受默认位置。

4. **设置密码短语（可选但推荐）**

   接下来，系统会提示您输入密码短语。这是一个额外的安全层，即使有人获取了您的私钥，没有密码短语也无法使用。强烈建议设置密码短语。

   ```
   Enter passphrase (empty for no passphrase):
   Enter same passphrase again:
   ```

5. **启动 SSH 代理**

   如果您设置了密码短语，为避免每次使用 SSH 密钥时都输入密码，可以使用 SSH 代理：
   
   在 macOS/Linux 上：
   ```bash
   eval "$(ssh-agent -s)"
   ssh-add ~/.ssh/id_ed25519
   ```
   
   在 Windows 上（使用 Git Bash）：
   ```bash
   eval "$(ssh-agent -s)"
   ssh-add ~/.ssh/id_ed25519
   ```
   
   在 Windows 上（使用 PowerShell）：
   ```powershell
   # 确保 ssh-agent 服务正在运行
   Get-Service ssh-agent | Set-Service -StartupType Automatic
   Start-Service ssh-agent
   ssh-add $env:USERPROFILE\.ssh\id_ed25519
   ```

#### 将 SSH 公钥添加到 GitHub 账户

1. **复制公钥**

   使用以下命令复制 SSH 公钥到剪贴板：
   
   在 macOS 上：
   ```bash
   pbcopy < ~/.ssh/id_ed25519.pub
   ```
   
   在 Linux 上（需要安装 xclip）：
   ```bash
   xclip -sel clip < ~/.ssh/id_ed25519.pub
   ```
   
   在 Windows 上（使用 Git Bash）：
   ```bash
   cat ~/.ssh/id_ed25519.pub | clip
   ```
   
   在 Windows 上（使用 PowerShell）：
   ```powershell
   Get-Content $env:USERPROFILE\.ssh\id_ed25519.pub | Set-Clipboard
   ```
   
   或者，您也可以直接打开公钥文件，手动复制内容：
   ```bash
   cat ~/.ssh/id_ed25519.pub
   ```

2. **添加公钥到 GitHub**

   - 登录 GitHub
   - 点击右上角的个人头像，选择 "Settings"
   - 在左侧边栏中，选择 "SSH and GPG keys"
   - 点击 "New SSH key" 按钮
   - 在 "Title" 字段中，为密钥添加一个描述性名称（例如 "工作笔记本电脑"）
   - 在 "Key" 字段中，粘贴您刚才复制的公钥
   - 点击 "Add SSH key" 按钮

#### 测试 SSH 连接

添加完公钥后，测试 SSH 连接是否正常工作：

```bash
ssh -T git@github.com
```

首次连接时，您会看到一条警告消息。这是正常的，输入 "yes" 继续。如果一切正常，您将看到如下消息：

```
Hi 用户名! You've successfully authenticated, but GitHub does not provide shell access.
```

#### 使用 SSH URL 克隆和操作仓库

一旦 SSH 密钥设置完成，您就可以使用 SSH URL 而不是 HTTPS URL 来克隆和操作仓库：

1. **克隆仓库**

   ```bash
   git clone git@github.com:用户名/仓库名.git
   ```

2. **更新现有仓库的远程 URL**

   如果您已经使用 HTTPS 克隆了仓库，并想切换到 SSH，可以更新远程 URL：
   
   ```bash
   # 检查当前的远程 URL
   git remote -v
   
   # 更改远程 URL 为 SSH
   git remote set-url origin git@github.com:用户名/仓库名.git
   
   # 验证更改
   git remote -v
   ```

#### 管理多个 SSH 密钥

如果您需要为不同的 GitHub 账户或不同的服务（如 GitLab、Bitbucket）使用不同的 SSH 密钥，可以通过 SSH 配置文件管理：

1. **创建配置文件**

   创建或编辑 `~/.ssh/config` 文件：
   ```bash
   touch ~/.ssh/config
   ```

2. **添加配置内容**

   ```
   # GitHub 账户
   Host github.com
     HostName github.com
     User git
     IdentityFile ~/.ssh/id_ed25519_github
     
   # 公司 GitLab 账户
   Host gitlab.company.com
     HostName gitlab.company.com
     User git
     IdentityFile ~/.ssh/id_ed25519_gitlab
   ```

#### 安全最佳实践

1. **使用强密码短语**：为您的 SSH 密钥设置强密码短语。
2. **定期更新密钥**：定期更新您的 SSH 密钥，特别是在您怀疑可能被泄露时。
3. **限制权限**：保护您的私钥文件，确保只有您能读取它：
   ```bash
   chmod 600 ~/.ssh/id_ed25519
   ```
4. **使用不同密钥**：为不同服务使用不同的 SSH 密钥。
5. **备份密钥**：安全地备份您的私钥和密码短语。
6. **使用 SSH 代理**：使用 SSH 代理管理您的密码短语，避免重复输入。

## 🚀 实例教程：从零开始的 GitHub 操作

这个实例将帮助您快速上手 GitHub，我们将完成以下步骤：
1. 在 GitHub 上创建一个新仓库
2. 将仓库克隆到本地
3. 创建一个 Markdown 文件并添加内容
4. 提交更改并推送到 GitHub

### 步骤 1：创建 GitHub 仓库

1. 登录您的 GitHub 账号
2. 点击右上角的 "+" 图标，选择 "New repository"
3. 在 "Repository name" 字段输入 "hello-github"
4. 添加一个简短描述："My first GitHub repository"
5. 选择 "Public"（公开仓库）
6. 勾选 "Add a README file"（添加一个 README 文件）
7. 点击 "Create repository" 按钮

现在您已经在 GitHub 上创建了一个名为 "hello-github" 的仓库！

### 步骤 2：克隆仓库到本地

1. 在您的仓库页面上，点击绿色的 "Code" 按钮
2. 复制显示的 HTTPS URL（类似 `https://github.com/您的用户名/hello-github.git`）
3. 打开命令行终端（Windows 的命令提示符、PowerShell 或 macOS/Linux 的终端）
4. 导航到您想要存放项目的目录：
   ```bash
   # 例如，导航到桌面
   cd Desktop
   ```
5. 克隆仓库：
   ```bash
   git clone https://github.com/您的用户名/hello-github.git
   ```
6. 进入克隆的仓库目录：
   ```bash
   cd hello-github
   ```

### 步骤 3：创建 Markdown 文件

1. 使用文本编辑器或命令行创建一个名为 `hello-world.md` 的文件：
   
   使用命令行创建：
   ```bash
   # Windows
   echo # Hello World! > hello-world.md
   
   # macOS/Linux
   echo "# Hello World!" > hello-world.md
   ```
   
   或者使用您喜欢的文本编辑器创建文件并保存

2. 检查文件状态：
   ```bash
   git status
   ```
   
   您会看到 `hello-world.md` 被列为未跟踪的文件（untracked file）

### 步骤 4：添加文件到暂存区

1. 添加文件到暂存区：
   ```bash
   git add hello-world.md
   ```

2. 再次检查状态：
   ```bash
   git status
   ```
   
   现在您应该看到 `hello-world.md` 被标记为新文件，准备提交（changes to be committed）

### 步骤 5：提交更改

1. 提交更改：
   ```bash
   git commit -m "Add hello-world.md file"
   ```

2. 检查提交历史：
   ```bash
   git log
   ```
   
   您应该能看到您刚才的提交记录

### 步骤 6：推送到 GitHub

1. 将您的更改推送到 GitHub：
   ```bash
   git push origin main
   ```
   
   注意：在较新的 GitHub 仓库中，默认分支通常命名为 `main`，而不是 `master`。如果您的默认分支是 `master`，则使用：
   ```bash
   git push origin master
   ```

2. 输入您的 GitHub 用户名和密码（如果需要）
   
   注意：如果您已经设置了 SSH 密钥或使用了个人访问令牌，可能不需要输入密码

### 步骤 7：验证结果

1. 刷新您的 GitHub 仓库网页
2. 您应该能看到新添加的 `hello-world.md` 文件
3. 点击文件名查看其内容

### 完整操作示例

下面是完整的命令序列，从克隆到推送：

```bash
# 克隆仓库
git clone https://github.com/您的用户名/hello-github.git

# 进入仓库目录
cd hello-github

# 创建 Markdown 文件
echo "# Hello World!" > hello-world.md

# 检查状态
git status

# 添加文件到暂存区
git add hello-world.md

# 再次检查状态
git status

# 提交更改
git commit -m "Add hello-world.md file"

# 推送到 GitHub
git push origin main

# 查看提交历史
git log
```

### 常见问题

1. **推送失败**：如果您看到 "Authentication failed" 错误，请检查您的用户名和密码，或考虑设置 SSH 密钥或个人访问令牌。

2. **分支名称问题**：如果推送命令出错，确认您的默认分支名称是 `main` 还是 `master`，使用 `git branch` 命令可以查看当前分支。

3. **合并冲突**：如果您在推送前其他人对同一文件进行了更改，您可能需要先 `git pull` 更新您的本地仓库，解决冲突后再推送。

恭喜！您已经成功完成了 GitHub 的基本工作流程：创建仓库、克隆、修改、提交和推送。这是 Git 和 GitHub 使用中最常见的操作流程，掌握了这些基础，您已经能够开始使用 GitHub 进行项目管理和协作了。

## 🏫 实例教程：参与RISLAB项目贡献

这个实例将指导您如何参与SCNU-RISLAB的项目，包括发起讨论、提交代码贡献，以及与实验室成员协作。本教程适合所有希望为实验室开源项目做出贡献的成员和外部合作者。

### 准备工作

在开始之前，请确保您：
1. 已有GitHub账号
2. 已安装Git并完成基本配置
3. 了解基本的Git操作（如克隆、提交、推送等）

### 步骤1：找到并Fork实验室仓库

1. 访问[SCNU-RISLAB](https://github.com/SCNU-RISLAB)GitHub组织页面
2. 浏览并找到您感兴趣的项目仓库
3. 点击仓库右上角的"Fork"按钮，将仓库复制到您自己的GitHub账号下
   
   ![Fork仓库示意图](这里应该有图片，但当前不可用)

4. 几秒钟后，您将拥有该仓库的个人副本

### 步骤2：克隆您的Fork到本地

1. 在您的GitHub个人页面找到刚才Fork的仓库
2. 点击绿色的"Code"按钮，复制仓库URL
3. 打开终端，导航到您想存放代码的目录
4. 执行克隆命令：
   ```bash
   git clone https://github.com/您的用户名/仓库名.git
   ```
5. 进入克隆的仓库目录：
   ```bash
   cd 仓库名
   ```

### 步骤3：设置上游仓库

为了保持您的Fork与原始仓库同步，需要添加原始仓库作为远程上游仓库：

```bash
git remote add upstream https://github.com/SCNU-RISLAB/仓库名.git
```

验证远程仓库设置：
```bash
git remote -v
```

您应该能看到两个远程仓库：origin（您的Fork）和upstream（原始RISLAB仓库）。

### 步骤4：保持Fork同步

在开始工作前，建议先同步最新的代码：

```bash
# 获取上游仓库的最新代码
git fetch upstream

# 切换到主分支（通常是main或master）
git checkout main

# 合并上游仓库的更改
git merge upstream/main

# 推送更新到您的Fork
git push origin main
```

### 步骤5A：在GitHub上发起讨论

如果您有问题、建议或想法想与实验室成员讨论：

1. 在原始RISLAB仓库页面，点击"Discussions"（讨论）标签
2. 点击"New discussion"（新讨论）按钮
3. 选择合适的讨论分类：
   - 💡 Ideas（想法）：分享您的创新想法
   - 🙏 Q&A（问答）：提出技术或研究问题
   - 🧪 Experiments（实验）：分享实验结果或请求帮助
   - 📢 Announcements（公告）：了解实验室最新动态
4. 填写标题和内容，尽量详细描述您的想法或问题
5. 点击"Start discussion"（开始讨论）按钮

### 步骤5B：贡献代码

如果您想贡献代码，请遵循以下工作流程：

1. 创建新的特性分支：
   ```bash
   git checkout -b feature/您的特性名称
   ```
   
   使用描述性的分支名，如`feature/point-cloud-optimization`或`fix/slam-crash-bug`

2. 在您的分支上进行更改：
   - 编写代码
   - 添加测试（如果适用）
   - 更新文档（如果需要）

3. 提交您的更改：
   ```bash
   git add .
   git commit -m "简要描述您的更改"
   ```
   
   提交信息应简洁明了，描述您做了什么以及为什么做这些更改

4. 推送到您的Fork：
   ```bash
   git push origin feature/您的特性名称
   ```

### 步骤6：创建Pull Request

当您完成代码更改并准备贡献给原始仓库时：

1. 访问您的Fork仓库页面
2. 点击"Pull requests"（拉取请求）标签
3. 点击绿色的"New pull request"（新拉取请求）按钮
4. 确保基础分支是RISLAB仓库的main（或master），比较分支是您的特性分支
5. 点击"Create pull request"（创建拉取请求）按钮
6. 填写PR标题和描述：
   - 简要说明您的更改内容
   - 解释您解决了什么问题
   - 描述您的测试方法
   - 提及相关的issue（如果有）
7. 点击"Create pull request"按钮完成创建

### 步骤7：处理代码审查反馈

提交PR后，实验室成员会审查您的代码并可能提出修改建议：

1. 查看PR页面上的评论
2. 根据反馈修改您的代码
3. 提交新的更改：
   ```bash
   git add .
   git commit -m "根据反馈进行修改"
   git push origin feature/您的特性名称
   ```
4. 新的提交会自动添加到您的PR中

### 步骤8：Pull Request被合并

如果您的贡献被接受，实验室管理员会将您的PR合并到主分支。合并后：

1. 在您的本地仓库切换回主分支：
   ```bash
   git checkout main
   ```
2. 更新您的Fork：
   ```bash
   git pull upstream main
   git push origin main
   ```
3. 删除特性分支（可选）：
   ```bash
   git branch -d feature/您的特性名称
   ```

### 贡献最佳实践

为使您的贡献更容易被接受，请遵循以下最佳实践：

1. **遵循代码规范**：确保您的代码符合项目的编码风格和规范
2. **写好注释和文档**：为您的代码添加适当的注释和文档
3. **一次PR一个功能**：每个PR应专注于一个功能或修复
4. **积极参与讨论**：回应评论和问题，与团队保持沟通
5. **遵守项目许可证**：确保您的贡献符合项目的许可证要求

### 常见问题

1. **合并冲突**：如果出现合并冲突，您需要在本地解决这些冲突：
   ```bash
   git fetch upstream
   git merge upstream/main
   # 解决冲突
   git add .
   git commit
   git push origin feature/您的特性名称
   ```

2. **权限问题**：如果您无法直接访问某些仓库，请联系实验室管理员请求访问权限

3. **贡献被拒绝**：如果您的PR被拒绝，请仔细阅读拒绝理由，进行必要的修改后重新提交

通过参与RISLAB的项目，您不仅能够提升自己的技术能力，还能与实验室成员建立联系，共同推动3D视觉和机器人领域的研究进展。我们期待您的宝贵贡献！

## ❓ 常见问题解决

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

## 💡 进阶技巧

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

## 📝 总结

通过本教程，您已经学习了 GitHub 命令行的基本使用方法：
- 设置 Git 环境
- 创建和克隆仓库
- 提交更改
- 使用分支
- 与远程仓库交互
- 认证方式的详细设置和使用
- 解决常见问题
- 一些进阶技巧
- 完整的实例操作流程

随着您的实践，这些命令将变得更加熟悉。记住，Git 和 GitHub 是强大的工具，掌握它们需要时间，但会极大地提高您的工作效率和协作能力。

## 📋 附录：常用命令速查表

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

## 👨‍💻 讨论区：尝试贡献

这是一个供实验室成员练习Git操作的讨论区。请按照上面的教程，尝试Fork本仓库，添加您的名字，然后提交Pull Request。

格式为：`xxx到此一游 - YYYY/MM/DD`

### 贡献者名单：

1. 管理员到此一游 - 2025/05/10

---
*提示：请按照[参与RISLAB项目贡献](#-实例教程参与rislab项目贡献)章节的步骤操作，这是一个很好的实践机会！*
