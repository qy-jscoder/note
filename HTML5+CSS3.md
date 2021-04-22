

## 一、meta的用法

meta主要用于设置网页的一些元数据，元数据不是给用户看的

属性charset指定网页的字符集

### 1.属性name

属性name表示指定的数据的名称

（1）属性值为keywords，表示网站的关键字（搜索引擎通过关键字来搜索），可以同时指定多个关键字，关键字之间用逗号隔开

（2）属性值为description，表示用于指定网站的描述，网站的描述会作为搜索结果显示在搜索引擎的结果中

### 2.属性content

属性content表示指定的数据的内容

### 3.属性title

属性值会作为搜索结果的超链接上的文字显示

### 4.属性http-equiv

~~~html
<meta http-equiv="refresh" content="3;url=https://www.baidu.com">
~~~

该语句表示重定向，content中的表示3秒后跳转到指定网址

## 二、结构化语义标签

div没有语义，就用来表示一个区块，目前来说div还是主要的布局元素

### 1.header

表示网页头部，一个网页中可以有多个。

### 2.main

表示网页主体部分，一个页面中只有一个main

### 3.footer

表示网页的底部，一个网页中可以有多个。

### 4.nav

表示网页的导航

### 5.aside

表示和主体相关的其他内容，例如：侧边栏

### 6.article

表示一个独立的文章

### 7.section

表示一个独立的区块

## 三、图片格式

除了常见格式外，可以将图片使用base64编码，转为字符，通过字符的形式来引入图片，一般都是和网页一起加载的图片

## 四、em和rem

em相对于元素的字体大小改变而改变

rem相对于HTML根元素的字体大小改变而改变

比如

~~~css
html{
	font-size:100px;
}
.box1{
	width:1rem//此处1rem就表示100px
}
~~~

## 五、HSL

H：色相（0~360）

S：饱和度，颜色的浓度（百分比）

L：亮度，颜色的亮度（百分比）

## 六、盒子模型

### 1.auto

水平方向上的子元素在其父元素中，水平布局必须满足以下等式

margin-left+border-left+padding-left+width+margin-right+padding-right+border-right=父元素内容区宽度

如果不满足，则称为过度约束，则等式会由浏览器自动调整（调整margin-right）

如果其中有一个值设为auto，则会由浏览器根据其他值来自动计算该auto的值

无论怎样，浏览器都会使得该等式满足

如果左右都为auto，即为水平居中，我们一般都根据该原理实现块级元素水平居中

<hr/>

所以有些时候，我们不应该给元素设置宽度，这样当我们设置内边距时，元素本身不会被撑开，而根据水平布局等式，浏览器会自动将元素宽度调整，则宽度不变，且内边距也实现了。

> 详细参考 ：https://www.bilibili.com/video/BV1XJ411X7Ud?p=56&spm_id_from=pageDriver

### 2.盒子大小

默认情况下，盒子可见框大小由内容区、内边距和边框共同决定

box-sizing属性用来设置盒子尺寸大小的计算方式

可选值：

（1）content-box 默认值，宽度和高度用来设置内容区大小（此处的宽度和高度指的是内容区总大小

（2）border-box，宽度和高度用来设置整个盒子可见框的大小（此处的宽度和高度指的是可见框总大小，即一旦设置好，则无论怎么调整都不会改变可见框的大小）

### 3.轮廓阴影和圆角

（1）outline：

用来设置元素的轮廓线，用法和border一样

不同之处在于轮廓不会影响到整体的布局

例如：一个div元素下面有一个span元素，给div设置边框则span会被挤下去

​	给div设置outline，则span不会被挤下去，只会被轮廓线遮住

（2）阴影box-shadow

用来设置元素的阴影效果，阴影不会影响到页面布局

第一个值：水平偏移量，设置阴影的水平位置，正值向右移，负值向左移动

第二个值：垂直偏移量，设置阴影的垂直位置，正值向下移动，负值向上移动

第三个值：阴影的模糊半径，值越大模糊程度越大

第四个值：阴影的颜色

注：不会影响布局

（3）圆角

border-radius

有四个单独设置的方向：border-top-left-radius、border-top-right-radius、border-bottom-left-radius、border-bottom-right-radius

