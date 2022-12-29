- [一、Git基础](#一git基础)
  - [1. 获取Git仓库](#1-获取git仓库)
    - [1.1 在已存在目录中初始化仓库](#11-在已存在目录中初始化仓库)
    - [1.2 克隆现有的仓库](#12-克隆现有的仓库)
  - [2. 记录每次更新到仓库](#2-记录每次更新到仓库)
    - [2.1 文件状态](#21-文件状态)
    - [2.2 检查当前文件状态](#22-检查当前文件状态)
    - [2.3 跟踪新文件](#23-跟踪新文件)
    - [2.4 暂存已修改的文件](#24-暂存已修改的文件)
    - [2.5 状态简览](#25-状态简览)
    - [2.6 忽略文件](#26-忽略文件)
    - [2.7 查看已暂存和未暂存的修改](#27-查看已暂存和未暂存的修改)
    - [2.8 提交更新](#28-提交更新)
    - [2.9 跳过使用暂存区域](#29-跳过使用暂存区域)
    - [2.10 移除文件](#210-移除文件)
    - [2.11 移动文件](#211-移动文件)
  - [3. 查看提交历史](#3-查看提交历史)
  - [4. 撤销操作](#4-撤销操作)
    - [4.1 修改提交信息](#41-修改提交信息)
    - [4.2 取消暂存的文件](#42-取消暂存的文件)
    - [4.3 撤消对文件的修改](#43-撤消对文件的修改)
  - [5. 远程仓库的使用](#5-远程仓库的使用)
    - [5.1 查看远程仓库](#51-查看远程仓库)
    - [5.2 添加远程仓库](#52-添加远程仓库)
    - [5.3 从远程仓库中拉取](#53-从远程仓库中拉取)
    - [5.4 推送到远程仓库](#54-推送到远程仓库)
    - [5.5 查看某个远程仓库](#55-查看某个远程仓库)
    - [5.6 远程仓库的重命名与移除](#56-远程仓库的重命名与移除)
- [二、Git分支](#二git分支)
  - [1. 分支简介](#1-分支简介)
    - [1.1 分支创建](#11-分支创建)
    - [1.2 分支切换](#12-分支切换)
  - [2. 分支的新建与合并](#2-分支的新建与合并)
    - [2.1 新建分支](#21-新建分支)
    - [2.2 分支的合并](#22-分支的合并)
    - [2.3 遇到冲突时的分支合并](#23-遇到冲突时的分支合并)
  - [3. 分支管理](#3-分支管理)

# 一、Git基础
## 1. 获取Git仓库
* 将本地目录转化为Git仓库
* 从服务器克隆一个Git仓库
### 1.1 在已存在目录中初始化仓库
```bash
git init
```
该命令会创建一个名为.git的子目录，目录中包含Git仓库必须文件。
### 1.2 克隆现有的仓库
```bash
git clone <url>
git clone https://github.com/marktext/marktext.git
git clone git@github.com:marktext/marktext.git
```
## 2. 记录每次更新到仓库
### 2.1 文件状态
* 请记住，你工作目录下的每一个文件都不外乎这两种状态：已跟踪或未跟踪。<br/>
* 已跟踪的文件是指那些被纳入了版本控制的文件，在上一次快照中有它们的记录，在工作一段时间后，<br/>
  它们的状态可能是未修改，已修改或已放入暂存区。简而言之，已跟踪的文件就是 Git 已经知道的文件。<br/>
* 工作目录中除已跟踪文件外的其它所有文件都属于未跟踪文件，它们既不存在于上次快照的记录中，也没有被放入暂存区。<br/>
* 初次克隆某个仓库的时候，工作目录中的所有文件都属于已跟踪文件，并处于未修改状态，因为 Git刚刚检出了它们，而你尚未编辑过它们。<br/>
  编辑过某些文件之后，由于自上次提交后你对它们做了修改，Git 将它们标记为已修改文件。 在工作时，<br/>
  你可以选择性地将这些修改过的文件放入暂存区，然后提交所有已暂存的修改，如此反复。
### 2.2 检查当前文件状态
```bash
git status
On branch main
Your branch is ahead of 'origin/main' by 1 commit.
  (use "git push" to publish your local commits)

nothing to commit, working tree clean
```
### 2.3 跟踪新文件
```bash
git add <files>
```
### 2.4 暂存已修改的文件
```bash
git add <files>
```
`git add`是个多功能命令：
1. 可以用它开始跟踪新文件；
2. 或者把已跟踪的文件放到暂存区；
3. 还能用于合并时把有冲突的文件标记为已解决状态等。
### 2.5 状态简览
```bash
git status -s/--short
```
### 2.6 忽略文件
一般我们总会有些文件无需纳入 Git 的管理，也不希望它们总出现在未跟踪文件列表。<br/>
通常都是些自动生成的文件，比如日志文件，或者编译过程中创建的临时文件等。在这种情况下，<br/>
我们可以创建一个名为 .gitignore的文件，列出要忽略的文件的模式。
### 2.7 查看已暂存和未暂存的修改
```bash
git diff
```
### 2.8 提交更新
```bash
git commit
git commit -m "提交注释信息"
```
### 2.9 跳过使用暂存区域
```bash
git commit -a -m "提交注释信息"
```
### 2.10 移除文件
```bash
# 从文件夹内删除文件
rm <file>
git rm <files>
# 删除之前修改过或已经放到暂存区的文件
git rm -f <files>
# 把文件从Git仓库中删除（即从暂存区域移除），但仍保留在当前工作目录中。
git rm --cached <files>
```
### 2.11 移动文件
```bash
# 重命名文件
git mv file_from file_to
```
## 3. 查看提交历史
```bash
git log
```
## 4. 撤销操作
### 4.1 修改提交信息
有时候我们提交完了才发现漏掉了几个文件没有添加，或者提交信息写错了。<br/>
此时，可以运行带有 --amend 选项的提交命令来重新提交：
```bash
git commit --amend
# 使用流程
git commit -m "initial commit"
git add forgotten_file
git commit --amend
```
### 4.2 取消暂存的文件
```bash
git restore --staged <file>...
```
### 4.3 撤消对文件的修改
```bash
git restore <file>...
```
## 5. 远程仓库的使用
### 5.1 查看远程仓库
```bash
git remote
git remote -v
```
### 5.2 添加远程仓库
```bash
# 添加一个新的远程 Git 仓库，同时指定一个简写
git remote add <shortname> <url>
# 拉取远程仓库中有但你没有的信息
git fetch <shortname>
```
### 5.3 从远程仓库中拉取
```bash
# git fetch命令只会将数据下载到你的本地仓库——它并不会自动合并或修改你当前的工作
git fetch <remote>
# git pull通常会从最初克隆的服务器上抓取数据并自动尝试合并到当前所在的分支
git pull <remote>
```
### 5.4 推送到远程仓库
```bash
git push <remote> <branch>
```
### 5.5 查看某个远程仓库
```bash
git remote show <remote>
```
### 5.6 远程仓库的重命名与移除
```bash
# 重命名
git remote rename <oldname> <newname>
# 移除
git remote remove/rm <name>
```
# 二、Git分支
## 1. 分支简介
* Git的分支模是它的“必杀技特性”，也正因为这一特性，使得Git从众多版本控制系统中脱颖而出。
* Git 处理分支的方式可谓是难以置信的轻量，创建新分支这一操作几乎能在瞬间完成，
  并且在不同分支之间的切换操作也是一样便捷。
* 与许多其它版本控制系统不同，Git 鼓励在工作流程中频繁地使用分支与合并，哪怕一天之内进行许多次。
* Git 保存的不是文件的变化或者差异，而是一系列不同时刻的快照。
### 1.1 分支创建
```bash
git branch <branchname>
```
### 1.2 分支切换
```bash
git checkout <branchname>
```
## 2. 分支的新建与合并
### 2.1 新建分支
```bash
git checkout -b <branchname>
# git branch <branchname>
# git checkout <branchname>
```
### 2.2 分支的合并
```bash
# 返回主分支
git checkout main
# 合并分支
git merge <branchname>
# 删除分支
git branch -d <branchname>
```
### 2.3 遇到冲突时的分支合并
```bash
git mergetool
```
## 3. 分支管理
```bash
# 显示所有分支
git branch
git branch -v
```
如果要查看哪些分支已经合并到当前分支，可以运行`git branch --merged`:<br/>
```bash
$ git branch --merged
  iss53
* master
```
因为之前已经合并了 iss53 分支，所以现在看到它在列表中。在这个列表中分支名字前没有*号的分支通常可
以使用`git branch -d`删除掉；你已经将它们的工作整合到了另一个分支，所以并不会失去任何东西。
查看所有包含未合并工作的分支，可以运行 `git branch --no-merged`：
```bash
$ git branch --no-merged
  testing
```
这里显示了其他分支。因为它包含了还未合并的工作，尝试使用`git branch -d`命令删除它时会失败：
```bash
$ git branch -d testing
error: The branch 'testing' is not fully merged.
If you are sure you want to delete it, run 'git branch -D testing'.
```
```bash
# 尚未合并到 master 分支的有哪些？
git branch --no-merged master
```