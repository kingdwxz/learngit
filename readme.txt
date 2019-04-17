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