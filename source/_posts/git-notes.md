title: Git学习笔记
date: 2015-12-23 11:49:57
tags:
---
##### 安装
【Windows】msysgit是Windows版的Git，从http://msysgit.github.io/下载，然后按默认选项安装即可
安装完后输入
```
$ git config --global user.name "Your Name"
$ git config --global user.email "email@example.com"
```
注意`git config`命令的`--global`参数，用了这个参数，表示你这台机器上所有的Git仓库都会使用这个配置，当然也可以对某个仓库指定不同的用户名和Email地址
##### 初始化一个Git仓库：
切换到所需目录输入`git init`
<!--more-->
##### 把文件放到Git仓库：
1.用`git add [filename]` 把文件添加到仓库。
2.用`git commit -m"[commit message]"` 把文件提交给仓库。[commit message]表示本次提交的说明。
3.注：可以多次`add`不同的文件，通过`commit`一次提交多个文件
##### 修改文件后：
运行`git status` 掌握仓库工作状态
```
$ git status
On branch master
Changes not staged for commit:
  (use "git add <file>..." to update what will be committed)
  (use "git checkout -- <file>..." to discard changes in working directory)

	modified:   readme.txt

no changes added to commit (use "git add" and/or "git commit -a")
```
运行`git diff` 具体查看修改内容
```
$ git diff
diff --git a/readme.txt b/readme.txt
index 46d49bf..9247db6 100644
--- a/readme.txt
+++ b/readme.txt
@@ -1,2 +1,2 @@
-Git is a version control system.
+Git is a distributed version control system.
 Git is free software.
```
##### 提交修改后的文件：
`git add` 此时键入`git diff`，若已添加所有修改后的文件到仓库，不会显示内容。
运行`git ststus` 显示将要提交的文件
```
$ git commit
On branch master
Changes to be committed:
  (use "git reset HEAD <file>..." to unstage)

	modified:   readme.txt
```
用`git commit -m"[commit message]"` 提交文件

##### 查看历史记录
`git log`
```
$ git log
commit 60774ec30fa7472336effe456f9488dc6e0c3f06
Author: BlackLine <*********@gmail.com>
Date:   Wed Dec 23 13:21:03 2015 +0800

    append GPL

commit 1f430a9b0526e613a338794b35d15e9fdf8f7643
Author: BlackLine <*********@gmail.com>
Date:   Wed Dec 23 12:34:00 2015 +0800

    add distributed

commit baad47381430610afc98beff43934c7a544f20d4
Author: BlackLine <*********@gmail.com>
Date:   Wed Dec 23 12:10:36 2015 +0800

    wrote a readme file
```
如果觉得输出信息太多，加上`--pretty=oneline`
```
$ git log --pretty=oneline
60774ec30fa7472336effe456f9488dc6e0c3f06 append GPL
1f430a9b0526e613a338794b35d15e9fdf8f7643 add distributed
baad47381430610afc98beff43934c7a544f20d4 wrote a readme file
```
##### 版本回退
如果要将当前版本回退到上一个版本
`git reset --hard HEAD^`
```
$ git reset --hard HEAD^
HEAD is now at 1f430a9 add distributed
```
用`git log`查看版本状态
```
$ git log
commit 1f430a9b0526e613a338794b35d15e9fdf8f7643
Author: BlackLine <jessywuzq@gmail.com>
Date:   Wed Dec 23 12:34:00 2015 +0800

    add distributed

commit baad47381430610afc98beff43934c7a544f20d4
Author: BlackLine <jessywuzq@gmail.com>
Date:   Wed Dec 23 12:10:36 2015 +0800

    wrote a readme file
```
如果误操作了，如果要恢复到新版本，就必须知道`append GPL`的commmit id
`git reflog`记录了每一次命令
```
$ git reflog
1f430a9 HEAD@{0}: reset: moving to HEAD^
60774ec HEAD@{1}: commit: append GPL
1f430a9 HEAD@{2}: commit: add distributed
baad473 HEAD@{3}: commit (initial): wrote a readme file
```
使用`git reset --hard 60774ec`就能回复最新版本
```
$ git reset --hard 60774ec
HEAD is now at 60774ec append GPL
```
Git的版本回退速度非常快，因为Git在内部有个指向当前版本的`HEAD`指针，当你回退版本的时候，Git仅仅是把HEAD从指向`append GPL`：
![](/images/GitReset01.jpg)
改为指向`add distributed`：
![](/images/GitReset02.jpg)
然后顺便把工作区的文件更新了。所以你让`HEAD`指向哪个版本号，你就把当前版本定位在哪。
##### 工作区与暂存区
###### 工作区（Working Directory）
在电脑里能看到的目录，一个文件夹就是一个工作区
###### 版本库（Repository）
工作区里有一个隐藏目录`.git`，是Git的版本库
Git版本库里最重要的是称为`index`的暂存区,还有Git自动创建的第一个分支`master`以及指向`master`的一个指针`HEAD`。
![](/images/GitRepository01.jpg)
把文件添加到Git版本库是分两步执行的：
1.`git add`添加文件，把文件修改提交到暂存区
2.`git commit`提交修改，把暂存区的所有内容提交到当前分支
___
修改readme.txt 新建一个LICENSE文件
用`git status`查看状态
```
$ git status
On branch master
Changes not staged for commit:
  (use "git add <file>..." to update what will be committed)
  (use "git checkout -- <file>..." to discard changes in working directory)

	modified:   readme.txt

Untracked files:
  (use "git add <file>..." to include in what will be committed)

	LICENSE

no changes added to commit (use "git add" and/or "git commit -a")
```
Git显示readme.txt被修改了，LICENSE从未被添加过，所以状态为`Untracked`
将两个文件添加后
```
$ git status
On branch master
Changes to be committed:
  (use "git reset HEAD <file>..." to unstage)

	new file:   LICENSE
	modified:   readme.txt
```
暂存区变成：
![](/images/GitRepository02.jpg)
所以`git add`命令就是把要提交的修改放到暂存区
然后执行`git commit`把暂存区所有修改提交到分支
```
$ git commit -m"understand how stage works"
[master 46fb205] understand how stage works
 2 files changed, 2 insertions(+)
 create mode 100644 LICENSE
```
一旦提交，若没对工作区作修改，那工作区就是“干净的”
```
$ git status
On branch master
nothing to commit, working directory clean
```
暂存区就没有任何内容
![](/images/GitRepository03.jpg)
##### 撤销修改
1.在`git add`之前：
手动修改或者
`$ git checkout -- <file>`
命令`$ git checkout -- readme.txt`的意思是撤销readme.txt在工作区的全部更改，包括
* readme.txt修改后未放到暂存区，撤销修改就回到版本库状态
* readme.txt已经添加到暂存区又作了修改，撤销修改回到添加到暂存区时的状态

