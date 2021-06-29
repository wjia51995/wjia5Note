# git最基本的流程

## 创建工作目录，对工作目录进行修改

git add ./

​	git hash-object -w 文件名（修改了多少个工作目录中的文件，此命令就要被执行多少次）

​	git update-index

git commit -m "注释内容"

​	git write-tree

​	git commit-tree

# git高层命令（CRUD）

​	git init								初始化仓库

​	git status							检查当前文件状态

​	git diff								查看哪些修改还没有暂存

​	git diff --staged				查看哪些修改以及被暂存了 还没有提交

​	git diff --cached				同上

​	git log --oneline				查看提交的历史记录

​	git add ./							将修改添加到暂存区（会先添加到版本库再添加到暂存区），add后面加的是文件或者目录路径

​	git commit -m "注释"		将暂存区提交到版本库

​	git commit						需要添加比较长的注释时使用，执行该命令后会进入vim编辑器，可直接在编辑器中添加描述，编辑器操作： https://blog.csdn.net/qq_43432935/article/details/92013718

​	git commit -a -m "注释"	跳过git add步骤，自动把所有已经跟踪过的文件暂存起来一并提交

​	git commit -a					需要添加比较长的注释时使用

# git高层命令（分支）

​	git branch						显示分支列表

​	git branch 分支名			创建分支

​	git branch 分支名 commithash	在指定的提交对象上创建新的分支（执行后再把分支切回去就可以查看历史版本的内容了）

​	git checkout 分支名		切换分支

​	**git checkout -b 分支名**	创建并切换到该新创建的分支

​	git branch -d name		 删除分支（需要把分支切换到master才可以删除其他的分支）

​	git branch -D name		 强制删除分支

​	git log --oneline --decorate --graph --all	查看项目分叉历史

​	git config --global alias.别名 "log --oneline --decorate --graph --all"	给命令配别名

（**注意：切换分支前确保当前分支已经干净，即内容已经全部处于提交状态，否则切换分支时，未提交的文件会被一并带到切换后的分支的工作目录中，造成其他分支的污染**）

​	git merge 分支名				合并分支（合并分支前先把分支切换到master）

（**注意：若存在分叉的分支，在合并分支时可能会出现存在冲突的文件（即被两个分支同时修改），这时需要编辑冲突文件，决定哪些代码留下或者删除，然后保存到暂存区并且提交**）

## 撤销

#### 工作区

​	如何撤回自己在工作目录中的修改： git checkout --file

#### 暂存区

​	如何撤回自己在暂存区中的修改：	 git reset HEAD file

#### 版本库

​	如何改上一次提交文件的注释：		 git commit --amend

## 提交到远程仓库

git remote add origin(远程地址别名) url(ssh地址)

git push -u origin master

# 远程仓库代码克隆/合并到本地中

git clone -b 远程分支名 远程地址       下载一个完整的远程项目（如果不加-b 也就是不指定哪个分支 会默认master分支）

git fetch   												拉取远程版本库中所有有变化的分支中的内容

git merge 指定远程某分支                    合并某个拉取下来的分支中的代码