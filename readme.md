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
23.分支冲突：当两个分支在同一个地方做了不同的更改，不能自动合并。需要我们手动将内容更改到最新版。
            git log --graph --pretty=oneline --abbrev-commit(查看分支冲突)
24.分支管理策略：
    fast forward模式：git merge dev(会丢失掉dev的分支信息)
    禁止fast for模式：git merge --no-f -m "no-f" dev(dev的分支信息存在并用-m做说明)
25.Bug:当我们存在master与dev分支后，现在还需要一个bug分支来更改bug时
    1）git status（查看当前工作分支dev的状态，存在未提交的修改内容，但是工作未完成无法提交）
    2）git stash （将当前工作现场储存起来，等以后恢复现场使用）（执行操作后当前分支状态未未更改状态）
    3）git switch master（切换分支到master）
    4）git switch -c issue-101（在master的基础上添加issue-101分支并切换）
    5）在issue分支上更改bug并提交。
    6）git switch master
    7）git merge --no-f -m "merged bug fix 101" issue-101(将issue-101分支与master合并并保留合并信息)
    8）git switch dev
    9）git stash list(查看之前保存的保存工作状态)
    10）git stash pop（恢复之前的工作状态并删除stash上的状态）= git stash apply（回复）+ git stash drop（删除）
    11）git stash可以保存多次状态，用git stash list查看后可以用git stash apply stash@{n}来选择恢复成哪一个
    12）当我们将master上的bug修改后，dev也是从master分支过来的要怎么更改
    13）git cherry-pick 209e846(在dev分支上执行此操作，提交改bug提交的commit文件信息，即可复制之前更改好的内容)
    14）说明: ①当两个分支的工作区都存在更改内容时，我们不能执行更改分支操作。这是因为我们的工作区、暂存区是公用的。
            ②若是不这么操作，也可将未完成的内容执行add/commit操作后在新建分支bug操作（不太建议将未完成的提交）
            ③bug