即回到最近一次`git commit`或`git add`状态
2.在`git add`之后
`git reset HEAD <file>`撤销暂存区修改，重新放回工作区
`git reset`命令既可以回退版本，也可以把暂存区的修改回退到工作区。当我们用`HEAD`时，表示最新的版本。
再使用方法1
3.在`git commit`后
使用版本回退`git reset --hard HEAD^`
##### 删除文件
假设删除文件test.txt
`rm test.txt`
运行`git status`
```
$ git status
On branch master
Changes not staged for commit:
  (use "git add/rm <file>..." to update what will be committed)
  (use "git checkout -- <file>..." to discard changes in working directory)

	deleted:    test.txt

no changes added to commit (use "git add" and/or "git commit -a")
```
此时有两个选择：
1. 从版本库中删除文件
```
$ git rm test.txt
rm 'test.txt'
```
然后`git commit`
```
$ git commit -m"remove test.txt"
[master 3fb8529] remove test.txt
 1 file changed, 0 insertions(+), 0 deletions(-)
 delete mode 100644 test.txt
```

2. 误删
`git checkout -- test.txt`
`git checkout`其实是用版本库里的版本替换工作区的版本，无论工作区是修改还是删除，都可以“一键还原”。

##### 远程库
###### 添加远程库
1.添加远程库地址
`git remote add origin https://github.com/black-line/LearnGit.gut`
或者`git remote add origin git@github.com:black-line/LearnGit.git`
2.把本地库所有内容推送到远程库上`git push -u origin master`
```
Counting objects: 17, done.
Delta compression using up to 4 threads.
Compressing objects: 100% (12/12), done.
Writing objects: 100% (17/17), 1.38 KiB | 0 bytes/s, done.
Total 17 (delta 4), reused 0 (delta 0)
To git@github.com:black-line/LearnGit.git
 * [new branch]      master -> master
Branch master set up to track remote branch master from origin.
```
把本地库的内容推送到远程，用`git push`命令，实际上是把当前分支`master`推送到远程。
由于远程库是空的，第一次推送`master`分支时，加上了`-u`参数，Git不但会把本地的`master`分支内容推送的远程新的`master`分支，还会把本地的`master`分支和远程的`master`分支关联起来，在以后的推送或者拉取时就可以简化命令。
* 现在只要`$ git push origin master`就能将本地`master`分支修改推送到GitHub上
###### 从远程库克隆
`$ git clone git@github.com:black-line/gitskills.git`
```
$ git clone git@github.com:black-line/gitskills.git
Cloning into 'gitskills'...
remote: Counting objects: 3, done.
remote: Total 3 (delta 0), reused 0 (delta 0), pack-reused 0
Receiving objects: 100% (3/3), done.
Checking connectivity... done.
```
##### 分支管理
未创建其它分支前，仓库里只有一条分支，即`master`分支
`HEAD`指向`master`分支，`master`指向提交，所以`HEAD`指向当前分支。
一开始的时候，`master`分支是一条线，Git用`master`指向最新的提交，再用`HEAD`指向`master`，就能确定当前分支，以及当前分支的提交点：
![](/images/Branch01.png)
每次提交，`master`分支都会向前移动一步，这样，随着不断提交，`master`分支的线也越来越长：
当创建新的分支，例如`dev`时，Git新建了一个指针叫`dev`，指向`master`相同的提交，再把`HEAD`指向`dev`，就表示当前分支在`dev`上：
![](/images/Branch02.png)
从现在开始，对工作区的修改和提交就是针对`dev`分支了，比如新提交一次后，`dev`指针往前移动一步，而`master`指针不变：
![](/images/Branch03.png)
假如我们在`dev`上的工作完成了，就可以把`dev`合并到`master`上。就是直接把`master`指向`dev`的当前提交，就完成了合并：
![](/images/Branch04.png)
合并完分支后，甚至可以删除`dev`分支。删除`dev`分支就是把`dev`指针给删掉，删掉后，我们就剩下了一条`master`分支：
![](/images/Branch05.png)

