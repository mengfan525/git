frist to git
1.判断是否安装git，在终端输入git
2.若是提示安装，sudo apt-get install git
3.设置全局变量，git config --global user.name "":git config --global user.email ""
4.建立你想要保存git文件的文件夹（file），cd file
5.在file中， git init /git clone "adress  " 
6.新建文件info，git add info -> git commit -m "说明信息"
7.版本退回：git log(查看版本信息) -> git reset --hard HEAD^n(退回n个版本)
8.退回指定版：git reset --hard 329bc46（版本号）
9.后悔想恢复：git reflog（查看版本变更信息，找出最新的） ->使用退回指定版本命令
10.对比：git diff（默认工作区与暂存对比），git diff HEAD(工作区与版本库对比)
11.丢弃工作区修改：git restore file(readme.md)
12.丢弃暂存区修改：git reset HEAD <file> / git restore --staged readme.txt