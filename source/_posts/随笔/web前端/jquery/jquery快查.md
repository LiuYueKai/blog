jQuery优势：
1、轻量级，大小只有30kb，压缩后18K。
2、强大的选择器。
          1、基本选择器
$('#id')  多个id为id的元素只取第一个
$('.class')
$('div')
$('span, #id')  选取id为id的span元素
2、层次选择器
$("div span") 选择div下的所有span元素（与下面的区别是此方式为后代，下面为子代）
$("div > span") 选择div下的为span的子元素
$(".one + div ")选择class为one的下一个div元素  可以用$(".one").next("div")替代
$("#two ~ div")选择id为two的元素后面的div兄弟元素 可以用$("#two").nextAll("div")替代
$("#two").siblings("div")代表的与two同级的其他所有div
3、基本过滤选择器
$(".menu_div:first") 样式为menu_div的第一个元素
$(".menu_div:last") 样式为menu_div的最后一个元素
$("input:not(:checked)") 查询所有未选中的input
$("tr:even") [ˈivən] 匹配所有索引值为偶数的元素，从0开始 1 3 5 7行  
$("tr:odd") [ɑd] 匹配所有索引值为奇数的元素，从0开始 2 4 6行
$("tr:eq(1)")匹配一个给定索引值的元素，第二行
$("tr.gt(0)")  greater [ɡreɪtə]匹配所有大于给定索引值的元素，第二行和第二行之后的行
$("tr.lt(2)")匹配所有小于给定索引值的元素，第一行和第二行
$(":header")选择所有header元素，包括h1 h2 h3
$(":animated") [ˈænɪmeɪtɪd] 匹配所有执行特效的元素
只有对不在执行动画效果的元素执行一个动画特效:
$("#run").click(function(){
  $("div:not(:animated)").animate({ left: "+=20" }, 1000);
});
4、内容过滤选择器
$("div:contains('john')") [kən'teɪnz] 匹配所有包含指定文本的元素
$("td:empty")匹配所有报不含子元素或者文本的空元素
$("div:has(p)").addClass("test")给所有包含 p 元素的 div 元素添加一个 text 类: 
$("td:parent")匹配含有子元素或者文本的元素，查找所有含有子元素或者文本的 td 元素:
5、可见性过滤选择器
$("tr:hidden")匹配所有不可见的 tr 元素
$("tr:visible")匹配所有可见的 tr 元素
6、属性过滤选择器
[attribute]匹配包含给定属性的元素， $("div[id]")查找所有含有 id 属性的 div 元素
[attribute=value]匹配给定的属性是某个特定值的元素,$("input[name='newsletter']")
[attribute!=value]匹配给定的属性是不包含某个特定值的元素$("input[name!='newsletter']")
[attribute^=value]匹配给定的属性是以某些值开始的元素$("input[name^='news']")
[attribute$=value]匹配给定的属性是以某些值结尾的元素$("input[name$='letter']")
[attribute*=value]匹配给定的属性是以包含某些值的元素$("input[name*='man']")
[attributeFilter1][attributeFilter2][attributeFilterN]复合属性选择器，需要同时满足多个条件时使用。$("input[id][name$='man']")
7、子元素过滤选择器
:nth-child(index/even/odd/equation)匹配其父元素下的第N个子或奇偶元素
 例子：$("ul li:nth-child(2)") 在每个 ul 查找第 2 个li:
':eq(index)' 只匹配一个元素，而这个将为每一个父元素匹配子元素。:nth-child从1开始的，而:eq()是从0算起的！
可以使用: 
nth-child(even) 
:nth-child(odd) 
:nth-child(3n) 
:nth-child(2) 


:first-child，匹配第一个子元素，':first' 只匹配一个元素，而此选择符将为每个父元素匹配一个子元素。例子：$("ul li:first-child")在每个 ul 中查找第一个 li


:last-child，匹配第一个子元素，':last' 只匹配一个元素，而此选择符将为每个父元素匹配一个子元素。例子：$("ul li:last-child")在每个 ul 中查找最后一个 li

:only-child，如果某个元素是父元素中唯一的子元素，那将会被匹配，如果父元素中含有其他元素，那将不会被匹配。例子：$("ul li:only-child")在 ul 中查找是唯一子元素的 li
8、表单选择器
名称
说明
解释
:input
匹配所有 input, textarea, select 和 button 元素
查找所有的 input 元素: 
$(":input")
:text
匹配所有的文本框
查找所有文本框 : 
$(":text")
:password
匹配所有密码框
查找所有密码框 : 
$(":password")
:radio
匹配所有单选按钮
查找所有单选按钮
:checkbox
匹配所有复选框
查找所有复选框 : 
$(":checkbox")
:submit
匹配所有提交按钮
查找所有提交按钮 : 
$(":submit")
:image
匹配所有图像域
匹配所有图像域 : 
$(":image")
:reset
匹配所有重置按钮
查找所有重置按钮 : 
$(":reset")
:button
匹配所有按钮
查找所有按钮 : 
$(":button")
:file
匹配所有文件域
查找所有文件域 : 
$(":file")
 9、表单过滤选择器
名称
说明
解释
:enabled
匹配所有可用元素
查找所有可用的 input 元素: 
$("input:enabled")
:disabled
匹配所有不可用元素
查找所有不可用的 input 元素: 
$("input:disabled")
:checked
匹配所有选中的被选中元素 ( 复选框、单选框等，不包括 select 中的option)
查找所有选中的复选框元素 : 
$("input:checked")
:selected
匹配所有选中的 option 元素
查找所有选中的选项元素 : 
$("select option:selected")

 *选择器返回结果为空的时候也不会报错。
选择器中如果碰到了. #等特殊字符通过\\转义
3、出色的DOM操作的封装。
Jquery对象：$(DOM对象)
DOM对象：$(DOM对象)[0]  或者$(DOM对象).get(0)

查找元素：通过jquery选择器
查找属性：$("#id").attr("text");
创建节点：$("<div id='id1'>文本</div>")
插入节点：
append()向每个匹配的元素内部追加内容：
HTML代码：
<p>我想说：</p>
jQuery代码：
$("p").append("<b>你好</b>");
结果：
<p>我想说：<b>你好</b></p>
appendTo()将所有匹配的元素追加到指定的元素中。实际上，使用该方法是颠倒了常规的$(A).append(B)的操作，即不是将B追加到A中，而是将A追加到B中：
HTML代码：
<p>我想说：</p>
jQuer代码：
$("<b>你好</b>").appendTo("p");
结果：
<p>我想说：<b>你好</b></p>
prepend()向每个匹配的元素内部前置内容：
HTML代码：
<p>我想说：</p>
jQuer代码：
$("p").prepend<"<b>你好</b>");
结果：
<p><b>你好</b>我想说：</p>
prependTo()将所有匹配的元素前置到指定的元素中。实际上，使用该方法是颠倒了常规的$(A).prepend(B)的操作，即不是将B前置到A中，而是将A前置到B中：
HTML代码：
<p>我想说：</p>
jQuer代码：
$("<b>你好</b>").prependTo("p");
结果：
<p><b>你好</b>我想说：</p>
after()在每个匹配的元索之后插入内容：
HTML代码：
<p>我想说：</p>
jQuer代码：
$("p").after("<b>你好</b>");
结果：
<p>我想说：</p><b>你好</b>
insertAfler()将所有匹配的元素插入到指定元素的后面。实际上，使用该方法是颠倒了常规的$(A).after(B)的操作，即不是将B插入到A后面，而是将A插入到B后面：
HTML代码：
<p>我想说：</p>
jQuer代码：
$("<b>你好</b>").insertAfter("p");
结果：
<p>我想说：</p><b>你好</b>
before()在每个匹配的元素之前插入内容：
HTML代码：
<p>我想说：</p>
jQuer代码：
$("p").before("<b>你好</b>");
结果：
<b>你好</b><p>我想说：</p>
insertBefore()将所有匹配的元素捅入到指定的元素的前面。实际上，使用该方法是颠倒了常规的$(A).before(B)的操作，即不是将B插入到A前面，而是将A插入到B前面：
HTML代码：
<p>我想说：</p>
jQuer代码：
$("<b>你好</b>").insertBefore("p");
结果：
<b>你好</b><p>我想说：</p>
删除节点：remove() empty()
复制节点：clone()   clone(true)表示复制的同时将对象的事件也进行复制
替换节点：replaceWith()    replaceAll()
$("p").replaceWith("<strong>内容</strong>") 和$("<strong>内容</strong>").replaceAll("p") 都是事先用内容替换p
包裹节点：
1.wrap()[ræp]方法：将某个节点用其他标记包裹起来。不会破坏原始文档的语义。
$(function(){
   $("strong").wrap("<b></b>");//用<b>元素把<strong>元素包裹起来
});
显示结果:
<b>
<strong title="选择你最喜欢的水果." >你最喜欢的水果是?</strong></b>
<b><strong title="选择你最喜欢的水果." >你最喜欢的水果是?</strong></b>
2.wrapAll()方法：将所有匹配的元素用一个元素来包裹。而wrap()方法则是对每个元素单独包裹。
$(function(){
   $("strong").wrapAll("<b></b>");
});
显示结果：
<b>
<strong title="选择你最喜欢的水果." >你最喜欢的水果是?</strong>
<strong title="选择你最喜欢的水果." >你最喜欢的水果是?</strong></b>
*如果strong元素中间隔着其他元素则会将strong元素移动到第一strong的位置
3.wrapInner()方法：将每一个匹配的元素的子内容(包括文本节点)用其他结构化的标记包裹起来。
$(function(){
   $("strong").wrapInner("<b></b>");
});
显示结果：
<strong title="选择你最喜欢的水果." ><b>你最喜欢的水果是?</b></strong>
属性操作：
通过attr()方法获取元素的属性
获取 img 标签 title 的值
var title = $("img").attr("title");
改变或设置 img 标签 title 的值
$("img").attr("title", "这是一幅风景画");
同时设置二个属性
$("img").attr({ src: "Images/img02.jpg", title: "这是一幅风景画" })
attr( key, function(index) ) 参数index为当前元素的索引号，整个函数返回一个字符串作为元素的值。图片在页面刷新时随机出现
$("img").attr("src", function() {
    return "Images/img0" + Math.floor(Math.random() * 2 + 1) + ".jpg";
});
 
