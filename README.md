
#############################
## git    版本管理工具   https://www.cnblogs.com/alex3714/articles/5930846.html

#############################
## 基本操作 

git init                   # 创建一个版本库  
aaa


git add                    # 工作区提交到暂存区(Stage)
git add .                  # 所有的文件一起提交

git commit -m "..."        # 暂存区的所有内容提交到当前分支
						   # 简单理解,需要提交的文件修改通通放到暂存区，然后一次性提交暂存区的所有修改。
git status                 

git diff                   # 比较工作区和暂存区的不同

git log                    # 显示从最近到最远的提交日志
git log --pretty=oneline   # 简洁显示

git reset --hard HEAD^     # 用HEAD表示当前版本，一个版本就是HEAD^，上上一个版本就是HEAD^^
git reset --hard 2f17147   # git log 显示的版本号，版本号没必要写全，前几位就可以了，Git会自动去找。

git reflog                 # 记录你所有的版本改变，可以用来找所有的版本号

git checkout -- readme.md  # readme.md文件在工作区的修改全部撤销，两种情况：1）是readme.md自修改后还没有被放到暂存区，现在，撤销修改就回到和版本库一模一样的状态；2）是readme.md已经添加到暂存区后，又作了修改，现在，撤销修改就回到添加到暂存区后的状态。   总之，就是让这个文件回到最近一次git commit或git add时的状态。    git checkout其实是用版本库里的版本替换工作区的版本，无论工作区是修改还是删除，都可以“一键还原”。


git reset HEAD readme.md  # 将提交的暂存区的修改版本撤销掉（unstage）

git rm test.txt           # 工作区中删除了文件，然后从版本库中删除该文件，也可以用git add 来更新删除信息到暂存区。如果是删错了，用git checkout -- test.txt 还原。 


git push origin master    # 推到远程



#############################
## 分支管理 

git branch dev            # 创建dev分支


git checkout dev          # 切换到dev分支
git checkout -b dev       # 创建dev分支，然后切换到dev分支


git branch                # 查看当前分支


git merge dev             # git merge命令用于合并指定分支到当前分支。  git status也可以告诉我们冲突的文件，然后查看冲突的文件，去掉<<<<<<<，=======，>>>>>>>，然后用git add , git commit 重新提交。   git log --graph --pretty=oneline 以看到分支的合并情况


git branch -d dev         # 删除dev分支



#############################
## 保存现场 

git stash                 # 可以把当前工作现场“储藏”起来。  用git status查看工作区，就是干净的（除非有没有被Git管理的文件）


git stash list            

            
git stash apply stash@{0} # 用git stash apply恢复，但是恢复后，stash内容并不删除，你需要用git stash drop来删除；


git stash pop             # 恢复的同时把stash内容也删了



#############################
## 多人协作

git remote                # 查看远程库的信息   远程仓库的默认名称是origin   -v显示更详细的信息


git push origin dev       # 要推送其他分支，比如dev


git checkout -b dev origin/dev      # 创建远程origin的dev分支到本地


git pull                  # 当git pull失败，原因是没有指定本地dev分支与远程origin/dev分支的链接，根据提示，设置dev和origin/dev的链接            ：git branch --set-upstream-to=origin/dev dev   




#############################
## 在GitHub上，可以任意Fork开源仓库；自己拥有Fork后的仓库的读写权限；可以推送pull request给官方仓库来贡献代码。




#############################
## .gitignore

git add -f App.class             # 想添加一个文件到Git，但发现添加不了，原因是这个文件被.gitignore忽略了，可以用-f强制添加到Git


git check-ignore -v App.class    # 发现可能.gitignore写得有问题，需要找出来到底哪个规则写错了，可以用git check-ignore命令检查