以上各属性的属性值可以有两个值，第一个值指的是水平方向的具体值，第二个值是垂直方向的具体值

也可以用百分比作为属性值

## 七、定位

粘滞定位：

position：sticky 开启了粘滞定位，同时设置方向以及方向上的偏移量，代表当在指定方向上滚动到指定位置以后，就不会再动

## 八、字体族

### 1.常见字体

~~~css
/*font-face可以将服务器中的字体直接提供给用户去使用*/
@font-face {
    font-family: myfont;/*自己取的任意名称*/
    src: url(/*本地字体所在路径*/);
}
~~~

（1）从服务器上加载字体会耗费时间，有可能会导致字体闪烁

（2）会涉及到版权问题，使用时要注意是否是开源的字体或是已付过钱

### 2.图标字体

在网页中经常使用一些图标，可以通过图片来引入图标

但是图片大小比较大，并且非常不灵活

所以在使用图标时，我们可以将图标直接设置为字体

然后通过font-face的形式来对字体进行引入

这样可以以字体的形式使用图标

使用： 导入库

创建i标签，利用特定的class来使用图标（一般每个图标有两个class，第一个一般是fas，第二个就是具体要用的图标的class）

~~~css
<i class="fas fa-bell"></i>
~~~

也可以利用实体来实现：

~~~css
<i class="fas">&#xf0f3</i>
~~~

有时候为了方便，利用before或after伪元素来实现调用图标

~~~css
li::before{
    content: "\f1b0";
    font-family: "Font Awesome 5 Free";
    font-weight: 900;
    color: blue;
}
~~~

## 九、实体

在HTML中有些时候，我们不能直接书写一些特殊符号，比如，多个连续的空格，比如，大于小于符号

如果要使用，则需要使用HTML中的实体（转义字符）

实体的语法：

​	&nbsp 空格

​	&gt 	大于号

等等

## 十、文本样式

### 1.text-decoration文本修饰符

可选值：

（1）none：什么都没有

（2）underline下划线

（3）line-through删除线

（4）overline上划线

### 2.white-space

设置空白

（1）normal正常

（2）nowrap不换行，一行显示

（3）pre保留空白

文本设置省略号：

~~~css
//文本设置省略号
.box2{
    width: 300px;
    white-space: nowrap;//一行显示
    text-overflow: ellipsis;//将文本隐藏部分设置为省略号的形式
    overflow: hidden;//给文本设置宽度，超出宽度部分隐藏
}
~~~

## 十一、背景

### 1.background-clip

设置背景的范围

可选值：

border-box默认值，背景会出现在边框的下边

padding-box 背景不会出现在边框，只会出现在内容区和内边距

content-box背景只会出现在内容区

### 2.background-origin

设置背景图片的偏移量计算的原点

padding-box默认值，background-position从内边距开始计算

content-box背景图片的偏移量从内容区开始计算

border-box背景图片的偏移量从边框处开始计算

### 3.background-size

设置背景图片大小

~~~css
background-size:200px 200px;
~~~

如果有两个值，则分别是宽和高

如果只有一个值，则宽是由自己设置，高是auto

若值为cover，则表示图片比例不变，将图片铺满（有可能图片显示不全）

若值为contain，则表示图片比列不变，将图片在元素中完整显示

注：（1）如果要将background相关属性值写在background中，则background-size必须写在background-position后面

（2）background-origin要写在background-clip前面

### 4.线性渐变

设置颜色渐变效果，渐变可以指定多个颜色（包括但不限于2种颜色）

（1）background-image: linear-gradient（）

默认是	从上向下渐变

~~~css
background-image: linear-gradient(red,yellow);
~~~

可以指定一个渐变的方向，语法如下：

~~~css
background-image: linear-gradient(to left,red,yellow);
~~~

该语句表示	向左从红到黄渐变



也可以通过设置deg（度数）来设置方向

还可以通过1 turn来表示转一圈

（2）background-image: repeat-linear-gradient

将线性渐变平铺

### 5.径向渐变

background-image : radial-gradient（）

从中心向外渐变