Math.random();   [mæθ]//无参数 - 返回0和1之间的伪随机数，可能为0，但总是小于1，(0,1)
document.write(Math.random()*(20-10)+10);   //返回10-20的随机数，带多位小数
document.write(Math.random()*(n-m)+m);      //返回指定范围的随机数(m-n之间)的公式
Math.floor(x);   //x -- 为number类型的数字，返回小于等于x的最大整数
document.write(Math.floor(5.99));   [flɔr, flor] //返回 5
document.write(Math.floor(-5.99));  //返回 -6
removeAttr(); 删除元素属性
$("img").removeAttr("src");
样式操作：
$("p").click(function() {
    $(this).css("font-weight", "bold");         //字体加粗
    $(this).css("font-style", "italic");        //斜体
    $(this).css("background-color", "#eee");    //增加背景色
    $(this).attr("class","newCLass");   //修改样式
    $(this).addClass("cls1 cls2");              //同时新增二个样式类别
    $(this).toggleClass("clsImg");      [ˈtɑɡəl]        //切换样式类别，循环添加删除对应样式
    $(this).removeClass("cls1 cls2");           //同时删除二个样式类别
    $(this).removeClass();                      //删除 P 标记的所有类别
    $(this).hasClass("cs");    //是否存在样式cs，实质上等同于$(this).is(".cs");
})
$(this).toggle(function(){
               //代码1
          },function(){
               //代码2
          });
