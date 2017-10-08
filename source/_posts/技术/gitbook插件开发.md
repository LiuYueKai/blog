# gitbook插件开发
本次主要记录开发gitbook插件的一些记录，后续会根据开发进度不断完善。以下文档内容可参考：
https://github.com/iuap-design/gitbook-plugin-iuap-design
## 创建插件
1.创建仓库名字以gitbook-plugin-开头，后面为插件的具体名称
例如：gitbook-plugin-iuap-design
2.再package.json中需要添加
​	
	"engines": {
	    "gitbook": ">1.x.x"
	},

之后gitbook才能识别此插件

## 插件核心文件说明
### index.js


	module.exports = {
	    book: {
	        assets: './book',
			js: [
	            'iuap-desigin.js'
		    ],
	        css: [
	            'iuap-desigin.css'
	        ]
	    },
	    hooks: {    
	        "page": function (page) {             
			    _.forEach(page.sections, insertAnchors);
		        return page;
		    }
		}
	};

book下配置内容会出现在最终的产出内容中，并且在浏览页面时才执行。
hooks下配置hook，此例中的page可以获取gitbook插件生成的默认section标签中的内容，同时对此部分内容进行编辑修改，影响最终产出的html文件。

### package.json
插件的配置信息。详细说明参考：
http://blog.csdn.net/zhangjk1993/article/details/50380403
## 插件使用
在book.json中的pulgins属性中添加创建的插件
例如：
​	
	"plugins":[
		"iuap-design"
	]

## 插件调试
### book内容调试
在book.json中添加插件执行执行
​		
	$ gitbook serve
或者
​	
	$ gitbook build

gitbook插件会根据book.json中的ouput产出html文件。进入此文件夹通过以下路径

	gitbook\plugins\gitbook-plugin-iuap-design
可找到插件index.js中module.exports下book中配置的js及css，修改js及css刷新页面即可看到效果。

### hooks内容调试

此部分内容只能通过重新执行
​	
	$ gitbook serve
或者
​	
	$ gitbook build
来进行调试。

以上内容只是目前开发过程的一些总结，有错误的地方欢迎提出来。



# 终极大法

直接修改模板文件，插件中theme/templates下存放的是模板，page.html为为最终的模板。

# 部分代码说明

plugin.js: Plugin.prototype.callHook = function(name, data) { 这里调用的hook

https://github.com/gitbook-plugins/gitbook-plugin-search-pro 有init以及参数设置

https://developer.gitbook.com/plugins/hooks.html


gitbook获取参数的方式
1、"body:start": function(current) {
            /* header */
            console.log(this.options.pluginsConfig['iuap-design']['title'])
2、gitbook.events.bind('start', function (e,obj) {
        console.log(obj['iuap-design'].title)
    });