可以给渐变色设置宽高（径向渐变中设置宽高显示为 圆形）

~~~css
background-image: radial-gradient(100px 100px,red,yellow);
~~~

相关具体可选值，请参考文档

## 十二、网站图标

设置网站打开后的图标，语法如下：

~~~css
<link rel="icon" href="当前图标所在路径">
~~~

## 十三、过渡效果

过渡效果可通过transition来实现

语法如下：

~~~css
.box2{
    transition:height 2s;//表示高度在2s内发生变化
    transition:all 2s;//表示所有设置的元素属性都会在2s内发生变化
}
~~~

过渡相关的属性：

### 1.transition-property

指定要执行过渡的属性

多属性使用，用逗号隔开

如果要执行自定义的所有属性，则用all属性值

大部分属性都支持过渡效果

### 2.transition-duration

指定过渡效果的持续时间

可以给对应的transition-property属性值分别加上持续时间

### 3.transition-timing-function

过渡的时序函数

指的是过渡的执行的方式

时序是由贝赛尔曲线决定

属性值：

（1）ease 默认值，先慢速开始，再加速，最后减速结束

（2）linear 匀速

（3）ease-in 加速运动

（4）ease-out减速运动

（5）ease-in-out 先加速 后减速

也可以通过cubic -bezier（）函数来指定具体的运动轨迹

> （该函数的具体参数可参照https://cubic -bezier. com）

还可以通过steps（）分部执行过渡效果

若只有一个参数，则表示步骤次数，即该过渡效果分几步走

若有两个参数，则第二个参数表示步骤的什么时候结束或开始，即在第x步在第x秒的开始或结束时才继续下一步

### 3.transition-delay

过渡效果触发后的延时，在指定时间后才会发生过渡效果

注：若只通过transition属性来设置相关属性值，则顺序无序，但是第一个时间必须是过渡效果的持续时间

注：要实现过渡，则必须设置一个起始效果

## 十四、动画效果

动画和过渡类似，但是过渡需要在某一属性发生变化时才会触发

而动画可以自动触发效果

设置动画效果，必须先设置一个关键帧，关键帧设置了动画执行的每一个步骤

关键帧语法：

~~~css
@keyframes 关键帧的名字{
	to{	}//表示动画的结束位置
	from{	}//表示动画的开始结束
}
要发生动画的元素{
    animation-name:关键帧名;
    animation-duration:时间
}
~~~

注：若只通过animation属性来设置相关属性值，则顺序无序，但是第一个时间必须是动画效果的持续时间

关键帧补充：

~~~css
@keyframes 关键帧的名字{
	from{	}//表示动画的开始结束
    
    33%{	}
    
    66%{	}
    
    to{		}//表示动画的结束位置
}
~~~

可以通过以上语法将动画设置的更加复杂，百分比表示动画的阶段（自定义，并不固定）

## 十五、变形

由transform属性来设置

不会影响其他元素的布局（脱离文档流）

平移元素时，如果用百分比移动，则百分比是相对于自身来计算的

### 1.X轴平移

translateX（）沿着X轴方向平移

### 2.Y轴平移

translateY（）沿着Y轴方向平移

### 3.Z轴平移

z轴平移，想要看到变化必须要先设置页面的视距

translateZ（）沿着Z轴方向平移

<hr/>

该属性可以用在无法用常规方法设置元素居中的情况下，代码如下图所示：

![image-20210309193651657](D:\web self-learn\HTML+CSS\HTML5+CSS3以及html的补充.assets\image-20210309193651657.png)

X轴居中如图所示，Y轴居中类似

实现鼠标指向指定元素出现浮出效果：

![image-20210309194719699](D:\web self-learn\HTML+CSS\HTML5+CSS3以及html的补充.assets\image-20210309194719699.png)

![image-20210309194746951](D:\web self-learn\HTML+CSS\HTML5+CSS3以及html的补充.assets\image-20210309194746951.png)



### 4.旋转

rotateX（）/rotateY（）/rotateZ（）

### 5.背景显示

backface-visible属性可以设置图片翻转后是否显示背面

### 6.缩放

transform:scaleX（）水平方向缩放

transform:scaleY（）垂直方向缩放

