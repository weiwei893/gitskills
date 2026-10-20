$ git config --global user.name "Your Name"

$ git config --global user.email "email@example.com"

注意git config命令的--global参数，用了这个参数，表示你这台机器上所有的Git仓库都会使用这个配置，当然也可以对某个仓库指定不同的用户名和Email地址。



在对应路径下打开git

创建一个版本库

$ mkdir *learngit(仓库的名字）*

$ cd learngit（进入当前文件夹）

$ pwd（pwd电脑回答你你在这个文件夹里，ls电脑回答你这个文件夹里有哪几个文件）



通过git init命令把这个目录变成Git可以管理的仓库：

$ git init(可以直接克隆，不要这一步)



文件一定要放在工作区（对应文件夹）

把文件存进Git仓库，每次修改了文件都要执行

$ git add *readme.txt（文件名)*     把文件放进暂存区

$ git commit -m *"wrote a readme file"(提交时备注内容)*



$ git status 查看工作区和暂存区的状态



查看修改了什么内容

$ git diff *readme.txt* *（文件名）*

查看工作区和版本库里面最新版本的区别

$ git diff HEAD -- readme.txt 



$git log命令显示从最近到最远的提交日志，可以查看提交的不同版本号



$ git log --pretty=oneline  简化输出信息



回退到上一个版本

$ git reset --hard HEAD^



查看文件里的内容

$ cat *readme.txt*



回到某一个版本

$ git reset --hard *1094a（版本号的前几位）*



撤回一步修改。修改后还没有被放到暂存区，用版本库里的版本替换工作区的版本；已经添加到暂存区后，又作了修改，现在，撤销修改就回到添加到暂存区后的状态。

$ git checkout -- readme.txt



删文件

$ rm test.txt



创建SSH Key

$ ssh-keygen -t rsa -C "youremail@example.com"



关联本地仓库和github仓库

$ git remote add origin git@github.com:*github用户名*/*learngit.git（Github仓库名）*



把本地库的所有内容推送到远程库

$ git push -u origin master(main)
$ git push origin master(main)



查看远程库信息

$git remote -v

删除远程库

$ git remote rm origin



从远程库克隆

$git clone git@github.com:Github用户名/gitskills.git



创建并切换分支

（1）$ git branch dev

&#x20;        $ git checkout dev

（2）$ git checkout -b *dev（分支名字）*

（3）$ git switch -c dev

查看分支有哪些，当前分支

$ git branch

在分支上改完也记得add, commit



切换到分支

$ git checkout *main（分支名字）*

或$ git switch master



合并到主分支（切换到main再合并）

$ git merge *dev（分支名字）*

$ git merge --no-ff -m "merge with no-ff" *dev*（禁用Fast forward，留下分支历史记录）



删除分支
$ git branch -d *dev（分支名字）*

$ git branch -D *feature-vulcan*（强行删除还没有合并的分支）



分支合并冲突时

直接查看对应文件进行删改再提交



查看分支合并情况

$ git log --graph --pretty=oneline --abbrev-commit



保存并隐藏还未提交的修改

$ git stash



查看隐藏

$ git stash list



修复完bug再把它放到工作区

$ git stash pop



打标签

$ git tag *v1.0*

$ git tag  查看标签

$ git log --pretty=oneline --abbrev-commit（查版本号）

$ git tag *v0.9 f52c633*（给历史版本打标签）

$ git tag -a *v0.1* -m *"version 0.1 released"* *1094adb*（带有备注的标签）

$ git tag -d v0.1 （删除标签）

$ git push origin v1.0（推送某个标签到远程）

$ git push origin --tags（推送全部标签）

$ git push origin :refs/tags/v0.9（远程删除标签）

