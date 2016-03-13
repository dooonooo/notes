title: Git 命令基本操作
date: 2016-01-02 22:21:15
categories:
tags:
- 基本操作
- git
---


![bg2015120901](/media/bg2015120901.png)
日常使用只要记住上图6个命令，就可以了
<!--more-->
图来自：http://www.ruanyifeng.com/blog/2015/12/git-cheat-sheet.html

## zui常用的命令


## 新建代码库

	//在当前目录新建一个git代码库
	git init
	
	新建一个目录，并将其初始化为git代码库
	git init [project－name]
	
	下载一个项目和它的整个代码历史
	git clone [url]
	
## 配置
git的配置文件为`.gitconfig`,它可以在用户目录下（全局配置），也可以在项目目录下（项目配置）。

	显示当前的git配置
	git config --list	
	
	编辑git配置文件
	git config -e [--global]
	
	设置提交代码时的用户信息
	git config [--global] user.name "[name]"
	git cinfig [--gloabl] user.email "[email address]"

## 增加/删除文件

	添加指定文件到暂存区
	git add [file1] [file2] ..
	
	添加指定目录到暂存区，包括子目录
	git add [dir]
	
	添加当前目录的所有文件到暂存区
	git add
	
	删除工作区文件，并且将这次删除放入暂存区
	git rm [file1] [file2]
	
	停止追踪指定文件，但该文件会保留在工作区
	git rm --cached [file]
	
	该名文件，并且将这个改名放入暂存区
	git mv [file-original] [file-renamed]
	
## 代码提交
	
	提交暂存区到仓库区
	git commit -m [message]
	
	提交暂存区的指定文件到仓库
	git commit [file1] [file2] ... -m [message]
	
	提交工作区自上次commit之后的变化，直接到仓库区
	git commit -a
	
	提交时现实所有diff信息
	gitcommit -v
	
	使用一次新的commit， 替代上一次的提交
	如果代码没有任何变化，则用了改写上一次的commmit的提交信息
	git commit --amend -m [message]
	
	git commit -- amend [file1] [file2] ...
	
## 分支

	列出所有本地分支
	git branch
	
	列出所有远程分支
	git branch -r
	
	列出所有本地分支和远程分支
	git branch -a
	
	新建一个分支，但依然停留在当前分支
	git branch [branch-name]
	
	新建一个分支，并切换到该分支
	git branch -b [branch-name]
	
	
	切换到指定分支，并更新工作区
	git checkout [branch-name]
	
	建立追踪关系，在现有分支与指定的远程分支之间
	[]
	
	合并指定分支到当前分支
	git merge [branch]
	
	选择一个commit,合并到当前分支
	git cherry-pick[commit]
	
	删除分支
	git branch -d [branch-name]
	
	删除远程分支
	git push origin --delete[branch-name]
	git branch -dr [remote/branch]
	
## 标签

	列出所有tag
	git tag
	
	新建一个tag在当前commit
	git tag [tag]
	
	新建一个tag在指定commit
	git tag [tag] [commit]
	
	删除本地tag
	git tag -d [tag]
	
	删除远程tag
	git tag －d [tag]
	
	查看tag信息
	git show [tag]
	
	提交指定tag
	git push [remote][tag]
	
	提交所有tag
	git push [remote] --tags
	
	新建一个分支，指向某个tag
	git checkout -b [branch] [tag]

## 查看信息

	显示有变更的文件
	git status
	
	显示当前分支的版本历史
	git log
	
	显示commit历史，以及每次commit发生变更的文件
	git log --stat
	
	[]
	
	显示某个文件的版本历史，包括文件改名
	git log --follow [file]
	git whatchanged [file]
	
	显示指定文件相关的每一次diff
	git log -p [file]
	
	显示指定文件是什么人在什么时间修改过
	git blame [file]
	
	显示暂存区和工作区的差异
	git diff
	
	[]
	
	
	
	
	
	
## 远程同步
	下载远程仓库的所有变动
	git fetch [remote]
	
	显示所有远程仓库
	git remote -v
	
	显示某个远程仓库的信息
	git remote show [remote]
	
	增加一个新的远程仓库，并命名
	git remote add [shortname] [url]
	
	取回远程仓库的变化，并与本地分支合并
	git pull [remote] [branch]
	
	上传本地指定分支到远程仓库
	git push [remote] [branch]
	
	强行推送当前分支到远程仓库，即使有冲突
	git push [remote] [branch]
	
	推送所有分支到远程仓库
	git push [remote] --all

## 撤销

	恢复暂存区的指定文件到工作区
	git checkout [file]
	
	恢复某个commit的指定文件到工作区
	git checkout [commit] [file]
	
	恢复上一个commit的所有文件到工作区
	git checkout
	
	重置暂存区的指定文件，与上一次commit保存一致，但工作区不变
	git reset [file]
	
	重置暂存区与工作区，与上一次commit保持一致
	git reset --hard
	
	重置当前分支的指针为指定commit，同时重置暂存区和文件区，但工作区不变
	git reset [commit]
	
	重置当前分支的HEAD为指定commit，同时重置暂存区和工作区，与指定commit一致
	git reset --hard [commit]
	
	重置当前HEAD为指定commit，但保持暂存区和工作区不变
	git reset --keep [commit]
	
	新建一个commit，用了撤销指定commit
	后者的所有变化都将被前者抵消，并且应用到当前分支
	git revert [commit]
	
## 其他

	生成一个可供发布的压缩包
	git archive
	
	
####参考：
1.[常用 Git 命令清单](http://www.ruanyifeng.com/blog/2015/12/git-cheat-sheet.html)