transform:scale（）双方向缩放

参数为数值，表示缩放多少倍

在z轴如果想看效果，必须要设置transform-style:preserve-3d;

transform-origin属性可以设置缩放开始变形的原点，默认原点是中心

## 十六、计算函数calc（）

calc（）相当于一个计算器，参数即为计算式子，不用开发者人为计算数据

语法：

~~~css
属性:calc(计算式);//计算时数据可以加单位
~~~

## 十七、less

less是一门css的预处理语言

是一个css的增强版，通过less可以编写更少的代码实现更强大的样式

在less中添加了许多新特性：对变量的支持、对mixin的支持等等

该语法大致上与css一致，但是less中添加了许多对css的扩展

所以浏览器无法直接执行less代码，要执行必须先将less转换为css，然后再执行

然而兼容性较差

### 1.基本使用

less写在less格式的文件内，

但是HTML引入时，要写引入格式为css

因为是将less转换为css（编译时会先生成一个新的css文件），再编译，所以实质上还是引入的是css文件

语法如下：

~~~less
//将body的类名为box的后代元素都设置样式
body{
    width: 500px;
    height: 500px;
    .box{
        width: 100px;
        height: 100px;
        background-color: yellow;
    }
}
//同理，如果要给box的子元素设置样式，就如下所示
body{
    width: 500px;
    height: 500px;
    .box{
        width: 100px;
        height: 100px;
        background-color: yellow;
        .box1{
            border:1px solid red;
        }
    }
}
~~~

用less写，会更加显得结构清晰

选择器:~“ ”双引号内的内容不会被编译，但是在转为css后，双引号会去掉

### 2.变量

变量可以在全局中定义，也可以在选择器中定义

变量在less中属于块级作用域，延迟加载

定义全局变量：

~~~less
@变量名:属性值;
~~~

使用变量：

~~~less
选择器{
	属性:@变量名;
}
~~~

定义局部变量：

~~~less
.box{
    @color:yellow;//定义局部变量，并初始化
    .p1{
        width:200px;
        height: 200px;
        background-color: @color;//使用了局部变量
    
    }
}
~~~

在选择器中定义的变量就可以理解为局部变量

less代码编译为css代码后：

~~~css
.box .p1 {
  width: 200px;
  height: 200px;
  background-color: yellow;
}
~~~

### 3.类名

定义类名：

~~~
@变量名:类名;
~~~

使用类名：

~~~
.@{类名}{
	属性:属性值;
}
~~~

例子：

~~~
@c:box1;
@a:200px;
.@{c}{
	width:@a;
}
~~~

如果变量是属性名，则在使用时也要加上{}

如果变量是选择器，则同理

如果变量是路径名，则在使用时也要加上{}

在一个选择器内可以通过$来调用其中的属性，例如

~~~less
.box1{
    color: #bfa;
    background-color: $color;
}
~~~

### 4.子选择器

~~~less
.box1{
    .box2{//此处表示设置 box1的后代元素box2 的样式
        width:100px;
        height:100px;
        background-color:red;
    }
    >.box3{//此处表示设置 box1的子元素box3 的样式
        width:100px;
        height:100px;
        background-color:blue;
    }
}
~~~

### 5.&外部选择器

~~~less
.box1{
    .box2{//此处表示设置 box1的后代元素box2 的样式
        width:100px;
        height:100px;
        background-color:red;
    }
    &:hover{//此处表示设置 box1的hover样式，且&表示外层的选择器
        width:100px;
        height:100px;
        background-color:blue;
    }
}
~~~

### 6.extend扩展

~~~less
.p1{
	width:100px;
    height:100px;
}
.p2:extend(.p1){
    color:red;
}
~~~

表示存在	类选择器p2	在	类选择器p1	的基础上扩展了一个属性color，且属性值为red

less文件编译后css代码为：

~~~css
.p1,
.p2 {
  width: 100px;
  height: 100px;
}
.p2 {
  color: red;
}
~~~

### 7.mixin混合函数

一旦选择器后面有括号，就表示该选择器只是用来被调用的，相当于定义了一个函数，不去调用时不会执行，只有调用了，才会执行，在less中也就是才会使用该选择器中的样式

