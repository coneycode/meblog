title: coney主题的博客颜色更改
keywords: hexo theme 主题 gengbiao.me 程序员 颜色
descripation: hexo的主题coney说明
date: 2014-10-16
categories:
- hexo
tags:
- 主题
- DIY

---


#coney主题
因为最近一直在不断更新，建议你们可以选择star[我的主题](https://github.com/coneycode/coney)，及时得到我的更新通知。
最后更新时间： 2014-10-18
已经安装的朋友可以选择升级主题:

```
cd themes/coney
git pull origin master
```

##主题颜色更改
###依赖
目前官方还未支持十六进制颜色与String值的转换,所以需要手动添加依赖包，本人已经向作者提交了issue，该问题估计稍后会解决

```
##在博客的目录下输入下面指令
cd node_modules/hexo-renderer-stylus 
sudo npm install stylus@0.49.2  #根据系统文件的权限不同，有的不需要加sudo,这里默认没有写权限，需要用管理员权限执行指令
```

###更改主题颜色

在hexo博客目录下的`_config.yml`的 `theme_color`下

```
theme_color: 
    background: "#dddddd"  #博客背景
    font: "#817c7c"        #博客字体
    theme: '#ea6753'       #博客主题颜色
    footer: "#ffffff"      #博客页脚颜色
```

###更改百度分享颜色

```
baidu_share:¬
   enable: true
   color: 4 ##百度分享栏的颜色设置，一共有九种颜色,详情见下图
```

![baidu_item_color](img/hexo/baidu_share.png)

按图示，从左到右分别是
第一行 0 | 1 | 2 | 3 | 4
第二行 5 | 6 | 7 | 8

稍后还会公开更多的颜色配置给大家。