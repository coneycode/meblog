title: coney主题介绍
keywords: hexo theme 主题 gengbiao.me 程序员
descripation: hexo的主题coney说明
date: 2014-10-13
categories:
- hexo
tags:
- 主题

---

# coney主题介绍
coney主题是[Hexo](http://hexo.io)的一款主题.基于[pacman主题](https://github.com/A-limon/pacman)的样式改写的。支持不同分辨率的使用。

因为最近一直在不断更新，建议你们可以选择star[我的主题](https://github.com/coneycode/coney-hexo-theme)，及时得到我的更新通知。
最后更新时间： 2014-10-18
已经安装的朋友可以选择升级主题:
```
cd themes/coney
git pull origin master
```
##安装
###安装
```
 git clone -b master https://github.com/coneycode/coney themes/coney
```
**注意：Coney 要求至少在 Hexo 2.4.5 以上.** 
###使用
在hexo博客目录下的` _config.yml`里将 `theme` 设置成 `coney`.
```
theme: coney
```
###升级
```
cd themes/coney
git pull origin master
```

**注意升级前备份好`theme/coney/_config.yml`以防自己的配置丢失** 
##配置

配置文件在 `/themes/coney/_config.yml`.

```
####菜单
menu:
  首页: /
  归档: /archives
## 使用标签或者分类需要在你的博客根目录下的`../source`中创建两个文件夹`tags`和`categories`.
## 然后分别在文件夹下创建文件`index.md`.内容如下，可以直接复制粘贴，注意去掉##：
##(categories中将tags换成 categories)
## layout: tags
## title: tags 
## ---
#### 平台，即头像下方的需要显示的数据，不想添加的去掉就好
widgets: 
- category  - ##分类使用标签或者分类需要在你的博客根目录下的`../source`中创建两个文件夹`tags`和`categories`.然后分别在文件夹下创建文件`index.md`.内容如下，(categories中将tags换成 categories)可以直接复制粘贴：
layout: tags
title: tags 
---
- tag       - ## 标签
- links     - ## 友情链接,你可以修改自己的links在 `/layout/_widget/links.ejs`默认为本人的博客和hexo主页.
- rss       - ## rss订阅
- tagcloud  - ## 标签云
#### RSS
rss:  atom.xml ## 即你本人的rss地址名称，一般不用更改。
#### Image
imglogo:    ## 即你名称左边的logo是否显示，本人觉得logo略鸡肋，但是鉴于每个人的审美不同，保留此功能.默认关闭
  enable: false            ##默认关闭           
  src: img/logo.svg        ##推荐使用`.svg`或者`.png` 将图片放置在 `/coney/source/img`.
favicon: img/favicon.ico   ## 即浏览器标签上显示的图片，大小: 32px*32px,`.ico`  将图片放置在 `/coney/source/img`.
#### 作者头像
author_img_enable: true ## 是不是显示作者的头像
author_img: img/coney.png ## 作者头像，size: 220px*220px.
#### 字体
ShowCustomFont: true  ## 你可以自定义你的字体,路径在 `/coney/source/css/variable.styl` 和 `/coney/source/css/font.styl`.
#### 目录
toc:
  article: true   ## 是不是在文章中显示目录.如果某一篇文章中你不想显示侧边栏，可以在正文之前 `front-matter`中添加属性`toc: false`.
  aside: true     ## 是不是在侧边栏中显示目录.
#### Fancybox
fancybox: false ##默认关闭，如果你使用Hexo经常发表Gallery类型的文章，那么请设置为true（同时需要复制fancybox.js到你的博客目录下scripts文件夹中）。
#### 作者信息，就是填写一些作者的相关信息
author:
  google_plus:    ## e.g. 116338260303228776998 指向 https://plus.google.com/u/0/116338260303228776998
  weibo:      coneylife ## e.g. 436062867 指向 http://weibo.com/436062867
  twitter:    ## e.g. gengbiaosky 指向 https://twitter.com/yangjiansky
  github:     coneycode ## e.g. coneycode 指向 https://github.com/coneycode
  facebook:   ## e.g. gengbiao 指向 https://favebook.com/yangjian
  tsina:      1005055274569156 ## e.g. 1664838973  这个是你的微博地址，在分享中其他人会自动@你。
  zhihu:     # coneylife, 现在知乎还没有icon，我已经提交了icon申请到Font-Awesome，静候佳音，我会第一时间更新.
#### 评论
duoshuo: 
  enable: true  ## 多说评论系统，系统默认disqus，但是大陆不好用你懂的。。
  short_name: coney ## 评论时显示的名字.
#### 分享
jiathis:
  enable: false ##  加网分享系统。默认关闭，因为主题已经内置了原生的分享功能。
  id:    ## e.g. 1501277 加网ID. 
  tsina: ## e.g. 1664838973 微博ID,会被用在分享功能中自动@你.
####百度分析
baidu_analytics:
  enable: true
  id: 391982416296a0d54221f59fe35250d4 # 你的百度分析ID
####百度分享
baidu_share:
  enable: true
  color: 4 ##百度分享栏的颜色设置，一共有九种颜色，详情在最后面的附录`coney主题的博客颜色更改`
####主题颜色修改,目前官方还未支持十六进制颜色与String值的转换
####想更改颜色需要查看最后面附录的`coney主题的博客颜色更改`¬
theme_color: 
    background: "#dddddd"  #博客背景
    font: "#817c7c"        #博客字体
    theme: '#ea6753'       #博客主题颜色
    footer: "#ffffff"      #博客页脚颜色
####百度站内搜索 
baidu_search:
  enable: true
  id: '2049782880735612718' ##你的百度站内搜索ID
  site: http://search.baidu.com/cse/search  #http://search.gengbiao.me/cse/search，百度站内搜索url，你可以用自己的地址指向百度默认站内搜索后更改此处。
####谷歌分析
google_analytics:
  enable: true
  id:   ## e.g. UA-55273525-1 谷歌分析ID.*Google Analytics已经升级到了Universal Analytics。请先前往后台升级你的Google Analytics版本后再启用追踪代码,链接地址在下面。
  site: ## e.g.gengbiao.me  谷歌分析的站点，默认会添加本博客。
####background music 
background_music:
  enable: false
  src: 
#### 谷歌站内搜索
google_cse: 
  enable: false  
  cx: 010584917530731754670:91c2z8qybp0  ## e.g. 010584917530731754670:91c2z8qybp0 你的谷歌搜索ID，但是在大陆经常不能用你懂的。https://www.google.com/cse/ 如果开启此功能，需要在博客根目录的 '/source'中创建文件夹 '/search'，然后在文件夹中创建"index.md"文件。文件内容如下：
layout: search 
title: search
---
```
附录：
[谷歌分析升级详情](https://developers.google.com/analytics/devguides/collection/upgrade/?hl=zh_CN)
[coney主题的博客颜色更改](http://gengbiao.me/2014/10/16/coney%E4%B8%BB%E9%A2%98%E7%9A%84%E5%8D%9A%E5%AE%A2%E9%A2%9C%E8%89%B2%E6%9B%B4%E6%94%B9/)