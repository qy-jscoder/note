[TOC]- HTML5笔记
- [一、attribute和property](#一attribute和property)
  - [1.attribute](#1attribute)
  - [2.property](#2property)
  - [3.两者关系](#3两者关系)
- [二、原生js操作class](#二原生js操作class)
- [三、原生js操作自定义属性](#三原生js操作自定义属性)
- [三、属性设置可编辑文本](#三属性设置可编辑文本)
- [四、HTML5的优势](#四html5的优势)
- [五、渲染模式](#五渲染模式)
- [六、语义化标签](#六语义化标签)
- [七、canvas最基本的部分](#七canvas最基本的部分)
  - [1. getContext](#1-getcontext)
  - [2.矩形](#2矩形)
  - [3.路径](#3路径)
## 一、attribute和property

### 1.attribute

HTML的预定义和自定义属性，属性值只能是字符串

在js中，一般通过setAttribute方法来设置对应属性的属性值

### 2.property

一般是指原生js对象的直接属性，属性值可以是各种类型

### 3.两者关系

在dom对象中既有attribute的属性也有property属性

非布尔值属性：不管什么情况，attribute和property的属性值都会同步

布尔值属性：property不会同步attribute。操作过property属性，attribute属性无法再操作；没有操作过property属性，attribute可以操作

浏览器只认property，且用户也只操作property

所以一般推荐，操作布尔值属性时用prop方法，操作非布尔值属性时用attr方法

## 二、原生js操作class

~~~js
var testNode=document.getElementById('btn')
testNode.classList.add('class1');//添加class
testNode.classList.remove('class1');//删除class
testNode.classList.toggle('class1');//有则删除，没有则添加
console.log(testNode.classList)//DOMTokenList ["class1", value: "class1"]
~~~

## 三、原生js操作自定义属性

HTML元素属性名必须为"data	-	....	-	...."的格式

调用时要将最后一个"-"去掉，且后面的改为驼峰命名法

但是该方法只能调用

HTML部分

~~~html
<button id="btn" data-button-btn="btn2">点我</button>
~~~

js部分

~~~js
var testNode = document.getElementById('btn')
console.log(testNode.dataset.buttonBtn)//此处调用注意驼峰命名才行
~~~

## 三、属性设置可编辑文本

预定义属性contenteditable设置可编辑文本

~~~html
<div id="col" contenteditable="true">dasdsadasdd</div>
~~~

## 四、HTML5的优势

（1）跨平台：唯一一个可以在PC、MAC、Android等主流平台上的跨平台语言

（2）快速迭代，降低成本

（3）导流入口多

（4）分发效率高



## 五、渲染模式

~~~html
<!DOCTYPE html>
~~~

DOCTYPE称为文档类型声明，浏览器在解析HTML文档之前，要确定当前文档的类型，以决定其需要采用的渲染模式。

在ie6以下都为怪异模式

以怪异模式渲染的HTML文档，采用的是怪异盒子模型（即border-sizing:border-box）

相反的，其他浏览器都采用的是标准模式渲染，采用的也是标准盒子模型

## 六、语义化标签

让更多具有语义化结构化的代码标签来代替大量的无意义的div标签

这种语义化的特性提升了网页的质量和语义，对搜索引擎更加的友好

没有任何的默认样式，除了会使文本另起一行



例如，开发人员喜欢这样命名

~~~html
<div id="footer"></div>
~~~

浏览器厂商发现div名称的通用id大量重复，所以在HTML5中引入了语义化标签，来便于开发

~~~html
<footer></footer>
~~~

## 七、canvas最基本的部分

HTML5新增的元素，可通过使用js中的脚本来绘制图形

canvas有默认宽高，宽300px，高150px

给canvas设置宽高，应当直接设置canvas标签的属性，如果在css中设置，会影响canvas内的图形

支持canvas的浏览器，不会显示canvas内部的标签内容

不支持canvas的浏览器，会显示canvas内部的标签内容



原生的图形绘制，只支持矩形。所有其他的图形的绘制都至少需要生成一条路径

默认情况下，线条和填充颜色都是黑色

### 1. getContext

该方法只有一个参数，且写法固定，参数为“2d”。返回一个用于在画布上绘图的环境。

可以用getContext来获取当前的绘制环境，通俗点来讲可以理解为获得一个只在画布内的画笔

### 2.矩形

（1）fillRect方法

fillRect方法绘制一个填充好的 矩形，有四个参数，前两个为相对于画布的偏移量（确立位置），后两个为图形宽高（不能加单位）

~~~js
ctx.fillRect(0,0,50,50)
~~~

（2）strokeRect方法

strokeRect方法绘制一个带有1px边框的矩形，其他同上

~~~js
ctx.strokeRect(100,100,100,100)
~~~

（3）clearRect方法

clearRect方法表示以画布背景颜色绘制一个指定位置大小的矩形，来覆盖原矩形

~~~js
ctx.clearRect(0,0,100,150)
~~~

（4）fillStyle属性

设置填充色，只能用在fillRect方法内，通俗来说就是画笔蘸了指定颜料

~~~~js
ctx.fillStyle='yellow'
ctx.fillRect(0,0,50,50)
~~~~

（5）strokeStyle属性

设置图形轮廓的颜色

~~~js
ctx.strokeStyle='yellow'
ctx.strokeRect(100,100,100,100)
~~~

（6）lineWidth属性

设置当前绘制线条的宽度，不带单位

~~~js
ctx.lineWidth=10
~~~

（7）lineJoin属性

设置线和线连接处的样式（默认是miter）

round：圆角

bevel：斜角

miter：直角



注：canvas有一套自己的规则。lineWidth、strokeStyle、fillStyle都是同步执行的，先设置再绘制，才能得到想要的图形

### 3.路径

图形的基本元素路径。路径是通过不同颜色和宽度的线段或曲线相连形成不同形状的点的集合。

步骤：

1）创建路径起始点	moveTo方法

2）画路径的终点	lineTo方法

3）以上一步的终点为起始点，再次画一条路径	lineTo

4）步骤同3），画出自己想要的图形

5）画出图形后，再按照自己的需求，决定是边框还是填充（stroke方法或者fill方法）

注：最后画图形时要回到最初的起始点，不仅可以采用moveTo方法，也可以采用closePath方法

closePath方法会自动合并路径，如果是填充则会自动调用closePath方法就可以直接获得图形

<hr/>

beginPath方法会清空之前的路径

lineCap会设置线段末尾的形状，参数为square和butt都表示末尾为方形，但是butt是在末尾加上方形，而square是使末尾变成方形