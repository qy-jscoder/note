[TOC]- jQuery
- [一、jQuery的基本使用](#一jquery的基本使用)
  - [1.jQuery核心函数](#1jquery核心函数)
  - [2.jQuery核心对象](#2jquery核心对象)
  - [3.jQuery函数的使用](#3jquery函数的使用)
  - [4.jQuery对象的使用](#4jquery对象的使用)
- [二、选择器](#二选择器)
  - [1.选择器的说明](#1选择器的说明)
  - [2.基本选择器](#2基本选择器)
  - [3.层次选择器](#3层次选择器)
  - [4.过滤选择器](#4过滤选择器)
  - [5.表单选择器](#5表单选择器)
- [三、属性](#三属性)
- [四、css](#四css)
- [五、位置](#五位置)
- [六、尺寸](#六尺寸)
  - [1.内容尺寸](#1内容尺寸)
  - [2.内部尺寸](#2内部尺寸)
  - [3.外部尺寸](#3外部尺寸)
- [七、jQuery对象的筛选](#七jquery对象的筛选)
- [八、jQuery对象的查找](#八jquery对象的查找)
- [九、jQuery文档操作](#九jquery文档操作)
  - [1.元素内部插入：](#1元素内部插入)
  - [2.元素外部插入：](#2元素外部插入)
  - [3.元素替换：](#3元素替换)
  - [4.元素删除：](#4元素删除)
- [十、jQuery事件处理](#十jquery事件处理)
  - [1.各个常用事件](#1各个常用事件)
  - [2.mouseover和mouseenter的区别](#2mouseover和mouseenter的区别)
  - [3.事件委派/委托](#3事件委派委托)
- [十一、jQuery内置动画](#十一jquery内置动画)
  - [1.内置的动画](#1内置的动画)
  - [2.自定义动画](#2自定义动画)
- [十二、jQuery多库共存](#十二jquery多库共存)
- [十三、区分onload和ready](#十三区分onload和ready)
  - [1.window.onload](#1windowonload)
  - [2.$(document).ready()](#2documentready)
- [十四、jQuery插件](#十四jquery插件)
  - [1.扩展$全局对象的方法](#1扩展全局对象的方法)
  - [2.扩展jQuery对象的方法](#2扩展jquery对象的方法)
  - [3.上述两种的例子](#3上述两种的例子)
- [注意点](#注意点)
  - [1.伪数组](#1伪数组)
  - [2.this和$(this)](#2this和this)



## 一、jQuery的基本使用

jQuery的优点：

（1）链式调用

（2）读写二合一

（3）隐式迭代

（4）编码函数化

### 1.jQuery核心函数

使用jQuery核心函数：$（）/jQuery（）

jQuery库向外直接暴露的就是$/jQuery（即函数）

引入jQuery库后，直接使用$即可

当函数用：$（xxx）

### 2.jQuery核心对象

简称jQuery对象

得到jQuery对象：执行jQuery函数返回的就是jQuery对象

使用jQuery对象：$obj.xxx（）

### 3.jQuery函数的使用

作为函数使用：

$（param）

（1）参数为函数：当DOM加载完成后，执行此回调函数，相当于window.onload=function(){ }

（2）参数为选择器字符串：查找所有匹配的标签，并将它们封装成jQuery对象

（3）参数为DOM元素：将dom元素对象封装成jQuery对象

（4）参数为HTML标签字符串：创建标签对象并封装成jQuery对象

作为对象使用：

（1）$.each（）：隐式遍历数组，参数1为遍历对象，参数2为回调函数（回调函数内的参数1为index索引，参数2为item数组索引对应值）

若遍历对象为数组，则遍历的是	索引和索引对应的数组值

若遍历对象为Object对象，则遍历的是	属性名和其对应的属性值(包括方法)

（2）$.trim（str）：去除两端的空格，参数为指定字符串

（3）$.type（obj）：得到数据的类型

参数为要获取类型的数据

（4）$.isArray（obj）：判断是否是数组

（5）$.isFunction（）：判断是否是函数

（6）$.paraseJSON（json）：解析json字符串转换为js对象/数组

~~~js
var json='{"name":"Tom","age":12}';
console.log($.parseJSON(json));
//打印结果：
//{name:"Tom",age:12}（是一个Object对象）
~~~

### 4.jQuery对象的使用

jQuery对象  即为   执行jQuery函数返回的对象

jQuery对象是一个包含所有匹配的任意多个dom元素的  伪数组对象（可能只有一个）

有length、index（）、each（）等属性或方法

和js原生元素标签一样，都由[index]

~~~js
//打印同标签数目
var $a=$("button");
console.log("一共有"+$a.length+"个按钮");
//打印第2个标签的文本
console.log($a[1].innerHTML);
//遍历标签的文本
$a.each(function(index,domElement){
    console.log(index,this.innerHTML+" ");
})
//打印指定的元素的索引
console.log($("#btn3").index());

//打印结果：
/*
一共有5个按钮
测试2
0 "测试1 "
1 "测试2 "
2 "测试3 "
3 "测试4 "
4 "测试5 "
2
*/
~~~

## 二、选择器

### 1.选择器的说明

选择器只是一个有特定语法规则的字符串，没有实质用处

它的基本语法规则使用的就是CSS的选择器语法，并对基进行了扩展

只有调用$（），并将选择器作为参数传入才能起作用

$（selector）作用：

​	根据选择器规则在整个文档中查找所有匹配的标签的数组，并封装为对象

### 2.基本选择器

类选择器、元素选择器、id选择器、类选择器、通配选择器（ *{} ）、伪类选择器

~~~js
//选择id为div1的标签
$("#div1").css("background-color","red");
//选择所有的div标签
$("div").css("background-color","blue");
//选择所有的class属性为box的元素
$(".box").css("background-color","yellow");
//选择所有的div和span标签
$("div,span").css("background-color","green");
//选择所有的class属性为box的div元素
$("div.box").css("background-color","brown");
~~~

### 3.层次选择器

元素	元素：表示给定的祖元素下的所有满足条件的后代元素

元素>元素：表示给定父元素下的所有满足条件的子元素

元素+元素：表示选定满足条件的元素后紧挨着的一个元素

元素1~元素2：表示元素1后的所有满足元素2条件的元素（可以用*表示）

~~~js
//选中ul下的所有的span
$("ul span").css("background-color","red");
//选中ul下的所有的子元素span
$("ul>span").css("background-color","red");
//选中class为box的下一个li
$(".box+li").css("background-color","red");
//选中ul下的class为box的元素后面的所有兄弟元素
$("ul .box~*").css("background-color","red");
~~~

### 4.过滤选择器

| [:first](selector_first.asp.htm) | $("p:first") | 第一个 <p> 元素    |
| -------------------------------- | ------------ | ------------------ |
| [:last](selector_last.asp.htm)   | $("p:last")  | 最后一个 <p> 元素  |
| [:even](selector_even.asp.htm)   | $("tr:even") | 所有偶数 <tr> 元素 |
| [:odd](selector_odd.asp.htm)     | $("tr:odd")  | 所有奇数 <tr> 元素 |

| [:eq(*index*)](selector_eq.asp.htm)                          | $("ul li:eq(3)")        | 列表中的第四个元素（index 从 0 开始）             |
| ------------------------------------------------------------ | ----------------------- | ------------------------------------------------- |
| [:gt(*no*)](selector_gt.asp.htm)                             | $("ul li:gt(0)")        | 列出 index 大于 3 的元素                          |
| :gt(no)                                                      | $("ul li:gt(0):lt(2)")  | 列出 index大于 0 小于 2的元素（第二和第三个元素） |
| [:lt(*no*)](selector_lt.asp.htm)                             | $("ul li:lt(3)")        | 列出 index 小于 3 的元素                          |
| :not(*selector*)                                             | $("input:not(:empty)")  | 所有不为空的 input 元素                           |
| :not(*selector*)                                             | $("input:not(.box)")    | 所有class属性不为box的input元素                   |
| :contains(text)                                              | $("div:contains(“BB”)") | 所有内容为BB的div元素                             |
| :hidden                                                      | $("div:hidden")         | 所有隐藏的div元素                                 |
| :visible                                                     | $(":visible")           | 所有可见的元素                                    |
| [[*attribute*\]](selector_attribute.asp.htm)                 | $("div[title]")         | 所有带有title属性的div元素                        |
| [[*attribute*=*value*\]](selector_attribute_equal_value.asp.htm) | $("div[title=hello]")   | 所有title属性的值为hello的div元素(value引号随意)  |
| [[*attribute*=*variable*\]](selector_attribute_equal_value.asp.htm) | $("div[title=‘+abc+’]") | 所有title属性的值为abc变量的div元素               |

注：多个过滤选择器不是同时执行的，而是依次执行

### 5.表单选择器

| [:enabled](selector_input_enabled.asp.htm)   | $(":enabled")          | 所有激活的 input 元素               |
| -------------------------------------------- | ---------------------- | ----------------------------------- |
| [:disabled](selector_input_disabled.asp.htm) | $(":disabled")         | 所有禁用的 input 元素               |
| :text:disabled                               | $(":text:disabled")    | 所有不可用的type为文本的input的元素 |
| [:selected](selector_input_selected.asp.htm) | $(":selected")         | 所有被选取的 input 元素             |
| [:checked](selector_input_checked.asp.htm)   | $(":checked")          | 所有被选中的 input 元素             |
| :checkbox:checked                            | $(":checkbox:checked") | 所有被选中的复选框元素              |

可以利用    :type值     的形式，来获取元素

## 三、属性

（1）attr（）：有两个参数表示给当前选中的元素添加属性，参数1表示属性，参数2表示属性值

若只有一个参数则表示获取所选中元素的属性（操作属性值为非布尔值的属性，且标签的非固有的属性建议用该方法）

（2）prop（）：专门操作属性值为布尔值的属性，且标签固有的属性建议用该方法

（3）removeAttr（）：表示移除所有符合条件的属性，且只有一个的参数表示选中属性

（4）addClass（）：表示给所有的同名元素添加class，只有一个的参数表示要添加的class名

（5）removeClass（）：表示给所有的同名元素移除指定的class，只有一个的参数表示class名

（6）html（）：表示获取选中的所有同名元素的标签体，只有一个的参数则表示设置指定标签体

（7）val（）：表示获取选中的所有满足条件的元素的value值，若只有一个的参数表示设置指定value值

## 四、css

css（）方法只能设置style中的样式

可以直接将	{ 各种样式 }这样的一个对象	作为参数

一个参数表示获取style中的对应属性的属性值

两个参数表示设置style中的属性为指定的属性值

## 五、位置

offset（）：表示相对于页面的偏移量，含有left、top两个方向,可读/写（原点是页面左上角）

可以设置参数，参数是一个对象，对象中存放具体偏移值，会发生元素的偏移

position（）：表示相对于父元素左上角的坐标，一般不加参数，可以读（原点是父元素左上角）

scrollTop（）：表示当前滚动条相对于某元素的距离，可以有一个参数，表示设置滚动到某坐标 ，可读/写（原地是滚动条顶部）

## 六、尺寸

### 1.内容尺寸

width（）：width

height（）：height

### 2.内部尺寸

innerHeight（）：height+padding

innerWidth（）：width+padding

### 3.外部尺寸

outerHeight（）：height+padding+border，如果是参数是true，则加上margin

outerWidth（）：width+padding+border，如果参数是false，则加上margin

## 七、jQuery对象的筛选

过滤后仍然是对象

（1）first（）：获取一个元素伪数组的第一个元素

（2）last（）：获取一个元素伪数组的最后一个元素

（3）eq（）：参数为一个表示下标index，则表示获取一个元素伪数组的下标为index的元素

（4）filter（）：获取一个元素伪数组中指定属性为指定值的元素，参数为一个且语法为：filter（“[属性=属性值]”）

若语法为：filter（“[属性]”），则表示获取一个元素伪数组中含有指定属性的元素

若语法为：filter（“[属性] [属性=属性值]”），则表示获取一个元素伪数组中含有指定属性,且指定属性不为指定属性值的元素

（5）not（）：获取一个元素伪数组中指定属性	不	为指定值的元素（包括没有指定属性的元素），参数为一个，语法：not（“[属性=属性值]”）

（6）has（）：获取一个元素伪数组中含有指定子元素的所有满足条件的元素，且影响的是满足条件的父元素，例如 

> $lis.has("span").css("background","red");	此处就是影响的是符合条件的li，而不是span

## 八、jQuery对象的查找

（1）children（）：表示找到当前元素的指定子元素，例：

> $ul.children("span:eq(1)").css("background","red")	
>
> 此处找到的是ul标签下的第2个span子标签

（2）find（）：表示找到当前元素的指定后代元素，例：

> $ul.find("span:eq(1)").css("background","red")	

此处找到的是ul标签下的第2个span后代标签

（3）parent（）：找到指定元素的复标签

（4）prevAll（）：表示找到指定标签的前面的所有指定标签

> var $li=$("#cc")
>
> $ul.prevAll("li").css("background","red")	

此处表示获取id为cc的li标签的前面的所有li标签

（5）sibling（）：表示获取指定条件的元素的所有兄弟标签，参数只有一个表示  兄弟标签是什么，例：

> var $li=$("#cc")
>
> $li.sibling("li").css("background","red")	
>

此处表示id为cc的li标签的所有兄弟li标签

## 九、jQuery文档操作

### 1.元素内部插入：

（1）append（）：表示为每个匹配的元素末尾添加指定  标签体内容

（2）appendTo（）：表示将指定的  标签体内容   添加到指定的所有匹配的元素末尾（操作对象是标签体内容，参数是选中的 元素）

（3）prepend（）：表示在每个匹配的元素	前面	添加指定  标签体内容

（4）prependTo（）：表示将指定的  标签体内容   添加到指定的所有匹配的元素前面（操作对象是标签体内容，参数是选中的 元素）

~~~js
//HTML部分
<div id="test">
  <p>a</p>
</div>
//js部分
$(document).ready(function(){
    $("#test").append("<p>b</p>") //使用append()添加 b 段落
    $("#test").prepend("<p>c</p>") //使用 prepend()添加 c 段落
})
/*结果如下：
<div id="test">
    <p>c</p>
    <p>a</p>
    <p>b</p>
</div>
*/
~~~

### 2.元素外部插入：

（1）before（）：表示为每个匹配的元素前面添加指定  标签体内容

（2）after（）：表示为每个匹配的元素末尾添加指定  标签体内容

~~~js
//HTML部分
<div id="test">
  <p>a</p>
</div>
//js部分
$(document).ready(function(){
    $("#test").after("<p>b</p>")
	$("#test").before("<p>c</p>")
})
/*结果如下：
<p>c</p>
<div id="test">
	<p>a</p>
</div>
<p>b</p>
*/
~~~

### 3.元素替换：

（1）replaceWith（）：表示为每个匹配的元素替换为指定的  标签体内容

（2）replaceAll（）：表示将指定的  标签体内容  替换掉所有匹配的元素（操作对象是标签体内容，参数是选中的 元素）

### 4.元素删除：

（1）empty（）：表示将所有匹配的元素内部清空，一般情况下不加参数

（2）remove（）：表示将所有匹配的元素移除，一般情况下不加参数

## 十、jQuery事件处理

### 1.各个常用事件

（1）页面载入：

在DOM加载完成后就运行的代码：$(document).ready(function(){      })

而我们可以简写为：$(function(){         })

（2）绑定监听事件有两种方法：

第一种：jQuery对象.on（“ 事件 ”，function（）{ 	}）（这种方法更加通用：可以使用不同的事件，但是使用率不如第二种方法）

第二种：jQuery对象.事件名（function（）{	 }）（更加简便）

 （3）移入移出事件

mouseenter（）：当鼠标进入指定标签时就会触发（只触发一次）

mouseleave（）：当鼠标离开指定标签时就会触发（只触发一次）

（4）悬停事件

hover（）：参数有两个，都是函数，分别表示移入移出事件

该事件相当于对移入移出事件的封装

（5）解除监听事件

off（）：解除指定jQuery对象上绑定的所有事件

该事件必须要通过其他鼠标事件来触发

有一个参数表示解除指定	已绑定的事件

（6）事件的坐标

event.clientX/event.clientY：相对于视角的左上角，原点为向下或向右滚动后所能看到的视角页面左上角（原点会变）

event.pageX/event.pageY：相对于页面的左上角，原点为页面左上角（原点不会变）

event.offsetX/event.offsetY：相对于事件元素左上角，原点为元素的左上角（原点不会变，除非对获取的元素进行了位置的设置）

（7）停止事件冒泡

event.stopPropagation（）：表示停止事件冒泡（一般情况下不加参数）

举例说明，一个div内的一个div元素，给父子元素都加上一个点击监听事件，点击子元素时不会触发父元素的事件

（8）阻止事件默认行为（例如超链接页面跳转）

event.preventDefault（）：表示阻止事件默认行为（一般情况下不加参数）

### 2.mouseover和mouseenter的区别

mouseover：在移入子元素时也会触发父元素所绑定的事件，对应相反事件mouseout

mouseenter：只有在移入当前元素时才会触发，对应相反事件mouseleave（hover（）使用的就是mouseenter（）和mouseleave（））

### 3.事件委派/委托

（1）解释

将多个子元素的事件监听委托给父辈元素处理

监听回调是加在了父辈元素上

当操作任何一个子元素时，事件会冒泡到父辈元素上

父辈元素不会直接处理事件，而是根据event.target得到发生事件的子元素，通过这个子元素来调用回调函数

且事件委派机制就是利用事件冒泡实现的

<hr/>

举个例子，比如有一个ul无序列表，给现有的li元素添加监听事件（点击变红），并给按钮添加上一个监听事件（点击就添加一个li标签），但是在点击按钮后，新增的li标签没有 点击变红的监听事件,此时用事件委托机制就可以实现

（2）事件委托的双方

委托方：子元素   	业主（例如li）

被委托方：父元素	中介（例如ul）

（3）好处

添加新的子元素时，会自动有事件响应处理（动态添加事件）

减少事件监听的数量

（4）如何使用

设置事件委托：$（父辈元素）.delegate（子元素，事件名，回调函数）

移除事件委托：$（父辈元素）.undelegate（事件名）

## 十一、jQuery内置动画

### 1.内置的动画

动画本质就是	透明度或者宽高	的变化过程

~~~js
var $div=$(".div1");
//淡出
$("#btn1").click(function(){
    $div.fadeOut("slow",function(){
        alert("淡出结束")
    })
})
$("#btn2").click(function(){
    $div.fadeIn("slow",function(){
        alert("淡入结束")
    })
})
$("#btn3").click(function(){
    $div.fadeToggle("slow",function(){
        alert("动画结束")
    })
})
$("#btn4").click(function(){
    $div.slideUp("slow",function(){
        alert("向上收缩结束")
    })
})
$("#btn5").click(function(){
    $div.slideDown("slow",function(){
        alert("向下伸展结束")
    })
})
$("#btn6").click(function(){
    $div.slideToggle("slow",function(){
        alert("切换结束")
    })
})
$("#btn7").click(function(){
    $div.show(function(){
        alert("立即显示结束")
    })
})
$("#btn8").click(function(){
    $div.show(2000,function(){
        alert("慢慢显示结束")
    })
})
$("#btn9").click(function(){
    $div.hide(3000,function(){
        alert("慢慢隐藏")
    })
})
$("#btn10").click(function(){
    $div.toggle(3000,function(){
        alert("显示隐藏切换")
    })
})
~~~

### 2.自定义动画

~~~js
var $div=$(".div1");
//宽高都变为200
$("#btn1").click(function(){
    $div.animate({
        width:200,
        height:200
    },3000)
})
//先变宽后变高
$("#btn2").click(function(){
    $div.
    animate({
        width:200
    })
        .animate({
        height:200
    })
})
//移动到指定位置
$("#btn3").click(function(){
    $div.
    animate({
        left:300,
        top:100
    })
})
//移动指定距离
$("#btn4").click(function(){
    $div.
    animate({
        left:"+=100",
        top:"+=50"
    })
})
//停止动画
$("#btn5").click(function(){
    $div.stop()
})
~~~

## 十二、jQuery多库共存

如果有两个以上的库都有$，就存在冲突

解决：jQuery库可以释放$的使用权，让另一个库可以正常使用，此时jQuery库就只能使用jQuery来代替$了

释放使用权的方法：jQuery.noConflict（）

## 十三、区分onload和ready

### 1.window.onload

​	在document文档加载完成后就可以可以对DOM进行操作，document文档包括了加载图片等其他信息。那么Dom Load就是在页面响应加载的顺序中的“加载图片等其他信息”之后，就可以操作Dom了。

只能执行一次，如果有多个，那么第一次的执行会被覆盖。

除了要等待DOM被创建还要等到包括大型图片、音频、视频在内的所有外部资源都完全加载。如果加载图片和媒体内容花费了大量时间，用户就会感受到定义在onload事件上的代码在执行时有明显的延迟。

### 2.$(document).ready()

​	等同于：$(function(){ 	})  

​	在DOM加载完成后就可以可以对DOM进行操作。一般情况一个页面响应加载的顺序是：域名解析-加载html-加载js和css-加载图片等其他信息。那么Dom Ready应该在“加载js和css”和“加载图片等其他信息”之间，就可以操作Dom了。

可以执行多次，第N次都不会被上一次覆盖。

只需对 DOM 树的等待，而无需对图像或外部资源加载的等待，从而执行起来更快。

## 十四、jQuery插件

### 1.扩展$全局对象的方法

$.extend(dest,src1,src2,src3...)

常用语法：$.extend（{ 	}）

该方法省略dest参数
   上述的extend方法原型中的dest参数是可以省略的，如果省略了，则该方法就只能有一个src参数，而且是将该src合并到调用extend方法的对象中去，如：
$.extend(src)

该方法就是将src添加到jQuery的全局对象中去

### 2.扩展jQuery对象的方法

$.fn.extend({	})
 　该方法将src合并到jquery的实例对象中去

调用时：$（“选择器”）.自定义的方法

### 3.上述两种的例子

~~~js
(function(){
    //添加函数方法
    $.extend({
        min:function(a,b){
            return a<b?a:b;
        },
        max:function(a,b){
            return a>b?a:b;
        },
        leftTrim:function(str){
            return str.replace(/^\s+/,"")
        },
        rightTrim:function(str){
            return str.replace(/\s+$/,"")
        }
    })
    //jQuery对象的方法的扩展
    $.fn.extend({
        checkAll:function(){
            this.prop("checked",true);//将伪数组中的元素统一设置才可以这样
        },
        unCheckAll:function(){
            this.prop("checked",false);
        },
        reverseCheck:function(){
            this.each(function(){/*此处不是统一设置成一样的属性值，
                而是伪数组的每个元素的属性值都不一样，所以要遍历*/
                this.checked=!this.checked;
            });
        }

    })
})()
~~~

如何调用

~~~js
 console.log($.min(3,5),$.max(3,5));

var str="          --hello world--             ";
console.log($.leftTrim(str),$.rightTrim(str));

$(function(){
    var $items=$(":checkbox[name=items]")
    $("#checkedAll").click(function(){
        $items.checkAll();
    })
    $("#checkedAllNo").click(function(){
        $items.unCheckAll();
    })
    $("#reverseChecked").click(function(){
        $items.reverseCheck();
    })
})
~~~

## 注意点

### 1.伪数组

可遍历，有length属性，数值下标

但是没有数组对象内置的方法：foreach（），push（），pop（），splice（）等等

### 2.this和$(this)

如果只是简单的获取DOM元素本身的属性，则可以用this.xxx

但如果对象是jQuery对象，则要用$(this).xxx