循环执行代码1和代码2
设置和获取html、文本和值
html()不传参数就是获取html否则是设置html
text()不传参数就是获取text否则是设置text
val()不传参数就是获取value否则是设置value
遍历节点：
children() 获取所有子节点
next()获取下个节点
prev() 获取前面相邻的同辈元素
siblings()获取元素前后的同辈元素
closest()从当前元素开始一直往上层查找，直到找到匹配的元素
4、可靠的事件处理机制。
事件绑定：
bind(type[,data],fun) [baɪnd]第一个参数是事件名称，第二个可选为传递给事件的额外数据对象，第三个为方法
简写方式$(this).mouseover(function(){});
合成事件：
hover(enter,leave)用于模拟鼠标悬停事件，当光标移动到元素上时调用第一个func，离开时调用第二个func。
$(document).ready(function() {
$("#orderedlist tbody tr").hover(function() {
$(this).addClass("blue");
}, function() {
$(this).removeClass("blue");
});
});
toggle(func1,func2,func3) ['tɒɡl]用于模拟鼠标连续单机事件，第一次出发func1，第二次出发func2...
如果只有func1和func2的话则循环调用func1和func2
事件冒泡：
event.stopPropagation() [ˌprɑpəˈɡeʃən]/停止事件冒泡
event.preventDefault() [prɪ'vent] /阻止默认行为
都可以使用return false来实现。
下面是jQuery事件对象可以在扩浏览器支持的属性:

属性名称	描述	举例
type
事件类型.如果使用一个事件处理函数来处理多个事件, 可以使用此属性获得事件类型,比如click.	
$("a").click(function(event) {
            alert(event.type);
            });
target
获取事件触发者DOM对象	
$("a[href=http://google.com]").click(function(event) {
            alert(event.target.href);
            });
data
事件调用时传入额外参数.	
$("a").each(function(i) {
            $(this).bind('click', {index:i}, function(e){
            alert('my index is ' + e.data.index);
            });
            });
relatedTarget [rɪˈletɪd]
对于鼠标事件, 标示触发事件时离开或者进入的DOM元素	
$("a").mouseout(function(event) {
            alert(event.relatedTarget);
            });
currentTarget
冒泡前的当前触发事件的DOM对象, 等同于this.	
$("p").click(function(event) {
            alert( event.currentTarget.nodeName );
            });
结果:P

pageX/Y
鼠标事件中, 事件相对于页面原点的水平/垂直坐标.	
$("a").click(function(event) {
            alert("Current mouse position: " + event.pageX + ", " + event.pageY );
            });
result
上一个事件处理函数返回的值	
$("p").click(function(event) {
            return "hey"
            });
            $("p").click(function(event) {
            alert( event.result );
            });
结果:”hey”

timeStamp [stæmp]
事件发生时的时间戳.	
var last;
            $("p").click(function(event) {
            if( last )
            alert( "time since last event " + event.timeStamp - last );
            last = event.timeStamp;
            });
上面是jQuery官方文档中提供的event对象的属性. 在”jQuery实战”一书中还提供了下面的多浏览器支持的属性, 时间关系我没有尝试每一个属性, 大家可以帮忙验证是否在所有浏览器下可用:

属性名称	描述	举例
altKey	Alt键是否被按下. 按下返回true	 
ctrlKey	ctrl键是否被按下, 按下返回true	 
metaKey  ['metə]	Meta键是否被按下, 按下返回true.
meta键就是PC机器的Ctrl键,或者Mac机器上面的Command键	 
shiftKey	Shift键是否被按下, 按下返回true	 
keyCode	对于keyup和keydown事件返回被按下的键. 不区分大小写, a和A都返回65.对于keypress事件请使用which属性, 因为which属性跨浏览时依然可靠.	 
which	对于键盘事件, 返回触发事件的键的数字编码. 对于鼠标事件, 返回鼠标按键号(1左,2中,3右).	 
screenX/Y	对于鼠标事件, 获取事件相对于屏幕原点的水平/垂直坐标	 
 

事件对象除了拥有属性, 还拥有事件. 有一些是一定会用到的事件比如取消冒泡 stopPropagation() 等.下面是jQuery事件对象的函数列表:

名称	说明	举例
preventDefault()
取消可能引起任何语意操作的事件. 比如<a>元素的href链接加载, 表单提交以及click引起复选框的状态切换.	
$("a").click(function(event){
            event.preventDefault();
            // do something
            });
isDefaultPrevented()
是否调用过
 

preventDefault()
方法

$("a").click(function(event){
            alert( event.isDefaultPrevented() );
            event.preventDefault();
            alert( event.isDefaultPrevented() );
            });
stopPropagation()
取消事件冒泡	
$("p").click(function(event){
            event.stopPropagation();
            // do something
            });
isPropagationStopped()
是否调用过
 

stopPropagation()
方法

$("p").click(function(event){
            alert( event.isPropagationStopped() );
            event.stopPropagation();
            alert( event.isPropagationStopped() );
            });
stopImmediatePropagation()
[ɪˈmi:diət]
取消执行其他的事件处理函数并取消事件冒泡.如果同一个事件绑定了多个事件处理函数, 在其中一个事件处理函数中调用此方法后将不会继续调用其他的事件处理函数.	
$("p").click(function(event){
            event.stopImmediatePropagation();
            });
            $("p").click(function(event){
            // This function won't be executed
            });
isImmediatePropagationStopped()
是否调用过
 

stopImmediatePropagation()
方法

$("p").click(function(event){
            alert( event.isImmediatePropagationStopped() );
            event.stopImmediatePropagation();
            alert( event.isImmediatePropagationStopped() );
            });

这些函数中  stopPropagation()  是我们最长用的也是一定会用到的函数. 相当于操作原始event对象的event.cancelBubble=true来取消冒泡.
移除事件：
unbind([type],[func])方法来移除事件
第一个参数是要移除的事件，第二个参数是要移除的方法。
（1）没有参数则移除所有事件
（2）一个参数的时候移除相应的事件对应的所有方法
（3）两个参数的时候移除特定的方法
jQuery提供了one()方法表示只触发一次，触发完了之后移除事件，与bind参数一致。
模拟操作：
trigger(type[,data])第二个参数可以传递参数
$this).trigger("click");表示模拟click操作，等同于$this).click();
triggerHandler(type[,data])模拟操作但是不会触发默认行为
其他用法：
同时绑定多个
bind("mouseover mouseout")同时绑定多个事件
命名空间
$('.class').bind('click.namespace',function(){}); / 空间事件
$('.class').trigger('click.namespace');/ 触发指定的空间事件
$('.class').unbind('click.namespace');/ 移除指定的空间事件
$('.class').unbind('.namespace');/ 移除指定空间的事件
同一事件对应不同空间
$('.class').bind('click',function(){});
$('.class').bind('click.space',function(){});
$('.class').trigger("click") /同时触发2个click
$('.class').trigger("click!") /触发不包含命名空间的事件
Jquery中的动画：
show()和hide()
fadeIn()和fadeOut()对元素的透明度进行处理
slideUp()和slideDown()  [slaɪd] 对元素的高度进行处理
自定义动画方法：
animate()：
$(this).animate({ fontSize:"50px"}, 300 ,func);  /第三个参数为动画完成之后执行的方法
$(this).animate({ width:"+=50px",height:"+=50px"}, 300);
停止动画：
stop([clearQuene][,gotoEnd])第一个参数表示是否情况未执行完的动画队列，第二个参数表示是否直接将当前动画直接跳到最后结果
判断动画是否正在执行：
$(this).is(":animated");
其他动画方法：
toggle()切换对象是否可见
slidetoggle()通过高度来切换对象是否可见
fadeTo()调整透明度  fadeTo(speed,opacity[,callback])
5、完善的Ajax。
6、不污染顶级变量。
jQuery.noConflict(); [ˈkɑnˌflɪkt]//将变量$的控制权交给其他库
          jQuery(function(){//使用jQuery
               jQuery("p").click(function(){
                    alert(jQuery(this).text());
               })
          });

          jQuery.noConflict();//将变量$的控制权交给其他库
          jQuery(function($){//使用jQuery,内部使用$
               $("p").click(function(){
                    alert($(this).text());
               })
          });

          jQuery.noConflict();//将变量$的控制权交给其他库
         (function($){//使用jQuery,内部使用$
               $("p").click(function(){
                    alert($(this).text());
               })
          })(jQuery);

          var $J = jQuery.noConflict();//将变量$的控制权交给其他库并且使用$J作为关键字
          $J(function(){//使用$J
               $J("p").click(function(){
                    alert($J(this).text());
               })
          });
7、出色的浏览器兼容。
8、链式操作方式。
9、隐式迭代。
     当用jQuery找到带有“.myClass”类的全部元素，然后隐藏它们时，无需循环遍历每一个返回的元素。相反，jQuery的方法都被设计成自动操作对象集合，而不是单独的对象，这使得的大量的循环结构变得不在必要，从而大幅的减少代码量。
10、行为层和结构层的分离。
     将元素和事件分隔开
11、丰富的插件支持。
12、完善的文档。
13、开源。

jQuerydom渲染完成之后的事件的写法：

来源网址： http://www.w3school.com.cn/jquery/event_ready.asp
$(document).ready(function)

$().ready(function)

$(function)


window.onload 是当所有元素加载完成之后处理，而上面的处理时在dom树构建完成之后执行，此时可能元素还未加载完成，有可能宽高无法获取

$(window).load(function)  /此处理会等到所有元素加载完成之后执行

window.onload只能加载一次，juqery的ready处理可以加载多次。