###### 实战
创建并切换到`dev`分支
```
$ git checkout -b dev
Switched to a new branch 'dev'
```
`$ git checkout -b dev`等同于
```
$ git branch dev
$ git checkout dev
```
用`git branch`查看当前分支
```
$ git branch
* dev
  master
```
在`dev`分支上修改readme.txt并提交
```
$ git add readme.txt
$ git commit -m"branch test"
[dev f7b61c8] branch test
 1 file changed, 1 insertion(+)
```
切换到`master`分支，发现readme.txt内容并没有变,因为那个提交是在`dev`分支上，而`master`分支此刻的提交点并没有变。
把`dev`分支合并到`master`分支：
```
$ git merge dev
Updating 3fb8529..f7b61c8
Fast-forward
 readme.txt | 1 +
 1 file changed, 1 insertion(+)
```
`git merge`命令用于合并指定分支到当前分支
`Fast-forward`信息显示此次合并是快进模式，即`master`直接指向`dev`
删除`dev`分支：
```
git branch -d dev
Deleted branch dev (was f7b61c8).
```
Git鼓励大量使用分支：

* 查看分支：`git branch`

* 创建分支：`git branch <name>`

* 切换分支：`git checkout <name>`

* 创建+切换分支：`git checkout -b <name>`

* 合并某分支到当前分支：`git merge <name>`

* 删除分支：`git branch -d <name>`

###### 解决冲突
当在分支`feature1`和`master`上同一个文件都做修改后，分支如图
![](/images/conflict01.png)
快速合并会产生冲突，必须手动解决冲突,
```
$ git merge feature1
Auto-merging readme.txt
CONFLICT (content): Merge conflict in readme.txt
Automatic merge failed; fix conflicts and then commit the result.
```
使用`git status`查看
```
$ git status
On branch master
Your branch is ahead of 'origin/master' by 1 commit.
  (use "git push" to publish your local commits)
You have unmerged paths.
  (fix conflicts and run "git commit")

Unmerged paths:
  (use "git add <file>..." to mark resolution)

	both modified:   readme.txt

no changes added to commit (use "git add" and/or "git commit -a")
```
查看readme.txt内容
```
$ cat readme.txt
Git is a distributed version control system.
Git is free software distributed under the GPL.
Git has a mutable index called stage.
<<<<<<< HEAD
Creating a new branch is quick &&&&&&&&&& SIMPLE.
=======
Creating a new branch is quick AND simple.
>>>>>>> feature1
```
Git用`<<<<<<<`，`=======`，`>>>>>>>`标记出不同分支的内容
手动修改后提交：
```
$ git commit -a -m"conflict fixed"
[master c4715f1] conflict fixed
```
此时分支如图：
![](/images/conflict02.png)
使用带参数`git log`查看分支合并情况
```
$ git log --graph --pretty=oneline --abbrev-commit
*   c4715f1 conflict fixed
|\  
| * 2370a7d AND simple
* | ca687db &&&&&&&&& SIMPLE
|/  
* f7b61c8 branch test
* 3fb8529 remove test.txt
* f6dbb03 add test.txt
* 46fb205 understand how stage works
* 60774ec append GPL
* 1f430a9 add distributed
* baad473 wrote a readme file
```
最后删除分支
`git branch -d feature1`
