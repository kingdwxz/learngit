git is a version control system.
git is free software

1、安装git，windwos下载程序安装即可
2、设置git
git config --global user.email "kingdwxz@163.com"
git config --global user.name "kingd"
3、初始化git
找到本机一个文件夹当做git的仓库，输入下面的命令
git init
4、基本命令
添加了一个文件并上传至git。加入这个文件为readme.txt
git add readme.txt
git commit -m "这是一个学习git的文件"

如果修改了readme.txt,查看状态命令
git status 

如果想看readme.txt修改了哪些内容
git diff readme.txt

查看完之后，按q退出当前文档即可。

查看git提交修改记录
git log

如果嫌输出信息太多，看得眼花缭乱的，可以试试加上--pretty=oneline参数：

如果要回退到上一个版本，则使用下面的命令
git reset --hard HEAD^
或者
git reset --hard 版本号

查看每一次命令执行语句
git reflog

如果想对比本地文件和版本库中文件的区别，用以下命令
git diff HEAD --readme.txt

如果想撤回到上一个版本，可通过以下命令
git checkout -- readme.txt

命令git checkout -- readme.txt意思就是，把readme.txt文件在工作区的修改全部撤销，这里有两种情况：
一种是readme.txt自修改后还没有被放到暂存区，现在，撤销修改就回到和版本库一模一样的状态；
一种是readme.txt已经添加到暂存区后，又作了修改，现在，撤销修改就回到添加到暂存区后的状态。
总之，就是让这个文件回到最近一次git commit或git add时的状态。
git checkout -- file命令中的--很重要，没有--，就变成了“切换到另一个分支”的命令

场景1：当你改乱了工作区某个文件的内容，想直接丢弃工作区的修改时，用命令git checkout -- file。
场景2：当你不但改乱了工作区某个文件的内容，还添加到了暂存区时，想丢弃修改，分两步，第一步用命令git reset HEAD <file>，就回到了场景1，第二步按场景1操作。
场景3：已经提交了不合适的修改到版本库时，想要撤销本次提交，参考版本回退，不过前提是没有推送到远程库。


删除文件
git rm test.txt
git commit -m "删除了test.txt"

恢复文件
git checkout -- test.txt

要关联一个远程库，使用命令git remote add origin git@server-name:path/repo-name.git；
关联后，使用命令git push -u origin master第一次推送master分支的所有内容；
此后，每次本地提交后，只要有必要，就可以使用命令git push origin master推送最新修改；

创建分支
git checkout -b dev
查看当前分支
git branch

Git鼓励大量使用分支：
查看分支：git branch
创建分支：git branch <name>
切换分支：git checkout <name>
创建+切换分支：git checkout -b <name>
合并某分支到当前分支：git merge <name>
删除分支：git branch -d <name>

退出编辑页面
按下ESC，再连按两下大写的字母Z

用git log --graph命令可以看到分支合并图。

合并分支禁用fast forward
it merge --no-ff -m "merge with no-ff" dev

查看远程库信息
git remote
或者
git remote -v 显示更详细的信息

创建远程dev分支到本地
git checkout -b dev origin/dev

设置本地dev分支与远程origin/dev分支关联
git branch --set-upstream dev origin/dev

将最新的提交拉取到本地
git pull

多人写作模式
首先，可以试图用git push origin <branch-name>推送自己的修改；

如果推送失败，则因为远程分支比你的本地更新，需要先用git pull试图合并；

如果合并有冲突，则解决冲突，并在本地提交；

没有冲突或者解决掉冲突后，再用git push origin <branch-name>推送就能成功！

如果git pull提示no tracking information，则说明本地分支和远程分支的链接关系没有创建，用命令git branch --set-upstream-to <branch-name> origin/<branch-name>。

这就是多人协作的工作模式，一旦熟悉了，就非常简单。



命令git tag <tagname>用于新建一个标签，默认为HEAD，也可以指定一个commit id；

命令git tag -a <tagname> -m "blablabla..."可以指定标签信息；

命令git tag可以查看所有标签。

命令git push origin <tagname>可以推送一个本地标签；
命令git push origin --tags可以推送全部未推送过的本地标签；
命令git tag -d <tagname>可以删除一个本地标签；
命令git push origin :refs/tags/<tagname>可以删除一个远程标签。





==============================================================================================================
git init
git add README.md
git commit -m "first commit"
git remote add origin ssh://kingd@192.168.1.116:29418/test.git
git push -u origin master


git remote add origin ssh://kingd@192.168.1.116:29418/test.git
git push -u origin master

删除分支
1、删除本地分支
git branch -d BranchName
2、远程删除git服务器上的分支：
git push origin -d BranchName
