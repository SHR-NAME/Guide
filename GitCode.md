# GitCode

把当前目录变成git仓库：git init  

把文件添加到仓库：git add [文件名]  //注：可添加多个文件，以空格隔开

把文件提交到仓库：git commit -m "提交说明"

查看当前仓库的状态：git status  //nothing to commit (working directory clean) 表示没有要提交的修改

查看某个文件修改的差异：git diff [文件名]

查看每次提交的历史：git log  //如果嫌输出的信息过多，可以添加--pretty=oneline

查看分支的合并情况：git log --graph --pretty=oneline --abbrev-commit

git 回退版本：git reset --hard HEAD^ 或回退到指定commit id ep:git reset --hard fb67e35

查询之前提交的命令：git reflog //可以查看到近期提交的commit id

把暂存区的修改撤销掉（unstage），重新放回工作区：git reset HEAD [文件名]

丢弃工作区的修改或者删除的文件还原到工作区：git checkout -- [文件名]

删除文件：git rm [文件名]

关联远程仓库：git remote add origin [仓库地址]

提交本地仓库代码到远程：git push -u origin master

由于远程库是空的，我们第一次推送master分支时，加上了-u参数，Git不但会把本地的master分支内容推送的远程新的master分支，还会把本地的master分支和远程的master分支关联起来，在以后的推送或者拉取时就可以简化命令
这样：git push origin master

从远程克隆：git clone [远程仓库地址]

切换分支：git checkout [分支名]

创建并切换分支:git checkout -b [分支名] 相当于 git branch [分支名]；git checkout [分支名]

查看当前分支：git branch

删除分支:git branch -d [分支名]

没有合并删除分支：>git branch -D [分支名]

合并到当前分支：git merge [其他分支分支名] ；git merge --no-ff -m "提交说明" dev

合并分支时，加上--no-ff参数就可以用普通模式合并，合并后的历史有分支，能看出来曾经做过合并，而fast forward合并就看不出来曾经做过合并。

存储工作空间：git stash //保存现场

查看工作现场：git stash list

恢复工作现场：一是用git stash apply恢复，但是恢复后，stash内容并不删除，你需要用git stash drop来删除；另一种方式是用git stash pop，恢复的同时把stash内容也删了

查看远程仓库信息：git remote 添加-v显示更详细信息

在本地创建和远程分支对应的分支，使用git checkout -b [分支名] origin/[分支名]，本地和远程分支的名称最好一致；

建立本地分支和远程分支的关联，使用git branch --set-upstream [分支名] origin/[分支名]；

添加标签：切换到需要打tag的分支，执行 ：git tag [tag] el:git tag v1.0

查看标签：git tag

**工作区和暂存区理解**

版本库（Repository）

工作区有一个隐藏目录.git，这个不算工作区，而是Git的版本库。
Git的版本库里存了很多东西，其中最重要的就是称为stage（或者叫index）的暂存区，还有Git为我们自动创建的第一个分支master，以及指向master的一个指针叫HEAD。

![理解](http://www.liaoxuefeng.com/files/attachments/001384907702917346729e9afbf4127b6dfbae9207af016000/0)

**分支策略**

在实际开发中，我们应该按照几个基本原则进行分支管理：

首先，master分支应该是非常稳定的，也就是仅用来发布新版本，平时不能在上面干活；

那在哪干活呢？干活都在dev分支上，也就是说，dev分支是不稳定的，到某个时候，比如1.0版本发布时，再把dev分支合并到master上，在master分支发布1.0版本；

你和你的小伙伴们每个人都在dev分支上干活，每个人都有自己的分支，时不时地往dev分支上合并就可以了。

所以，团队合作的分支看起来就像这样：

![branch](http://www.liaoxuefeng.com/files/attachments/001384909239390d355eb07d9d64305b6322aaf4edac1e3000/0)

**如何解决远程冲突**

1. git pull 从远程啦取最新的代码
2. 在本地解决冲突，合并
3. 提交代码到远程

 注：git pull提示“no tracking information”，则说明本地分支和远程分支的链接关系没有创建，用命令git branch --set-upstream branch-name origin/branch-name
