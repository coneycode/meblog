title: git 常见问题汇总
keywords: Mac 苹果 终端 terminal gengbiao.me 程序员 git add contributions calendar 
descripation: 做一名文艺的程序员
date: 2014-09-22
categories:
- 技术-Git
	
tags:
- git

---------


#git 常见问题汇总

##github Contributions Calendar不记录
一开始为了方便直接用ssh登陆了，结果github发现我push的账号email跟我的github上public的email不一样，果断悲剧了。就是calendar这个东西没有提交动态。。
![github_calendar](http://coney.qiniudn.com/blog_github_calendar.png?download&e=1411476009&token=gJq7XMKe61C7zF73uUsV1e9QYqD3-fJSyQAAZZZr:5Mfsi5XN6P96jPe1u3gzpFy5wJw)

于是

```
git config user.email
```
这个时候当然什么都没有，最开始登陆是直接ssh登陆的，没有config这些东西。
然后

```
git config user.email "username@email.com"
```
搞定。
##github add 的不同形式
git add命令主要用于把我们要提交的文件的信息添加到索引库中。当我们使用git commit时，git将依据索引库中的内容来进行文件的提交。
基本上会用到下面的几个命令：

git add xxx    | description |
---------------|-------------|
git add --all|第一次提交的时候需要使用git add --all,将数据初始化到索引库中。|
git add path|通过git add <path>的形式把我们<path>添加到索引库中，<path>可以是文件也可以是目录。git不仅能判断出<path>中，修改（不包括已删除）的文件，还能判断出新添的文件，并把它们的信息添加到索引库中。|
git add -u [<path>] | 把<path>中所有tracked文件中被修改过或已删除文件的信息添加到索引库。它不会处理untracted的文件。省略<path>表示.,即当前目录。|
git add -A [<path>] | 表示把<path>中所有tracked文件中被修改过或已删除文件和所有untracted的文件信息添加到索引库。省略<path>表示.,即当前目录。|
git add -i  |通过git add -i [<path>]命令查看<path>中被所有修改过或已删除文件但没有提交的文件，并通过其revert子命令可以查看<path>中所有untracted的文件，同时进入一个子命令系统。（见下图）|

![github_add - i](http://coney.qiniudn.com/blog_git_add_-i.png?download&e=1411476009&token=gJq7XMKe61C7zF73uUsV1e9QYqD3-fJSyQAAZZZr:nwbo1MrbypVQz7xzFwgVE8iPuTE)