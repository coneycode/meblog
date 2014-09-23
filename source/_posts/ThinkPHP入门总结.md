title: ThinkPHP学习总结
keywords: ThinkPHP 入门 PHP CMS DUXCms 程序员 
descripation: ThinkPHP 入门 PHP CMS DUXCms 程序员 
date: 2014-09-05
categories:
- 技术-PHP
tags:
- php

---

#ThinkPHP学习总结

最近工作需要，要用PHP写目前项目的后台，因为之前一行PHP代码都没写过，只能从头开始读代码，找了个框架，thinkPHP，现将从零开始学习的心得分享如下。

thinkPHP框架概况


	├─ThinkPHP.php     框架入口文件
	├─Common 框架公共文件
	├─Conf 框架配置文件
	├─Extend 框架扩展目录
	├─Lang 核心语言包目录
	├─Library 核心类库目录
	│  ├─Behavior 核心行为类库
	│  ├─Core 核心基类库
	│  ├─Driver 内置驱动
	│  │  ├─Cache 内置缓存驱动
	│  │  ├─Db 内置数据库驱动
	│  │  ├─TagLib 内置标签驱动
	│  │  └─Template 内置模板引擎驱动
	│  └─Template 内置模板引擎
	└─Tpl 系统模板目录

基于thinkPHP做二次开发的时候主要使用的`Library`目录下`Driver`的东西。也有可能使用`Template`,写到`/Taglib`里面，定义自己的模板类。利与开发。
####比如想写一个formrow，如果直接使用html写的话，写法如下：
   
    <div class="formitm">
       <label class="lab">title</label>
          <div class="ipt">content<p class="help-block">tip</p></div>
    </div>
####采用模板写法如下：
新建一个文件MyTpl.class.php

	public function _formrow($tag,$content) {
        $title      = $tag['title'];                //标题
        $tip      = $tag['tip'];                //提示信息
        $html = '
        <div class="formitm">
            <label class="lab">'.$title.'</label>
            <div class="ipt">
                '.$content.'
                <p class="help-block">'.$tip.'</p>
            </div>
        </div>';
        return $html;
    }
以后可以直接使用下面的字段达到上面的效果。
	
	<MyTpl:formrow title="" tip="" ></admin:formrow>
	
本质是一个映射的思想。使程序结构更清晰，代码更简洁统一。

以实例叙述，Demo如下：
   首先你创建新的文件夹应该包含如下几个文件夹：
   
    ├─View        表示层
	├─Controller  控制层  use Think\Controller
	├─Model       数据层  use Think\Model
	├─Conf        配置文件
	├─index.html  默认的入口index.html文件
	├─Common      非必要，但是可以将公用的文件放到这里面
	
###View层包含的为html代码，并可以直接使用已存在的模板。
* 需要提交的数据直接写在form表单里面，action后写接收响应的Controller,使用方法`U`定位地址。比如`{:U()}`指提交到了本地，`{:U(“admin/getInfo”)}`就是提交到admin文件里的getInfo方法。
* 值得注意的是，在这里不需要写Controller，是因为U方法会自动解析，直接定位到adminController方法中去，所以真正的物理文件命名不应该是admin，而是adminController，
* 关于View层其他的不再过多叙述。
Controller层为逻辑控制层，负责MV之间的沟通。
Modle层是数据持久层。
MVC模式在ThinkPHP中的数据交互主要通过`_POST` `Request`，鉴于PHP中前端的_POST请求可以在任何地方被捕捉到。所以MVC通信过程中只需要调用方法，不需要传递数据。

---
- - - - 

###Controller层和Model包含的为php代码。
* Controller层主要是对方法的调用，包含了大量的工程中绝大部分的逻辑代码。当调用Model时使用使用方法`M`定位地址。具体用法与上文`U`类似。
* Model层不需要编写真正的sql语句，CURD都已经封装的很完备。用如下语句进行举例。
		
		$this->table("__CONTENT__ as A")
                    ->join('__CONTENT_ARTICLE__ as B ON A.content_id = B.content_id')
                    ->join('__CATEGORY__ as C ON A.class_id = C.class_id')
                    ->where($where)
                    ->order($order)
                    ->count();
  选定table，thinkPHP的格式为`_table名称_`,如 `table("__CONTENT__ as A")`即选择了数据库中名为CONTENT的table。可以根据自己喜好添加where，order等语句，不添加默认为空。
  
  **需要注意的是** ThinkPHP在执行table以后，关于CURD的操作就缺省针对于之前的那个table，不再重新选择。而且如果不做映射处理的话，默认`_POST`里的字段名与table中的字段名是相同的，即KEY-VALUE在`table`中和`_POST`中是一致的。
  
  关于这部分，剩下的不再叙述。
###ThinkPHP新手，尤其是没有学过PHP的新手容易疑惑的几个地方：
> 数据去哪了?如何获取到的数据？

		首先，在PHP中_POST请求可以在后台的任何地方接收到，action只是选定了提交form表单后执行哪个类，并非把数据提到到了这个类里面，其他类不可以使用。
		其次，在thinkPHP的MVC层中，如果不做自定义的映射处理，默认前台form中的{name,value}直接对应数据库中table的{key,value}。所以在数据form激发action的时候就数据已经送达到了后台的每一个地方，无论Controller还是Model都可以使用。
> thinkPHP伪静态的具体效果，如何根据url解析到目的地址？

		thinkPHP采用了伪静态效果，伪静态有利于搜索引擎的收录,能够增加网站的优化效果。而且跟人觉得用户友好度较好。	至于如何根据url解析到正确的目的地址，以如下代码示例。
		比如url：http://serverName/index.php/Blog/read/，就定位到Blog这个文件下read方法了。
		比如方法如下：
			public function read($id=0){
    			echo 'id='.$id;
 			}
 		则访问后会显示0.
 **值得注意的地方是**`read($id=0)`里面给id一个缺省值，如果没有这个缺省值，则访问时会报错。如果在`/read/`后加参数，比如`http://serverName/index.php/Blog/read/5`,则显示5.
 
 	其实也可以开启路由功能，自定义url解析规则，自己定义url的写法。这里不详细展开。
 



