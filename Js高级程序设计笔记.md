- [一、数据、内存、变量](#一数据内存变量)
  - [1.数据](#1数据)
  - [2.内存](#2内存)
  - [3.变量](#3变量)
  - [4.三者之间的关系](#4三者之间的关系)
- [二、关于引用变量赋值问题](#二关于引用变量赋值问题)
- [三、js调用函数时参数的问题](#三js调用函数时参数的问题)
- [四、引擎如何管理内存](#四引擎如何管理内存)
  - [1.内存生命周期](#1内存生命周期)
  - [2.释放内存](#2释放内存)
- [五、关于对象的相关问题](#五关于对象的相关问题)
  - [1.什么是对象](#1什么是对象)
  - [2.为什么用对象](#2为什么用对象)
  - [3.对象的组成](#3对象的组成)
  - [4.如何访问对象内部数据](#4如何访问对象内部数据)
  - [5.什么时候必须用对象['属性名']的方式](#5什么时候必须用对象属性名的方式)
  - [6.创建对象的内存行为](#6创建对象的内存行为)
  - [7.创建对象的模式](#7创建对象的模式)
- [六、关于函数的相关问题](#六关于函数的相关问题)
  - [1.什么是函数](#1什么是函数)
  - [2.为什么用函数](#2为什么用函数)
  - [3.如何定义函数](#3如何定义函数)
  - [4.如何调用（执行）函数](#4如何调用执行函数)
  - [5.什么是回调函数](#5什么是回调函数)
- [七、IIFE](#七iife)
  - [1.什么是IIFE](#1什么是iife)
  - [2.作用](#2作用)
- [八、this](#八this)
  - [1.什么是this](#1什么是this)
  - [2.如何确定this](#2如何确定this)
- [九、关于语句是否加分号的问题](#九关于语句是否加分号的问题)
- [十、关于原型的相关问题](#十关于原型的相关问题)
  - [1.函数的prototype属性](#1函数的prototype属性)
  - [2.函数的prototype作用](#2函数的prototype作用)
  - [3.显式原型和隐式原型](#3显式原型和隐式原型)
  - [4.内存中的行为](#4内存中的行为)
  - [5.原型链](#5原型链)
  - [6.原型的属性和方法规则](#6原型的属性和方法规则)
  - [7.instanceof](#7instanceof)
- [十一、变量提升和函数提升](#十一变量提升和函数提升)
  - [1.变量声明提升](#1变量声明提升)
  - [2.函数声明提升](#2函数声明提升)
  - [3.变量声明提升和函数声明提升的优先级](#3变量声明提升和函数声明提升的优先级)
- [十二、执行上下文](#十二执行上下文)
  - [1.全局执行上下文](#1全局执行上下文)
  - [2.函数执行上下文](#2函数执行上下文)
  - [3.总体执行的大致情况](#3总体执行的大致情况)
  - [4.相关面试题](#4相关面试题)
- [十三、作用域相关问题](#十三作用域相关问题)
  - [1.作用域定义](#1作用域定义)
  - [2.作用域类别](#2作用域类别)
  - [3.作用](#3作用)
  - [4.作用域和执行上下文的关系](#4作用域和执行上下文的关系)
  - [5.作用域链](#5作用域链)
- [十三、闭包的理解](#十三闭包的理解)
  - [1.闭包的定义](#1闭包的定义)
  - [2.常见的闭包](#2常见的闭包)
  - [3.闭包的作用](#3闭包的作用)
  - [4.闭包的生命周期](#4闭包的生命周期)
  - [5.闭包的应用](#5闭包的应用)
  - [6.闭包的缺点](#6闭包的缺点)
  - [7.内存溢出和内存泄露](#7内存溢出和内存泄露)
  - [8.闭包例题](#8闭包例题)
- [十四、进程和线程](#十四进程和线程)
  - [1.进程](#1进程)
  - [2.线程](#2线程)
  - [3.线程和进程](#3线程和进程)
  - [4.线程的优缺点](#4线程的优缺点)
  - [5.js的进程](#5js的进程)
- [十五、浏览器内核](#十五浏览器内核)
  - [1.内核的组成](#1内核的组成)
- [十六、定时器](#十六定时器)
  - [1.定时器真的是定时执行的吗](#1定时器真的是定时执行的吗)
  - [2.定时器回调函数是在分线程执行的吗](#2定时器回调函数是在分线程执行的吗)
  - [3.定时器如何实现](#3定时器如何实现)
- [十七、js执行是单线程](#十七js执行是单线程)
  - [1.js执行是单线程的](#1js执行是单线程的)
  - [2.js执行为什么是单线程的](#2js执行为什么是单线程的)
  - [3.代码的分类](#3代码的分类)
  - [4.js引擎执行代码的基本流程](#4js引擎执行代码的基本流程)
  - [5.Web Workers](#5web-workers)
- [十八、事件循环模型](#十八事件循环模型)
  - [1.模型原理图](#1模型原理图)
  - [2.模型的两个重要组成部分](#2模型的两个重要组成部分)
  - [3.模型的运转流程](#3模型的运转流程)
- [十九、H5的Web Workers多线程](#十九h5的web-workers多线程)
  - [1.介绍](#1介绍)
  - [2.使用](#2使用)
  - [3.缺点](#3缺点)
- [二十、继承](#二十继承)
  - [1.原型链继承](#1原型链继承)
  - [2.借用构造函数继承](#2借用构造函数继承)
  - [3.组合继承（将1和2两种继承方法结合起来）](#3组合继承将1和2两种继承方法结合起来)
## 一、数据、内存、变量

### 1.数据

数据是存储在内存中代表特定信息的进制位，本质上只是0或者1组成的一串数字

数据的特点：

可传递、可运算、一切皆数据

内存中所有课操作的目标都是数据

### 2.内存

内存条通电后产生的可存储数据的空间（临时的）

内存产生和死亡：内存条—>通电—>产生内存空间—>存储数据—>处理数据—>断点—>内存空间和数据都消失

内存中存储的数据： 数据、地址值

内存分类：

（1）栈：全局变量 / 局部变量

（2）堆：对象 

### 3.变量

可变化的量，由变量名和变量值组成

每个变量都对应的一块内存，变量名用来查找对应的内存地址，变量值就是内存中保存的数据

### 4.三者之间的关系

内存用来存储数据的空间

变量是内存的标识

例如：变量

var obj={name:"hi"}；

var obj_1=obj;

其中obj_1保存的是变量obj保存的内容（不能说是地址值，因为栈内存中的变量也有地址值，所以只能说变量保存的值或是变量值）

## 二、关于引用变量赋值问题

多个引用变量指向同一个对象，通过一个变量来修改对象内部数据（即属性或方法），则其他变量得到的是修改后的数据

~~~js
var a={name:20};
var b=a;
b={hello:12};
console.log(a);//结果：{name:20}
console.log(b);//结果：{hello:12}
~~~

一个变量所指向的对象发生改变（相当于换了一个空间，在堆内存中的空间地址也变了），此时其他指向原来空间的变量保存的地址内容不变

~~~js
a.age=20;
function bb(obj){
	obj={age:18};
}
bb(a);
console.log(a.age);//结果：age为20
~~~

上述代码中，a作为实参传进函数，此时形参指向的地址为a的地址。但是给obj重新赋值了一个对象，相当于将形参指向的地址断掉，指向新的对象所在的空间地址。所以a的age属性是不变的

## 三、js调用函数时参数的问题

js调用函数时传递变量参数时，是<span style="font-weight:bold;color:red">值传递</span>

理解：1.都是值（基本/地址值）传递

2.可能是值传递，也可能是引用传递（地址值）

~~~js
var a=2;
function f(a){
    a+=1;
}
f(a);
console.log(a);
~~~

此处，a=2

函数中，是将a的值复制一下，给形参，形参进行操作后，被释放，所以a的值不会变

## 四、引擎如何管理内存

### 1.内存生命周期

分配内存空间，得到其使用权	—>	存储数据，反复进行操作	—>	释放内存空间

### 2.释放内存

局部变量：函数执行完自动释放

对象：成为垃圾对象，被垃圾回收器回收

~~~js
var a={}；
a=null
~~~

上述代码的含义：创建了一个空对象

然后再将对象赋为null，即将堆内存中的对象回收。

## 五、关于对象的相关问题

### 1.什么是对象

多个数据的封装体

用来保存多个数据的容器

一个对象代表现实中的一个事物

### 2.为什么用对象

统一管理多个数据

### 3.对象的组成

属性：属性名和属性值

方法：一种特别的属性

### 4.如何访问对象内部数据

.属性名：编码简单，有时不能用

['属性名']：编码稍微麻烦些，能通用

### 5.什么时候必须用对象['属性名']的方式

实例化对象调用属性时

属性名在引号内，且包含特殊字符或者

### 6.创建对象的内存行为

创建对象时，是先在堆内存中进行操作，然后再在栈内存中操作，因为创建对象是一个赋值的过程

### 7.创建对象的模式

通过工厂模式创建的对象都是object类型

通过构造函数创建的对象都是自己创建的函数的类型

构造函数+原型的模式：属性放在构造函数中，方法放在原型对象中，该方法可以节约内存空间

## 六、关于函数的相关问题

### 1.什么是函数

实现特定功能的n条语句的封装体

只有函数是可以执行的，其他类型的数据不能执行

### 2.为什么用函数

提高代码复用，减少代码量

便于阅读交流

### 3.如何定义函数

（1）函数声明

最先声明函数，无论在哪个位置调用该函数，都不会报错，最多只会返回undefined（因为存在变量提升）

~~~js
function f1(){
    ...
    ...
}
~~~

（2）表达式

~~~js
var f2=function(){
    ...
    ...
}
~~~

必须要先有顺序，即先定义函数，再后执行，否则会报错

### 4.如何调用（执行）函数

假设有一个函数test（）

（1）test（）直接调用

（2）对象.test（）通过对象调用

（3）new  test（）相当于用构造函数实例化一个对象时可以在括号内赋值

（4）test.call/apply（对象）临时让函数成为指定对象的方法

~~~js
var obj={};
function test(){
	this.xx="nihao";
}
test.call(obj);
console.log(obj.xx=="nihao");//结果为true
~~~

### 5.什么是回调函数

（1）自主定义的、由浏览器自己调用并执行的函数

（2）一个函数作为实参传入另一个函数的参数中，这种被作为参数的函数就是回调函数

## 七、IIFE

### 1.什么是IIFE

全称：Immediately-Invoked Function Expression

中文为：立即执行函数，也称 匿名函数自调用

语法如下：

~~~js
(function(){
    var a=1;
    console.log(a+2);
})()
~~~

### 2.作用

隐藏实现，即外部程序无法发现该函数，换句话说就是 不会污染外部（全局）命名空间

## 八、this

### 1.什么是this

任何函数本质上都是通过某个对象来调用的，如果没有指定则都是window

所有函数内部都有的一个变量this

它的值是调用当前函数的对象

### 2.如何确定this

由函数调用的，this都是window

由对象调用的，this都是该对象

test（）：window

p.test（）：p

new test（）：新创建的对象

P.call（obj）：obj

## 九、关于语句是否加分号的问题

![image-20210215144356375](D:\web self-learn\HTML+CSS\Js高级程序设计笔记.assets\image-20210215144356375.png)

## 十、关于原型的相关问题

### 1.函数的prototype属性

每个函数都有一个prototype属性，它默认指向一个Object空对象（一个空的空间，没有任何自己定义的属性或方法，即称为：原型对象）。换句话说就是，函数的显式原型指向的对象默认是一个空的Object实例对象，但Object函数除外

函数的显式原型指向的对象默认是一个空的Object实例对象，即 函数 . prototype==

~~~js
console.log(Object.prototype instanceof Object);
打印结果：
false
~~~

原型对象中有一个属性constructor，他指向函数对象

### 2.函数的prototype作用

函数的所有实例对象都自动拥有原型中的属性和方法

函数的任意一个实例对象想要调用原型中的属性或者方法时，可以直接调用

### 3.显式原型和隐式原型

每个函数都有一个prototype属性，即为显式原型

每个实例对象都有一个<span>_ _ _proto_ _ _</span>，即为隐式原型，在创建对象时会自动添加，默认值为构造函数的prototype属性

程序员可以直接操作显式原型，但不能直接操作隐式原型（ES6之前）

实例对象的<span>_ _ _proto_ _ _</span>与函数的prototype 相等

prototype和<span>_ _ _proto_ _ _</span>保存的都是地址值

在实例化对象时，实际上进行了一个操作：this.<span>_ _ _proto_ _ _</span>=函数名.prototype

### 4.内存中的行为

~~~js
function Fn（）{
    this.prototype={};
}
console.log(Fn.prototype);
var fn=new Fn();
console.log(fn._ _proto_ _);//隐式原型只能打印，不能进行操作
console.log(Fn.prototype==fn._ _proto_ _);
~~~

![image-20210215192905228](D:\web self-learn\HTML+CSS\Js高级程序设计笔记.assets\image-20210215192905228.png)

### 5.原型链

js中的内置对象其实就是内置的函数对象，例如Object、Window

一切对象最终都指向Object的原型对象的

（1）原型链的操作

访问一个对象的属性时，先在自身属性中查找，找到返回，没有则在<span>_ _ _proto_ _ _</span>中查找，找到返回，如果最终没找到就返回undefined

![image-20210215201001770](D:\web self-learn\HTML+CSS\Js高级程序设计笔记.assets\image-20210215201001770.png)

（2）函数的原型关系

所有函数对象都有一个隐式原型属性指向Function函数对象的显式原型

因为函数对象既是函数又是对象，所以既有显式原型也有隐式原型

分析：

(1)	函数对象是由Function实例化的一个对象，所以fun（假设有函数fun（））的_ _ _proto_ _ _<span style="font-weight:bold;color:red">等于</span>Function的prototype，可以延伸为 <span style="font-weight:bold;color:red">所有函数</span>的隐式原型都等于Function的显式原型

(2)	函数对象是一个函数所以，所以它的prototype<span style="font-weight:bold;color:red">等于</span>由当前函数对象实例化的任意对象的<span>_ _ _proto_ _ _</span>

![img](https://img-blog.csdnimg.cn/20191024152938201.jpg?x-oss-process=image/watermark,type_ZmFuZ3poZW5naGVpdGk,shadow_10,text_aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L3hpYW9rZTU0OTE=,size_16,color_FFFFFF,t_70)

（3）原型最重要的三个点

函数的显式原型所指向的对象默认是空Object实例对象，但Object除外

所有函数都是Function都是Function的实例，包括Function本身

Object的原型对象就是原型链的尽头，即 Object.prototype._ _ _proto_ _ _=null

### 6.原型的属性和方法规则

（1）在构造函数的prototype中添加属性后，读取对象的该属性，则会自动到原型链中查找

（2）设置对象的属性时，不会查找原型链，如果该对象中没有此属性，则直接在对象中添加属性

（3）方法一般定义在原型中，属性一般通过构造函数定义在对象本身上

### 7.instanceof

（1）表达式：A	instanceof	B

如果B函数的显式原型对象在A对象的原型链上，则返回true

## 十一、变量提升和函数提升

### 1.变量声明提升

通过var定义（声明）的变量，无论在什么位置（包括定义或声明之前），都可以访问到该变量，获取值为undefined或   已经赋值好的具体值

### 2.函数声明提升

通过 "function  函数名"   的方式声明的函数，无论在什么位置调用该函数，就算在函数声明之前也可以直接调用

### 3.变量声明提升和函数声明提升的优先级

函数声明优先于变量提升。

解析器在向执行环境中加载数据时会<span style="font-weight:bold;color:red">率先</span>读取函数声明，并使其在执行任何代码之前可用(可访问)，即函数声明提升优先

但是若变量被赋值了，则会原来的打印结果会被变量覆盖，打印结果是变量的值

~~~js
function a(){}
var a
console.log(a);//打印：f a(){}（表明是函数）
a=1;
console.log（a）//打印：1
~~~

## 十二、执行上下文

### 1.全局执行上下文 

在执行全局代码前将window确定为全局执行上下文

对全局数据进行预处理：

（1）var定义的全局变量，添加为window的属性

（2）function声明的全局函数，添加为window的方法

（3）this，被赋值为window

### 2.函数执行上下文 

在<span style="font-weight:bold;color:red">调用函数</span>，准备执行函数体<span style="font-weight:bold;color:red">之前</span>，创建对应的函数执行上下文对象（一个虚拟的栈）

对局部数据进行预处理：

（1）形参：赋值，添加为执行上下文的属性

（2）arguments：实参列表，添加为执行上下文的属性

（3）var 定义的局部变量，添加为上下文的属性

（4）function声明的函数，添加为上下文的方法

（5）this，赋值为调用函数的对象

注：函数内的局部变量执行完会释放

### 3.总体执行的大致情况

（1）在全局代码执行之前，js引擎会创建一个栈来存储管理所有的执行上下文对象

（2）在全局执行上下文（即为 window）确定后，将其添加到栈中（压栈）

（3）在函数执行上下文创建后，将其添加到栈中（压栈）

（4）在当前函数执行后，将栈顶对象移除（出栈）

（5）当所有的代码执行后，栈中只剩下window

### 4.相关面试题

~~~js
console.log("a:"+i);
var i=1;
foo(1);
function foo(i){
    if(i==4){
        return ;
    }
    console.log("b:"+i);
    foo(i+1);//递归
    console.log("c:"+i);
}
//输出：
//a:undefined
//b:1
//b:2
//b:3
//c:3
//c:2
//c:1
~~~

根据执行上下文的相关设定，将各执行上下文对象入栈，最后再自顶向下依次出栈

## 十三、作用域相关问题

### 1.作用域定义

一个代码段所在的区域

是静态的，在代码编写时就已经确定

### 2.作用域类别

（1）函数作用域 

（2）全局作用域

### 3.作用

隔离变量，不同作用域下同名变量不会有冲突

### 4.作用域和执行上下文的关系

（1）全局作用域之外，每个函数都会创建自己的作用域，作用域在函数定义时，就已经确定了，而不是在函数调用时

全局执行上下文环境是在全局作用域确定之后，js代码马上执行之前创建

（2）作用域是静态的，只要函数定义好就一直存在，不会有变化

执行上下文是动态的，调用函数时创建，函数调用结束后自动释放

（3）上下文环境（对象）是从属于所在的作用域

全局上下文环境==全局作用域

函数上下文环境==函数作用域

### 5.作用域链

从当前作用域中查找，没有就向外一级查，再没有直到最外层作用域（即全局作用域），如果一直找不到就报错

执行函数时，不是看函数被调用的位置，而是看要调用的函数原来所在的作用域

例题如下所示：

~~~js
var a=10;
function fn(){
    console.log(a);
}
function show(f){
	var a=20;
	f();
}
show(fn);
//打印输出：  10
~~~

## 十三、闭包的理解

例如获取多个相同元素时，用for循环给其绑上事件，由于for循环会在事件触发之前，所以触发时循环早已结束，会导致出错

此时可利用闭包原理来解决问题，代码如下所示：

~~~js
var btns=document.getElementsByTagName("button");
for(var i=0;i<btns.length;i++){
    (function(i){
        var btn=btns[i];
        btn.onclick=function(){
            alert("第"+(i+1)+"个按钮");
        }
    })(i)
}
~~~

### 1.闭包的定义

当一个嵌套的内部（子）函数引用了嵌套的外部（父）函数的变量（函数）时，就产生了闭包

而这样的函数内部的函数就是闭包函数

本质上来说，闭包就是将函数内部和函数外部连接起来的一座桥梁

### 2.常见的闭包

函数作为另一个函数的返回值

函数返回一个内部函数，而内部函数使用了外部函数的变量。

这样外部就可以访问该函数使用的变量

当外部函数执行完毕后，它的变量不会被销毁

### 3.闭包的作用

（1）使用函数内部的变量在函数执行完后，仍然存活于内存中（延长了局部变量的生命周期，但是会加大内存消耗）

```js
function ab(){
	var a=1;
	function bc(){
        a++
        console.log(a);
	}
	return bc;
}
var f=ab();
f();//打印：2
f();//打印：3
```
（2）让函数外部可以获取函数内部的数据（变量/函数）

（3）在函数外部不能直接访问函数内部的局部变量，但是通过闭包可以获取 

### 4.闭包的生命周期

产生：在嵌套内部函数定义执行完时就产生了（不是在调用）

死亡：在嵌套的内部函数成为垃圾对象时（即不用一个变量接收函数或者赋值为null）

### 5.闭包的应用

定义一个具有特定功能的js文件

将所有的数据和功能都封装在一个函数内部（私有）

只向外暴露一个包含n个方法的对象或函数

模块的使用者只需通过模块暴露的对象调用方法来实现对应的功能

有两种暴露的方法：

（1）return {.......}（使用前要先执行函数）

（2）window.属性名={...........}（使用时直接调用，效率快，但必须要放在一个立即执行函数内）

![image-20210221225430935](D:\web self-learn\HTML+CSS\Js高级程序设计笔记.assets\image-20210221225430935.png)

### 6.闭包的缺点

缺点：

​	函数执行后，函数内的局部变量没有释放，占用内存时间变长

​	容易造成内存泄露

解决：

​	能不用闭包就不用

​	及时释放（将对象赋值为null）

### 7.内存溢出和内存泄露

（1）内存溢出：

​	一种程序运行出现的错误

​	当程序运行需要的内存超过了剩余的内存时，就会抛出内存溢出的错误（即要运行的程序占用的内存太多）

（2）内存泄露：

​	不再使用的内存没有及时释放就是内存泄露，没有及时释放会导致内存占用越来越高

​	内存泄露积累多了容易导致内存溢出

​	常见的内存泄露：

​			意外的全局变量

​			没有及时清理的计时器或回调函数

​			闭包

### 8.闭包例题

~~~js
function fun(m,n){
    console.log(n);
    return {
        fun:function (a) {
            //此处的参数m调用了外部函数变量的第一个参数m，形成闭包
            return fun(a,m);
        }
    }
}
var a=fun(0);//undefined
a.fun(1)//0,此处新形成了闭包，但是很快就抛弃了
a.fun(2)//0
a.fun(3)//0
//以上始终只调用了a的闭包
console.log("----------------------------------------------------")
var b=fun(0).fun(1).fun(2).fun(3)//undefined,0,1,2
console.log("----------------------------------------------------")
var c=fun(0).fun(1)//undefine,0
c.fun(2)//1
c.fun(3)//1
~~~

## 十四、进程和线程

### 1.进程

程序的一次执行，会占有一片独立的空间

可以通过windows任务管理器查看进程

一个程序可能有多个进程，称之为多进程应用

### 2.线程

线程是进程内的一个独立执行单元

是程序执行的一个完整流程

是CPU的最小的调度单元

一个进程可以有多个线程执行，称之为多线程程序

### 3.线程和进程

应用程序必须运行在某个进程的某个线程上

一个进程中至少有一个运行的线程：主线程，进程启动后自动创建

一个进程中也可以同时运行多个线程，可以说程序是多线程运行的

一个进程内的数据可以供其中的多个线程直接共享

多个进程之间的数据是不能直接共享的

线程池（thread pool）：保存多个线程对象的容器，实现线程对象的反复利用

单核也可以创建多个线程

### 4.线程的优缺点

（1）多线程

优点：

​	能有效提升CPU的利用率

​	创建多线程开销

缺点：

​	线程间切换开销

​	死锁与状态同步问题

（2）单线程

优点：

​	顺序编程简单易懂

缺点：

​	效率低

### 5.js的进程

js是单线程运行的

但使用H5的web workers可以多线程运行

## 十五、浏览器内核

浏览器内核是支撑浏览器运行的最核心的程序

不同的浏览器的内核可能不一样 

### 1.内核的组成

主线程中：

​		js引擎模块：负责js程序的编译和运行

​		HTML，CSS文档解析模块：负责页面文本的解析

​		DOM/CSS模块：负责DOM/CSS在内存中的相关处理

​		布局和渲染模块：负责页面的布局和效果的绘制（内存中的对象 ）

分线程中：

​		定时器模块：负责定时器的管理

​		DOM事件响应模块：负责事件的管理

​		网络请求模块：负责ajax请求

注：分线程的全局对象不再是window

## 十六、定时器

### 1.定时器真的是定时执行的吗

定时器并不能保证真正定时执行

一般会延时一点（可以接受），但是有时候会延时很多（不能接受）

### 2.定时器回调函数是在分线程执行的吗

不是，在主线程执行的，js代码都是由主线程的js引擎模块执行，js是单线程的

### 3.定时器如何实现

事件循环模型

## 十七、js执行是单线程

### 1.js执行是单线程的

setTimeout（）的回调函数是在主线程执行的

定时器回调函数只有在运行栈中的代码全部执行完后才有可能执行

### 2.js执行为什么是单线程的

js的单线程与它的用途有关

作为浏览器脚本语言，js的主要用途是与用户互动，以及操作DOM

这决定了它只能是单线程的，否则会带来复杂的同步问题

### 3.代码的分类

初始化代码：包含绑定dom事件监听，设置定时器，发送ajax请求的代码

回调代码：处理回调逻辑

### 4.js引擎执行代码的基本流程

先执行初始化代码：包含一些特别的代码   回调函数（异步执行）

设置定时器

绑定监听

发送ajax请求

后面在某个时刻才会执行回调代码

### 5.Web Workers

可以让js在分线程工作，让js多线程工作

![image-20210221010300415](D:\web self-learn\HTML+CSS\Js高级程序设计笔记.assets\image-20210221010300415.png)

worker内代码不能操作DOM更新UI

不是每个浏览器都支持这个新特性

不能跨域加载js



## 十八、事件循环模型

### 1.模型原理图

从任务队列中循环取出回调函数放入执行栈中处理

![image-20210220233857172](D:\web self-learn\HTML+CSS\Js高级程序设计笔记.assets\image-20210220233857172.png)

### 2.模型的两个重要组成部分

事件管理模块

回调队列

### 3.模型的运转流程

执行初始化代码，将事件回调函数交给对应模块管理

当事件发生时，管理模块会将回调函数及其数据添加到回调队列中

只有当初始化代码执行完后（可能需要一定时间），才会遍历读取回调队列中的回调函数执行

## 十九、H5的Web Workers多线程

### 1.介绍

Web Workers是HTML5提供的一个js多线程解决方案

可以将一些大计算量的代码交由Web Workers（分线程）运行而不冻结用户界面

但是子线程完全受主线程控制，而不得操作DOM，所以这个新标准没有改变js单线程的本质

### 2.使用

 ![image-20210221190827554](D:\web self-learn\HTML+CSS\Js高级程序设计笔记.assets\image-20210221190827554.png)

### 3.缺点

慢

不能跨域加载js

worker内代码不能访问DOM（更新UI）（因为全局对象不再是window）

不是每个浏览器都支持这个新特性

## 二十、继承

### 1.原型链继承

以下所说的“类型”即为构造函数

利用原型链来实现子类型对父类型的继承

将子类的显示原型指向父类的实例对象即可实现继承

此时，子类的一个实例化对象的构造函数变成了父类型，这是不好的，应当将其变为其本身

通过   子类型.prototype.constructor=子类型    的语句来实现

![image-20210221202546776](D:\web self-learn\HTML+CSS\Js高级程序设计笔记.assets\image-20210221202546776.png)

### 2.借用构造函数继承

~~~js
function Person(name,age){
    this.name=name;
    this.age=age;
}
function Student(name,age,price){
    //相当于this.Person(name,age)
    Person.call(this,name,age);
    this.price=price;
}
var s=new Student("Tom",20,120)
console.log(s.name,s.age,s.price);

//打印："Tom" 20 120
~~~

利用call方法将另一个构造函数的属性或方法借用在自身构造函数内，然后可以创建自身构造函数的一个实例化对象来调用 对应的 属性、方法

### 3.组合继承（将1和2两种继承方法结合起来）

~~~js
function Person(name,age){
    this.name=name;
    this.age=age;
}
Person.prototype.setName=function(name){
    this.name=name;
}
function Student(name,age,price){
    //相当于this.Person(name,age),得到其他函数的属性
    Person.call(this,name,age);
    this.price=price;
}
Student.prototype=new Person();//将子类的原型指向一个实例对象，为了能得到父类的方法
Student.prototype.constructor=Student;//修正constructor属性
Student.prototype.setPrice=function(price){
    this.price=price;

}

var s=new Student("Tom",20,120);
s.setName("Jery");
s.setPrice(160);
console.log(s.name,s.age,s.price);
~~~

<h2>注意点</h2>

（1）return后可以返回任意类型值，如果return 后的内容在一个大括号内表示一个无名对象

~~~js
var a=1;
function test(){
    console.log(++a);
}
window.$=function(){
    return {test:test}//此处返回一个对象，对象中的是一个方法
}
~~~

（2）全局变量和函数就是window对象的属性和方法

（3）Function也是由Function（）构造函数实例化得来的一个函数对象，所以它的隐式原型等于Function 的显式原型

（4）Object（）也是一个构造函数，所以它也是由Function实例化而来，所以Object的隐式原型等于Function . prototype

（5）在函数中定义变量时不用var定义，在函数执行后变量无法释放

（6）alert（）语句可以起到暂停打印和计时器的作用（暂停当前主线程的执行，点击确定后恢复）

（7）查找对象中不存在的属性时，不会报错，而是返回undefined

（8）对象中的方法里若声明并执行了一个函数，则因为该方法由对象调用，但是方法中的函数不是由对象调用的，而是在window中声明的，所以此时的this是window

若想改变this，则可以用call或apply方法

~~~js
var a = {
            
    b: function () {

        var func = function () {
            console.log(this.c);

        }
        func();
    },
    c: 'hello'
}
a.b(); // undefined 这里的this指向的是全局作用域
console.log(a.c); // hello
~~~

