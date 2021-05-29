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
13.工作区删除：rm test.txt
14.版本库删除：git rm test.txt(暂存区) -> git commit -m "remove test.txt"
15.与github链接（ssh）：
    1）ssh-keygen -t rsa -C "youremail@example.com"（创建ssh key）
    2）cd .ssh ->code id_rsa.pub(公匙)
    3)在git中创建新的仓库
    4）git remote add origin https://github.com/mengfan525/tencent_linux.git（将git仓库与本地仓库相连）
    5)git push -u origin master(将当前分支master上传到github,-u是第一次将本地与远程的master关联)
16.断开与远程库链接：
    1）git remote -v(查看远程库信息)
    2）git remote rm origin（解除与远程库链接，删除远程库需要在github上操作）
17.克隆远程库：git clone https://github.com/mengfan525/git.git
18.创建分支：git checkout -v dev(创建dev分支并切换到dev分支) / git switch -c dev
    git branch dev(创建dev分支) : git checkout dev(切换到dev分支)
19.查看分支：git branch
20.切换分支：git switch master /  git checkout dev
21.合并分支：git merge dev(将dev分支合并到当前分支)
22.删除分支：git branch -d dev
23.分支冲突：