~~~less
.p4(){//创建一个仅仅是用来被其他选择器使用的选择器样式
	width: 100px;
  	height: 100px;
  	background-color:blue;
}
.p5{
	.p4();//可以使用p4类选择器
}
~~~

编译为css后，没有	类选择器p4，只有	类选择器p5	。代码为：

~~~css
.p5 {
  width: 100px;
  height: 100px;
  background-color: blue;
}
~~~

<hr/>

混合函数中可以加参数，基本原理同上，但是传入实参时，要与形参一一对应

~~~less
.test(@w,@h){
	width: @w;
    height: @h;
    background-color: blue;
}
.test1{
    .test(100px,200px);
}
~~~

编译为css后。代码为：

~~~css
.test1 {
  width: 100px;
  height: 200px;
  background-color: blue;
}
~~~

不仅如此，还可以在设置形参时，就设置属性值（即为默认值）

~~~less
.test3(@w:100px,@h:200px){
	width: @w;
    height: @h;
    background-color: blue;
}
.test4{
    .test3();//已经设置好默认值的形参，可以不传实参
}
~~~

编译为css后。css代码：

~~~css
.test4 {
  width: 100px;
  height: 200px;
  background-color: blue;
}
~~~

更是可以在在选择器中定义一个带参数的混合函数，并给该混合函数传入实参赋值执行

~~~less
.box{
    .p1(@w,@h){//定义一个带参数的混合函数，此处 =var .p1=function(){...}
        width:@w;
        height: @h;
        background-color: blue;
    }
    .p1(300px,200px);//传入实参并执行. 此处 =.p1（），相当于js中的函数执行
}
~~~

编译为css后。css代码：

~~~css
.box {
  width: 300px;
  height: 200px;
  background-color: blue;
}
~~~

### 8.内置的mixin混合函数

less中已经提供了一些写好的混合函数

比如：darken（颜色，百分比）表示	加深颜色百分比

average（颜色，颜色）表示取两个颜色之间的平均值

### 9.less补充

（1）在less中所有的数值可以直接进行计算

~~~less
.test {
  width: 100px+100px;
  height: 200px/2;
  background-color: blue;
}
~~~

（2）将其他的less文件引入当前的less文件

相当于在HTML中引入两个less文件

~~~less
@import "style.less";
~~~

## 十八、flex弹性盒

flex是css中的一种布局手段，主要用来代替浮动来完成页面的布局

可以使元素具有弹性，让元素可以跟随	页面/窗口	的大小的改变而改变

然而，兼容性较差

> 弹性盒应用可参考https://www.bilibili.com/video/BV1XJ411X7Ud?p=135&spm_id_from=pageDriver

### 1.弹性容器

要使用弹性盒，必须先将元素设置为弹性容器（只能给容器设置）

我们通过display来设置弹性容器

display:flex 设置为块级弹性容器

display:inline-flex 设置为行内的弹性容器

一旦设置display:flex表示默认设置flex-direction的属性值为row

### 2.弹性元素

 弹性容器的子元素是弹性元素

弹性元素可以同时是弹性容器

### 3.主轴

弹性元素当前的排列方向称为主轴

### 4.侧轴

与	弹性元素的排列方向	垂直的方向称为侧轴

### 5.弹性容器的样式

flex-direction：

指定容器中弹性元素的排列方式

可选值：

（1）row 默认值，弹性元素在容器中水平排列（从左向右）

（2）row-reverse 弹性元素在容器中反向水平排列（从右向左 ）

（3）column 弹性元素纵向排列（从上向下）

（4）column-reverse 弹性元素纵向排列（从下向上）



flex-wrap

设置弹性元素是否在弹性容器中自动换行

可选值：

（1）nowrap 默认值，元素不会自动换行

（2）wrap 元素沿着侧轴方向自动换行

（3）wrap-reverse 元素沿着侧轴反方向换行



justify-content

表示主轴上的元素如何排列

可选值：

（1）flex-start 元素沿着主轴起边排列

（2）flex-end 元素沿着主轴终边排列

（3）center 元素居中排列

