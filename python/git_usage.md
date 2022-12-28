- [Git基础](#git基础)
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

# Git基础
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
git rm <file>
```