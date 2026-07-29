# Git 快速入门

示例仓库：[my-first-repo](https://github.com/Anonymous-1028/my-first-repo)

最简单的 Git 操作流程：

```text
下载仓库 → 修改文件 → 添加修改 → 提交修改 → 推送到 GitHub
```

## 0.使用前提

==注意：需要执行后面流程，确保你现在已经把git安装到你自己的电脑后才可以执行。==

## 1. 下载仓库

第一次使用时，把 GitHub 仓库下载到电脑：

```powershell
git clone https://github.com/Anonymous-1028/my-first-repo.git
```

一个仓库只需要下载一次。

`git clone` 在你准备存放仓库的目录中执行。下载完成后，进入仓库再执行后续命令。



示例:下载 `my-first-repo.git` 仓库

#### 1.1 进入cmd或者PowerShell

![image-20260721110722673](assets/image-20260721110722673.png)



#### 1.2 选择拉取仓库的位置

这一步的意思就是给你要文件找个地方，本教材为了简单明了，就选择在桌面

```powershell
cd C:\Users\19222\Desktop
```

![image-20260721111946536](assets/image-20260721111946536.png)

#### 1.3 拉取GitHub上的代码库



## 2. 进入仓库

```powershell
cd my-first-repo
```

进入后，后面的 `git add`、`git commit` 和 `git push` 都在 `my-first-repo` 仓库根目录中执行。

仓库局部结构如下：

```text
my-first-repo/                 ← 在这里执行 Git 命令
└─ git学习/
   ├─ git快速入门.md
   ├─ Git学习笔记.md
   └─ 测试文件.txt             ← 在这里修改练习内容
```

## 3. 修改文件

打开 `git学习` 文件夹中的 `测试文件.txt`，修改内容并保存。（打开拉去下来的仓库，找到对应文件修改）

以后练习 Git 时，只修改这个测试文件，不需要修改其他文件。

## 4. 添加修改

```powershell
git add "git学习/测试文件.txt"
```

这条命令表示：准备把 `测试文件.txt` 的修改放入本次提交。命令仍然是在 `my-first-repo` 根目录中执行。

如果修改了多个文件，也可以一次添加全部修改：

```powershell
git add .
```

## 5. 提交修改

```powershell
git commit -m "修改学习文件"
```

这条命令把刚才添加的修改保存为一个本地版本。引号中的文字用于说明这次修改了什么。

## 6. 推送到 GitHub

```powershell
git push origin main
```

这条命令把本地提交上传到 GitHub。推送成功后，刷新仓库网页就能看到修改。

## 完整命令

第一次下载并进入仓库：

```powershell
git clone https://github.com/Anonymous-1028/my-first-repo.git
cd my-first-repo
```

修改并保存文件后执行：

```powershell
git add "git学习/测试文件.txt"
git commit -m "修改测试文件"
git push origin main
```