（4）space-around 空白左右平均的分配到每个元素的两侧（两个元素之间的空白是元素和边界之间的空白的两倍）

（5）space-evenly 空白分配到元素的单侧（每处空白都宽度相等）

（6）space-between 空白均匀的分配到元素之间（元素和边界之间没有空白）

align-items

元素在侧轴上如何对齐

可选值：

（1）stretch 默认值，将元素的长度设置为相同的值

（2）flex-start 元素沿着辅轴起边排列

（3）flex-end 元素沿着辅轴终边排列

（4）center 元素居中排列

（5）baseline基线对齐



align-content

辅轴空白空间的分布（辅轴上元素如何排列）

可选值同 justify-content



align-self

用来覆盖当前弹性元素上的align-items

### 6.弹性元素的样式

flex-grow

指定弹性元素的伸展的系数

默认为0,系数为1表示弹性元素伸展将弹性容器占满

当父元素有多余空间时，子元素如何伸展

父元素的剩余空间，会按照比例进行分配



flex-shrink

指定弹性元素的收缩系数

当父元素中的空间不足以容纳所有的子元素时，子元素会按照收缩系数的比例进行收缩



flex-basis

设置弹性元素在主轴上的基础长度

默认是auto，表示参考元素自身的高度或宽度



可以统一用flex属性设置以上三个属性的值

flex：伸展 缩减 基础（必须按照该顺序，不能打乱）

此外，该属性还有三个可选值：initial、auto、none

initial表示 flex: 0 1 auto

auto表示flex: 1 1 auto

none表示flex: 0 0 auto （弹性元素没有弹性）



order属性

决定弹性元素的顺序，例如：

> order: 2	表示当前元素在第二个

## 十九、像素

屏幕是一个一个发光的小点构成的，这一个个小点就是像素

分辨率1920X1080指的就是 屏幕中小点的分配规律

在前端开发中，像素要分成两种情况讨论：css像素和物理像素

页面缩放时，页面的物理像素没有变。

但是CSS像素会改变。如果放大页面，一个CSS像素所占的物理像素变多，那么屏幕范围的CSS像素变少。如果缩小页面，一个CSS像素所占的物理像素变少，那么屏幕范围的CSS像素变多。

### 1.物理像素

上述所说的小点就是物理像素

### 2.css像素

编写网页时，我们所用的就是css像素

浏览器在显示页面时，需要将css像素转换为物理像素再呈现

一个css像素最终由几个物理像素显示，由浏览器决定

默认情况下，在PC端，一个css像素=一个物理像素

### 3.视口

视口就是屏幕中显示网页的区域

可以通过查看视口的大小，来观察css像素和物理像素的比值

默认情况下：

​	视口宽度 1920px（css像素）

​					1920px（物理像素）

​					此时，css像素和物理像素的比是1 : 1

放大两倍的情况下：

​	视口宽度	960px（css像素）

​						1920px（物理像素）

​						此时，css像素和物理像素的比是1 : 2

我们可以通过改变视口大小来改变css像素和物理像素的比值

### 4.手机像素

在不同的屏幕，单位像素的大小是不同的，像素越小屏幕会越清晰

24寸	1920X1080

iPhone6 4.7寸	750X1334

智能手机的像素点远小于 计算机的像素点

问题：一个宽度为900px的网页在iPhone6中如何显示？

默认情况下，移动端的网页都会将视口设置为980像素（css像素）

移动端的像素比就是980/移动端宽度（980/750）（即视口大小/移动端宽度）

以确保pc端网页可以在移动端正常访问，但是如果网页的宽度超过了980

移动端的浏览器会自动对网页缩放以完整显示网页，导致网页中的内容非常非常小



所以大部分的PC端网站都可以在移动端正常显示，但是往往不会有一个好的体验



所以编写移动端代码时，必须要保持一个比较合理的像素比，比如：

1css像素	对应	2个 物理像素

1css像素	对应	3个 物理像素



一般我们要将像素比设置为一个最佳的像素比，得到一个最佳效果

将像素比设置为最佳像素比的视口大小，我们称之为完美视口（一般完美视口是设备宽度的一半）

可以通过meta标签来设置视口大小

