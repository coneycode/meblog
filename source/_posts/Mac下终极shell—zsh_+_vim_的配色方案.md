title: Mac下终极shell—zsh + vim 的配色方案
keywords: Mac 苹果 终端 terminal gengbiao.me 程序员 
descripation: 做一名文艺的程序员
date: 2014-09-22
categories:
- Mac
	
tags:
- Vim 
- terminal 

---------
#Mac下 终端 + vim 的配色方案

前两天电脑挂掉了，重新配置了工作环境，顺手记录一下。
##终端的配色
-------先放着。。明天补。。-_-!
国庆本来打算整理下这些东西，无意间发现了zsh这货，把shell更换成zsh后发现终端变得
好迅速。
##什么是zsh
好吧，想知道这个，首先要明白什么是shell
###什么是shell
shell是Linux/Unix的一个外壳，你理解成衣服也行。它负责外界与Linux内核的交互，接收
用户或其他应用程序的命令，然后把这些命令转化成内核能理解的语言，传给内核，内核是
真正干活的，干完之后再把结果返回用户或应用程序。
想查看本机有多少shell，可以使用指令
```
cat /etc/shells
```
显示如下
![shells List](http://coney.qiniudn.com/mac_5FAE29D3-8FD0-4FF2-923C-77388C6CD0FD.png?attname=&e=1412860785&token=gJq7XMKe61C7zF73uUsV1e9QYqD3-fJSyQAAZZZr:By1m3MYhwz5tTZjOpoyZyZLa0WI)
这都不是重点，重点是zsh这个shell
目前常用的 Linux 系统和 OS X 系统的默认 Shell 都是 bash，但是真正强大的 Shell 是
深藏不露的 zsh， 这货绝对是马车中的跑车，跑车中的飞行车，史称『终极 Shell』，但
是由于配置过于复杂，所以初期无人问津，很多人跑过来看看 zsh 的配置指南，什么都不
说转身就走了。直到有一天，国外有个穷极无聊的程序员开发出了一个能够让你快速上手的
zsh项目，叫做「oh my zsh」，Github 网址是：
https://github.com/robbyrussell/oh-my-zsh。  这玩意就像「X天叫你学会 C++」系列，可
以让你神功速成，而且是真的。
##安装zsh
这里只写出mac的安装方法，其他方法可以看github的主页。
自动安装：
```
wget https://github.com/robbyrussell/oh-my-zsh/raw/master/tools/install.sh -O -| sh
```
手动安装：
```
git clone git://github.com/robbyrussell/oh-my-zsh.git ~/.oh-my-zsh
cp ~/.oh-my-zsh/templates/zshrc.zsh-template ~/.zshrc
```
然后重新打开一个终端窗口默认shell就变成zsh了。
cool！
##配置zsh
zsh 的配置主要集中在用户当前目录的.zshrc里，用 vim 或你喜欢的其他编辑器打开
.zshrc
需要注意的是,以前用过shell的大家应该都用过`.bash_profile`,这里其实`.zshrc`跟
`.bash_profile`本质上是一样的，可以把代码直接粘贴过来。然后附录一些个人认为比较
好用的配置。
```
alias cls='clear'
alias ll='ls -l'
alias la='ls -a'
alias vi='vim'
alias javac="javac -J-Dfile.encoding=utf8"
alias grep="grep --color=auto"
alias -s html=vi   # 在命令行直接输入后缀为 html 的文件名，会在 vim 中打开,如果想用TextMate打开可以将vi改成mate
alias -s rb=vi     # 在命令行直接输入 ruby 文件，会在 vim 中打开
alias -s py=vi       # 在命令行直接输入 python 文件，会用 vim 中打开，以下类似
alias -s js=vi
alias -s c=vi
alias -s java=vi
alias -s txt=vi
alias -s gz='tar -xzvf'  #表示自动解压后缀为 gz 的压缩包。
alias -s tgz='tar -xzvf'
alias -s zip='unzip'
alias -s bz2='tar -xjvf'
```

也可以修改主题，默认主题是
```
ZSH_THEME=”robbyrussell”
```
##插件zsh
在这里就说一个必装的插件。
autojump：zsh 和 autojump 的组合形成了 zsh 下最强悍的插件。
Mac安装可以使用brew
```
brew install autojump
```
注意，虽然是自动安装，但是可能因为权限问题，还需要自己手动在`.zshrc`里添加如下代
码,而且Mac跟linux的指令还不太一样，Mac的指令如下所示：
```
[[ -s `brew --prefix`/etc/autojump.sh  ]] && . `brew --prefix`/etc/autojump.sh
```
Linux安装的话需要先clone项目。
```
git clone git://github.com/joelthelion/autojump.git
```
然后找到目录，执行
```
./install.py
```
最后需要自己手动在`.zshrc`里添加如下代码：
```
[[ -s ~/.autojump/etc/profile.d/autojump.sh  ]] && .~/.autojump/etc/profile.d/autojump.sh
```
大功告成。
关于终端配色与vim配色，下次单开一章来写。
