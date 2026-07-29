# Git 简单学习资料

这份文档用于记录 Git 的基础概念、常用命令和练习流程。

## 简单操作流程

### 1. 拉取远程仓库

```powershell
git clone https://github.com/Anonymous-1028/my-first-repo.git
```

### 2. 进入仓库目录

```powershell
cd my-first-repo
```

Git 命令要在仓库目录中执行。如果没有进入仓库目录，运行 `git status` 会提示 `not a git repository`。

### 3. 查看当前状态

```powershell
git status
```

刚克隆完成时，通常会看到：

```text
On branch main
Your branch is up to date with 'origin/main'.

nothing to commit, working tree clean
```

### 4. 修改文件

打开 `git学习/测试文件.txt`，增加或修改一些文字，然后保存文件。

### 5. 再次查看状态

```powershell
git status
```

这时会看到 `测试文件.txt` 已被修改，但还没有放入暂存区：

```text
Changes not staged for commit:
        modified:   git学习/测试文件.txt
```

### 6. 将修改放入暂存区

```powershell
git add "git学习/测试文件.txt"
```

再次查看状态：

```powershell
git status
```

此时修改会显示在 `Changes to be committed` 下，表示已经可以提交。

### 7. 提交修改

```powershell
git commit -m "练习修改文本文件"
```

这一步会把暂存区中的修改保存到本地 Git 仓库。

### 8. 查看提交记录

```powershell
git log --oneline --graph --decorate
```

最新提交会显示在最上方，`HEAD -> main` 表示当前位于 `main` 分支的最新提交。

### 9. 推送到远程仓库

```powershell
git push origin main
```

推送成功后，本地提交就会出现在 GitHub 仓库中。

### 10. 最后检查状态

```powershell
git status
```

如果本地和远程已经同步，并且没有其他修改，会看到：

```text
Your branch is up to date with 'origin/main'.
nothing to commit, working tree clean
```

完整顺序：

```text
clone → cd → status → 修改文件 → status → add → status → commit → log → push → status
```

## 1. Git 是什么

Git 是一个版本控制工具，可以记录文件的修改历史，并帮助多人协作开发。

一个常见的 Git 工作流程是：

```text
工作区 --git add--> 暂存区 --git commit--> 本地仓库 --git push--> 远程仓库
```

## 2. 获取远程仓库

```powershell
git clone <仓库地址>
cd <仓库目录>
```

示例：

```powershell
git clone https://github.com/Anonymous-1028/my-first-repo.git
cd my-first-repo
```

`git status` 必须在 Git 仓库目录或其子目录中执行，否则会出现 `not a git repository`。

## 3. 查看仓库状态

```powershell
git status
```

常见状态：

- `working tree clean`：没有未提交的修改。
- `Changes not staged for commit`：文件已修改，但还没有暂存。
- `Changes to be committed`：修改已暂存，可以提交。

查看具体修改：

```powershell
git diff
```

查看已经暂存的修改：

```powershell
git diff --staged
```

## 4. 暂存和提交修改

暂存指定文件：

```powershell
git add "git学习/测试文件.txt"
```

暂存当前目录中的全部修改：

```powershell
git add .
```

创建本地提交：

```powershell
git commit -m "练习修改文本文件"
```

提交说明应该简短、明确地描述本次修改。

## 5. 查看提交历史

```powershell
git log --oneline --graph --decorate
```

- `HEAD`：当前所在位置。
- `main`：当前本地分支。
- `origin/main`：上次获取到的远程 `main` 分支状态。
- 每条记录开头的短字符串（如 `a2b6163`）是提交 ID。

## 6. 与远程仓库同步

推送本地提交：

```powershell
git push origin main
```

获取并合并远程更新：

```powershell
git pull origin main
```

第一次推送新分支时，可以建立跟踪关系：

```powershell
git push -u origin <分支名>
```

建立关系后，该分支通常只需执行 `git push` 或 `git pull`。

## 7. 分支基础操作

查看本地分支：

```powershell
git branch
```

创建并切换到新分支：

```powershell
git switch -c practice/git-branch
```

切换回主分支：

```powershell
git switch main
```

把练习分支合并到当前分支：

```powershell
git merge practice/git-branch
```

合并前要先切换到接收修改的分支，例如 `main`。

## 8. 常用撤销操作

丢弃某个文件尚未暂存的修改：

```powershell
git restore <文件名>
```

取消暂存，但保留工作区中的修改：

```powershell
git restore --staged <文件名>
```

修改最近一次提交说明：

```powershell
git commit --amend -m "新的提交说明"
```

注意：`restore` 和 `commit --amend` 可能改变已有内容。执行前先运行 `git status`，确认操作对象。

## 9. 每次提交的推荐步骤

```powershell
git status
git diff
git add <文件名>
git diff --staged
git commit -m "清晰的提交说明"
git push
```

## 10. 常用命令速查

| 命令 | 作用 |
| --- | --- |
| `git clone <地址>` | 下载远程仓库 |
| `git status` | 查看当前状态 |
| `git diff` | 查看未暂存的修改 |
| `git add <文件>` | 暂存文件 |
| `git commit -m "说明"` | 创建本地提交 |
| `git log --oneline` | 简洁地查看提交历史 |
| `git pull` | 获取并合并远程更新 |
| `git push` | 推送本地提交 |
| `git branch` | 查看分支 |
| `git switch <分支>` | 切换分支 |

## 11. 安全提示

- 操作前后多使用 `git status`。
- 不确定修改内容时，先使用 `git diff`。
- 初学阶段谨慎使用 `git reset --hard` 和 `git push --force`，它们可能造成内容或历史丢失。
- 提交前不要把密码、访问令牌或其他隐私信息加入仓库。
