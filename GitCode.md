# GitCode

把当前目录变成git仓库：git init  
把文件添加到仓库：git add [文件名]  //注：可添加多个文件，以空格隔开
把文件提交到仓库：git commit -m "提交说明"
查看当前仓库的状态：git status  //nothing to commit (working directory clean) 表示没有要提交的修改
查看某个文件修改的差异：git diff [文件名]
查看每次提交的历史：git log  //如果嫌输出的信息过多，可以添加--pretty=oneline
git 回退版本：git reset --hard HEAD^ 或回退到指定commit id ep:git reset --hard fb67e35
查询之前提交的命令：git reflog //可以查看到近期提交的commit id

工作区和暂存区理解

版本库（Repository）

工作区有一个隐藏目录.git，这个不算工作区，而是Git的版本库。
Git的版本库里存了很多东西，其中最重要的就是称为stage（或者叫index）的暂存区，还有Git为我们自动创建的第一个分支master，以及指向master的一个指针叫HEAD。
![理解](http://www.liaoxuefeng.com/files/attachments/001384907702917346729e9afbf4127b6dfbae9207af016000/0)