~~~html
<meta name="viewport" content="width=300px">//此处的宽度是视口大小，可自定义
~~~

然而每个人的手机不同，此处的宽度不能写死

~~~HTML
<meta name="viewport" content="width=device-width, initial-scale=1.0">
~~~

此处的device-width表示设备的宽度，这样更加灵活。为了防止极端情况，要加上initial-scale=1.0

### 5.移动端大小单位vw

同理，在移动端开发中，就不能使用px来进行布局了

然而用百分比也会有缺陷，因为参照物会发生变化

所以在移动端开发中，采用vw作为单位

vw表示的参照的是视口的宽度

100vw=一个视口的宽度

1vw=1%视口宽度

### 5.vw适配

根据1 rem=1 html的字体大小

先按照100vw=设备宽度获取1vw=多少px

然后将html中的font-size按照比例设置好，且单位是vw

最后将网页中元素的大小依照与html中font-size的比例，进行调整，设置单位为rem

![image-20210311210619217](D:\web self-learn\HTML+CSS\HTML5+CSS3以及html的补充.assets\image-20210311210619217.png)

## 二十、媒体查询

### 1.简介

响应式布局

网页可以根据不同的设备或窗口大小呈现出不同的效果

使用响应式布局，可以使一个网页适用于所有的设备

响应式布局的关键就是 媒体查询

通过媒体查询，可以为不同的设备，或设备不同的状态来分别设置样式

语法：

~~~html
@media all{//表示所有的设备
	
}
~~~

媒体类型为：

（1）all 所有设备

（2）print 打印设备

（3）screen 带屏幕的设备

（4）speech 屏幕阅读器

可以使用逗号来连接多个媒体类型，这样他们之间就是或的关系

还有一种写法

~~~html
@media only 类型名{
	
}
~~~

但该方法没有意义，只是为了兼容老浏览器

### 2.特性

width 视口宽度

height 视口的高度

语法：

~~~html
@media (width: 500px){/*此处要加括号*/
/*此处表示当视口宽度等于500px时，body的背景颜色才会变色*/
	body{
		background-color:#bfa;
	}
}
~~~

min-width 视口的最小宽度（视口大于指定宽度时会生效）

max-width 视口的最大宽度（视口小于指定宽度时会生效）



样式切换的分界点，我们称之为断点，也就是网页的样式会在这个点时发生变化

一般常用的断点：

小于768 超小屏幕 max-width=768 px

大于768 小屏幕 min-width=768 px

大于992 中型屏幕 min-width=992 px

大于1200 大型屏幕 min-width=1200 px



若是表示或的关系，则用逗号

若是表示且的关系，则用and





























































































































































## 注意

（1）p元素中的图片会和父元素之间有一段空隙，这是因为图片和字体一样都是以基线对齐的，所以要消去空隙只要不以基线对齐就行，可以用vertical-align设置属性值来消去

（2）可以给body设置min-width属性，设定body的最小宽度，即当小于min-width后，界面不会变化

（3）让盒子	水平垂直居中	于父元素

~~~html
<!DOCTYPE>
<html>
    <head>
        <meta charset="UTF-8">
        <meta name="viewport" content="width=device-width,initial-scale=1.0" >
        <meta http-equiv="X-UA-Compatible" content="ie=edge">
        <style>
            /* 让盒子垂直水平居中于父元素 */
            .wangyi-loading{
                width: 360px;
                height: 360px;
                margin:auto;
                position: absolute;
                top:0;
                right:0;
                bottom:0;
                left:0;
                border:5px solid red;
            }
        </style>
    </head>
    <body>
        <div class="wangyi-loading">

        </div>
    </body>
</html>

~~~

此处是让div元素水平垂直居中于body

（4）只要涉及到z轴平移或旋转，都要先给html设置视距

（5）原生css也支持变量，语法如下：

~~~css
html{
	--colo:yellow;//此处是一个变量，可以任意定义（变量前面必须加上“--”）
}
.box{
    width: 100px;
    height: 100px;
    background-color: var(--colo);//使用变量
}
~~~

（6）flex一般常用在移动端中，pc端考虑到兼容性问题所以用得少，但是如果能用flex就不要用浮动