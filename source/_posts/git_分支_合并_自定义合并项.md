title: git_分支_合并_自定义合并项
keywords: git branch 分支 merge ignore file 忽略 文件 合并
descripation: git branch 分支 merge ignore file 忽略 文件 合并
date: 2014-10-16
categories:
- 技术-Git
	
tags:
- git

---------


#git 分支

##github 分支的相关指令

```
git branch #列出本地存在的分支
git branch -r #列出远程存在的分支
git branch -a #列出远程和本地存在的分支
git branch <文件名> #创建一个新分支，比如 git branch aa ,创建了一个aa的分支.
git branch -m oldbranch newbranch #重命名分支，如果需要强制重命名用大写的-M.
git branch -d branchname #删除branchname分支,如果需要强制重命名用大写的-D.
git branch -d -r branchname #删除远程branchname分支
```
###github 分支的切换

```
git checkout branchname #切换到某分支下，如 git checkout aa,即切换到了aa 分支下
git checkout -b newbranch # 创建新分支，并跳到该分支下
```
搞定。
###github 分支的合并
```
git merge branchname #把当前分支与指定分支合并 
    e.g. git merge aa #将当前分支与分支名为aa的分支合并
git merge branchname1 branchname2 #把当前分支与指定多个分支合并 
    e.g. git merge aa bb #将当前分支与分支名为aa和bb的的分支合并
```
###忽略某些文件的合并
```
git checkout aa  #切换到分支aa
vim .gitattributes #创建.gitattributes文件并用vim打开
config.yml merge=ours. #将前面这句话写入.gitattributes
:wq #在vim的命令行下敲入:wq, 保存并退出vim.
git add .gitattributes  #add 该文件
git commit -m "your commit" #commit 该文件
```
`config.yml merge=ours`这句话的意思是当合并时，如果与其他分支的config.yml文件发
生冲突，取消合并，使用当前分支下的config.yml文件.
然后切换到另一个想要合并的分支B中重复刚才的操作。
最后
```
git merge 分支名

```
大功告成!

###合并指定文件
```
git checkout branchname -- file1 file2 etc #合并分支里制定的文件
    e.g. git checkout aa -- file1 file2 #将当前分支的file1 file2 与分支名为aa下的file1 file2文件合并
```




