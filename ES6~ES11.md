[TOC]- ES6~ES11
- [一、ES6简介](#一es6简介)
- [二、let变量声明](#二let变量声明)
  - [1.不能重复声明](#1不能重复声明)
  - [2.块级作用域](#2块级作用域)
  - [3.变量提升](#3变量提升)
  - [4.作用域链](#4作用域链)
- [三、const变量声明](#三const变量声明)
  - [1.初始化](#1初始化)
  - [2.大小写](#2大小写)
  - [3.常量不能修改值](#3常量不能修改值)
  - [4.作用域](#4作用域)
  - [5.数组和对象](#5数组和对象)
- [四、变量的解构赋值](#四变量的解构赋值)
  - [1.数组的解构赋值](#1数组的解构赋值)
  - [2.对象的解构赋值](#2对象的解构赋值)
  - [3.解构默认值](#3解构默认值)
- [五、模板字符串](#五模板字符串)
- [六、对象写法的简化](#六对象写法的简化)
- [七、箭头函数](#七箭头函数)
  - [1.与普通函数声明的差别](#1与普通函数声明的差别)
  - [2.箭头函数的实践](#2箭头函数的实践)
- [八、严格模式](#八严格模式)
- [九、函数参数](#九函数参数)
  - [1.形参初始值](#1形参初始值)
  - [2.与解构赋值结合](#2与解构赋值结合)
  - [3.rest参数](#3rest参数)
- [十、扩展运算符](#十扩展运算符)
  - [1.与arguments的差别](#1与arguments的差别)
  - [2.扩展运算符的应用](#2扩展运算符的应用)
- [十一、Symbol数据类型](#十一symbol数据类型)
  - [1.Symbol的基本语法](#1symbol的基本语法)
  - [2.Symbol.for](#2symbolfor)
  - [3.在对象中使用](#3在对象中使用)
  - [4.内置属性](#4内置属性)
- [十二、迭代器](#十二迭代器)
  - [1.基本使用](#1基本使用)
  - [2.工作原理](#2工作原理)
  - [3.为对象自定义iterator接口](#3为对象自定义iterator接口)
  - [4.生成器](#4生成器)
- [十三、Promise](#十三promise)
  - [1.基本使用](#1基本使用-1)
  - [2.文件读取](#2文件读取)
  - [3.封装ajax操作](#3封装ajax操作)
  - [4.读取多个文件](#4读取多个文件)
  - [5.then方法](#5then方法)
  - [6.catch方法](#6catch方法)
- [十四、集合Set](#十四集合set)
  - [1.Set的基本使用](#1set的基本使用)
  - [2.Set的实践](#2set的实践)
- [十五、Map](#十五map)
- [十六、class类](#十六class类)
  - [1.声明](#1声明)
  - [2.静态成员](#2静态成员)
  - [3.继承](#3继承)
  - [4.重写](#4重写)
  - [5.get和set](#5get和set)
- [十七、数值扩展](#十七数值扩展)
  - [1.Number.EPSILON](#1numberepsilon)
  - [2.Number.isFinite](#2numberisfinite)
  - [3.Number.isNaN](#3numberisnan)
  - [4.Number.parseInt和Number.parseFloat](#4numberparseint和numberparsefloat)
  - [5.Number.isInteger](#5numberisinteger)
  - [6.Math.trunc](#6mathtrunc)
  - [7.Math.sign](#7mathsign)
- [十八、对象方法的扩展](#十八对象方法的扩展)
  - [1.Object.is](#1objectis)
  - [2.Object.assign](#2objectassign)
  - [2.Object.setPrototypeOf和Object.getPrototypeOf](#2objectsetprototypeof和objectgetprototypeof)
- [十九、模块化](#十九模块化)
  - [1.基本使用](#1基本使用-2)
  - [2.暴露数据的语法](#2暴露数据的语法)
  - [3.引入模块数据的语法](#3引入模块数据的语法)
  - [4.模块化引入模块规范](#4模块化引入模块规范)
  - [5.ES6模块化代码在项目的使用](#5es6模块化代码在项目的使用)
  - [6.在ES6中引入npm包](#6在es6中引入npm包)
- [二十、ES7新特性](#二十es7新特性)
  - [1.includes](#1includes)
  - [2.幂运算**](#2幂运算)
- [二十一、ES8新特性](#二十一es8新特性)
  - [1.async函数](#1async函数)
  - [2.对象方法扩展](#2对象方法扩展)
- [二十二、ES9新特性](#二十二es9新特性)
  - [1.对象中的扩展运算符和rest参数](#1对象中的扩展运算符和rest参数)
  - [2.正则扩展](#2正则扩展)
- [二十三、ES10新特性](#二十三es10新特性)
  - [1.Object.fromEntries](#1objectfromentries)
  - [2.字符串方法扩展](#2字符串方法扩展)
  - [3.数组方法扩展](#3数组方法扩展)
  - [4.Symbol.description](#4symboldescription)
- [二十四、ES11新特性](#二十四es11新特性)
  - [1.私有属性](#1私有属性)
  - [2.Promise.allSettled](#2promiseallsettled)
  - [3.String.matchAll](#3stringmatchall)
  - [4.可选链操作符](#4可选链操作符)
  - [5.动态import](#5动态import)
  - [6.新的数据类型BigInt](#6新的数据类型bigint)
  - [7.globalThis](#7globalthis)
- [学习过程中忘记的知识点](#学习过程中忘记的知识点)
  - [1.for循环绑定单击响应函数的相关问题的解决](#1for循环绑定单击响应函数的相关问题的解决)
  - [2.异步](#2异步)
  - [3.实现异步编程的几种方法](#3实现异步编程的几种方法)

## 一、ES6简介

ES6，全称ECMAScript6

ECMA中文名称为欧洲计算机制造商协会，这个组织的目标是评估、开发和认可电信和计算机标准。1994年后该组织改名为ECMA国际

ECMAScript 是由ECMA国际通过ECMA-262标准化的脚本程序设计语言（ECMA-262是众多标准中的一个版本）

## 二、let变量声明

JavaScript缺乏范围清晰性，常导致开发和故障排除的失败。以下是JavaScript使用var声明变量的范围异常的摘要：

· 一个变量可以使用两次var（重声明）

· 默认情况下，顶级变量是全局变量（全局对象）

· 可以在声明前使用变量（提升）

· 循环中的变量重复使用同样的引用（闭包）

### 1.不能重复声明

使用let定义的变量名不能重复定义，否则会报错

~~~js
let a=1;
let a='1';

//报错信息:
//Uncaught SyntaxError: Identifier 'a' has already been declared
~~~

这与var不同

### 2.块级作用域

let 是块级作用域，只能作用于代码块中（只要有中括号就是代码块）

~~~js
{
	let a=1;
}
console.log(a);
//无法打印，会报错
~~~

与var不同，var定义的变量是全局的或是局部函数的

### 3.变量提升

不存在变量提升

### 4.作用域链

let声明的变量虽然是块级作用域，但是不影响作用域链的效果

## 三、const变量声明

### 1.初始化

const声明的变量必须要赋初值，进行初始化

### 2.大小写

一般常亮使用大写，这是一种潜规则

### 3.常量不能修改值

常量的值不能修改

### 4.作用域

const声明的变量是块级作用域

### 5.数组和对象

对于数组和对象中的值进行修改，不算对常量进行修改，是可以的，不会报错

因为对象是保存的地址值，只要不改地址值就不算修改变量



## 四、变量的解构赋值

解构赋值是对赋值运算符的扩展。

他是一种针对数组或者对象进行模式匹配，然后对其中的变量进行赋值。

在代码书写上简洁且易读，语义更加清晰明了；也方便了复杂对象中数据字段获取。

ES6允许按照一定模式从数组和对象中提取值，对变量进行赋值

这被称为<span style="color:red;font-weight:bold">解构赋值</span>

### 1.数组的解构赋值

~~~js
const mn4=['王昭君','西施','貂蝉','杨玉环'];

let [wang,xi,diao,yang]=mn4;

console.log(xi);
console.log(wang);
console.log(diao);
console.log(yang);
/*打印结果:
    西施
    王昭君
    貂蝉
    杨玉环
*/
~~~

### 2.对象的解构赋值

~~~js
const mn={
    name:'貂蝉',
    age:18,
    action:function(){
    	console.log('操我');
	}
}
let {name,age,action}=mn;
console.log(mn.name);//貂蝉
console.log(name);//貂蝉

~~~

此处进行 解构操作，变量名必须要和对象内的属性名相同

~~~js
let { foo, bar } = { foo: 'aaa', bar: 'bbb' };
// foo = 'aaa'
// bar = 'bbb'
 
let { baz : foo } = { baz : 'ddd' };
// foo = 'ddd'

~~~

### 3.解构默认值

当解构模式有匹配结果，且匹配结果是 undefined或为空 时，会触发默认值作为返回结果。

数组解构默认值

~~~js
let [a = 2] = [undefined]; // a = 2
let [a = 3, b = a] = [];     // a = 3, b = 3
let [a = 3, b = a] = [1];    // a = 1, b = 1
let [a = 3, b = a] = [1, 2]; // a = 1, b = 2
~~~

对象解构默认值

~~~js
let {a = 10, b = 5} = {a: 3};
// a = 3; b = 5;

//此处实际相当于先将a的值赋给aa，b的值赋给了bb
//再进行匹配赋值
//而此时相当于只定义了aa和bb，所以只能打印aa和bb
let {a: aa = 10, b: bb = 5} = {a: 3};
// aa = 3; bb = 5;
~~~

## 五、模板字符串

引入的新的声明字符串的方式 

反引号:  `

（1）声明

~~~js
const str=`你过来啊`;
console.log(str)
~~~


（2）内容中可以直接出现换行符（单引号和双引号中无法换行）

~~~js
let str=`<ul>
			<li>你好</li>
			<li>你好</li>
		 </ul>`;
~~~

（3）字符串拼接

变量放在中括号内，前面再加上$，表示在当前字符串中引用变量

注：被引用的变量可以不是用 反引号 声明的，但是引用变量的当前字符串必须用  反引号 声明

~~~js
const base=`qy`;//反引号声明变量
const out=`${base}是大帅比`;
console.log(out) 	//qy是大帅比

const base='qy';//引号声明变量
const out=`${base}是大帅比`;
console.log(out)
~~~

## 六、对象写法的简化

~~~js
let name='qy';
let action=function(){
    console.log('我是函数');
}
const shi={
    name,
    action
}
console.log(shi)
/*打印结果：
{name: "qy", action: ƒ}
action: ƒ ()
name: "qy"
__proto__: Object
*/
~~~

并且对象中的方法声明时，可以省去	"	:function	"

~~~js
const shi={
    name,
    action,
    action2(){
        console.log('这是action2函数')
    }
}
console.log(shi)
/*打印结果：
{name: "qy", action: ƒ, action2: ƒ}
action: ƒ 
()action2: ƒ action2()
name: "qy"
__proto__: Object
*/
~~~

## 七、箭头函数

箭头函数声明与普通函数声明并无太大差别

~~~js
let fn=(a)=>{       
    console.log(`fn是一个${a}`);
}       
fn('箭头函数');
//fn是一个箭头函数
~~~

### 1.与普通函数声明的差别

（1）this是静态的。

this始终指向函数声明时所在的作用域下的this的值

也可以理解为，箭头函数没有this，它的this为当前所在的外层作用域的this

~~~js
function fn(){
    console.log(this.name);
}
let fn2=()=>{
    console.log(this.name);
}
name='qy'
const nameobj={
    name:'qyqq'
}
fn();//qy
fn2();//qy

//哪怕是使用call函数强制改变this值，也无法改变箭头函数的this
fn.call(nameobj);//qy哥哥
fn2.call(nameobj);//qy
~~~

（2）箭头函数无法作为构造函数实例化对象

~~~js
let Person=(name,gender)=>{
    this.namne=name;
    this.gender=gender;
}
let jia=new Person('路人甲','男');
console.log(jia)

//Uncaught TypeError: Person is not a constructor
~~~

（3）不能使用arguments变量

~~~js
//普通函数声明
function fn3(a,b,c){
	console.log(arguments);
}
fn3(1,2,3);
//Arguments(3) [1, 2, 3, callee: ƒ, Symbol(Symbol.iterator): ƒ]

//箭头函数声明
var fn3=(a,b,c)=>{
    console.log(arguments);
}
fn();
//Uncaught ReferenceError: arguments is not defined
~~~

（4）箭头函数的简写

1）当形参只有一个的时候，可以省略参数的小括号

~~~js
let fn3=a=>{
    return a+a;
}
console.log(fn3(2))
//4
~~~

2）当代码体只有一条语句时，此时return必须省略，则语句的执行结果就是函数的返回值

~~~js
let fn4=a=>a*a
console.log(fn3(2))
//4
~~~

（5）箭头函数的使用场景

箭头函数适用于与this无关的回调，例如：定时器、数组的方法

### 2.箭头函数的实践

（1）定时器是window的方法，所以定时器下的this指向window

1）如果想改变this，可以在定时器外保存this，再在定时器内使用

~~~js
let ad=document.getElementById('ad')

ad.addEventListener('click',function(){
    //保存this，此时的this指向ad选择器
    let _this=this;
    setInterval(function(){
        //使用上面保存的this
        _this.style.background='yellow'
    },2000)
})
~~~

2）可以利用箭头函数的特性来使用

this始终静态，是当前作用域下的this的值

~~~js
let ad=document.getElementById('ad')
ad.addEventListener('click',function(){
	//箭头函数，当前this在定时器内，定时器在ad绑定的事件内
    setInterval(()=>{
        this.style.background='yellow'
    },2000)
})
~~~

## 八、严格模式

在js最上方写上

~~~js
'use strict'
~~~

表示开启了严格模式

现代浏览器都支持strict模式，一旦它执行到这行代码，就会开启strict模式运行javascript

strict模式下运行的JavaScript，强制使用var来声明变量，未使用var声明变量就使用的，将导致ReferenceError运行错误。

未使用var声明就使用的变量，会被自动声明为全局变量，但是如果在同一页面出现多个同名的变量时，变量之间就会相互影响，也无法调试。

在严格模式下，使用var声明的变量则不是全局变量，它的范围被限制在该变量被声明的函数体内，同名变量在不同的函数体内互不冲突。

## 九、函数参数

允许给函数参数设置初始值

实参没有，但是有初始值，则结果为初始值

若有实参，且有初始值，则结果为实参（实参覆盖了初始值）

### 1.形参初始值

具有默认值的参数，一般放在参数后面

~~~js
function fn(a=1,b=2){
	console.log(a,b)
}
fn()//1 2
~~~

### 2.与解构赋值结合

~~~js
//对象解构赋值
function fn({host,username,password}){
    //直接调用对象中的属性
    console.log(host);
    console.log(username);
    console.log(password);
}
fn({
    host:'localhost',
    username:'root',
    password:'rootp'
})

~~~

同样的，对象参数中的属性也可以赋初值，原理同上

### 3.rest参数

rest参数的声明是在函数的形参内

（1）ES6中引入了rest参数来获取函数的实参，用来代替arguments

~~~js
//此处的args为自定义变量，不是固定写法
function fn2(...args){
    console.log(args)
}
fn2(1,2,3)
//(3) [1, 2, 3]
~~~

和arguments不同，rest参数返回的是一个数组，而不是对象

所以，可以使用数组的相关方法，更加灵活

（2）rest参数必须要在形参最后

~~~js
function fn3(a,b,...args){
    console.log(a)
    console.log(b)
    console.log(args)
}
fn3(1,2,3,4,5);
/*
1
2
(3) [3, 4, 5]
*/
~~~

## 十、扩展运算符

将字符串、集合、字符串等	转为逗号分隔的  元素数组

扩展运算符在传实参时写入

语法：	...变量名

### 1.与arguments的差别

arguments打印

只有一个参数，且参数为一个数组

~~~js
const mn=['貂蝉','西施','王昭君','杨玉环']
function bed(){
    console.log(arguments)
}
bed(mn)
/*打印结果:
Arguments [Array(4), callee: ƒ, Symbol(Symbol.iterator): ƒ]
0: (4) ["貂蝉", "西施", "王昭君", "杨玉环"]
callee: ƒ bed()
length: 1
Symbol(Symbol.iterator): ƒ values()
__proto__: Object
*/
~~~

扩展运算符将数组原来的一个arguments参数，分隔为了arguments的四个参数

参数为4个

~~~js
const mn=['貂蝉','西施','王昭君','杨玉环']
function bed(){
	console.log(arguments)
}
bed(...mn)
/*打印结果:
Arguments(4) ["貂蝉", "西施", "王昭君", "杨玉环",callee:f，Symbol（Symbol.iterator）:f]
0: "貂蝉"
1: "西施"
2: "王昭君"
3: "杨玉环"
callee: ƒ bed()
length: 4
Symbol(Symbol.iterator): ƒ values()
__proto__: Object
*/
~~~

### 2.扩展运算符的应用

（1）数组合并

~~~js
const arr1=['貂蝉','杨玉环']
const arr2=['西施','王昭君']
const arr=[...arr2,...arr1]
console.log(arr)
//(4) ["西施", "王昭君", "貂蝉", "杨玉环"]
~~~

（2）数组克隆

~~~js
const arry=['A','B','C']
const arrynew=[...arry]
console.log(arrynew)
//(3) ["A", "B", "C"]
~~~

（3）将伪数组转为真正的数组

~~~js
var divs=document.getElementsByTagName('div')
console.log([...divs])
//(3) [div, div, div]
~~~

## 十一、Symbol数据类型

ES6中引入的新的数据类型，表示独一无二的值。是js的第七种数据类型，是一种类似字符串的数据类型

Symbol 函数栈不能用 new 命令，因为是一种原始数据类型，不是对象。

可以接受一个字符串作为参数，为新创建的 Symbol 提供描述，用来显示在控制台或者作为字符串的时候使用，便于区分。

### 1.Symbol的基本语法

~~~js
let sy = Symbol("KK");
console.log(sy);   // Symbol(KK)
typeof(sy);        // "symbol"
 
// 相同参数 Symbol() 返回的值不相等
let sy1 = Symbol("kk"); 
sy === sy1;       // false
~~~

### 2.Symbol.for

和 Symbol()不同的是，用 Symbol.for()方法创建的的 symbol 会被放入一个全局 symbol 注册表中。Symbol.for() 并不是每次都会创建一个新的 symbol，它会首先检查给定的 key 是否已经在注册表中了。假如是，则会直接返回上次存储的那个。否则，它会再新建一个。

~~~js
Symbol.for("foo"); // 创建一个 symbol 并放入 symbol 注册表中，键为 "foo"
Symbol.for("foo"); // 从 symbol 注册表中读取键为"foo"的 symbol


Symbol.for("bar") === Symbol.for("bar"); // true，证明了上面说的
Symbol("bar") === Symbol("bar"); // false，Symbol() 函数每次都会返回新的一个 symbol


var sym = Symbol.for("mario");
sym.toString();
// "Symbol(mario)"，mario 既是该 symbol 在 symbol 注册表中的键名，又是该 symbol 自身的描述字符串
~~~

### 3.在对象中使用

向对象中添加方法

~~~js
let game={
            name:'qy',
            down:function(){

            },
            up:function(){

            },
            age:18
        }
let method={
    up:Symbol(),
    down:Symbol()
}
game[method.down]=function(){
    console.log('下降')
}
game[method.up]=function(){
    console.log('提升')
}
console.log(game)
/*
{name: "qy", age: 18, down: ƒ, up: ƒ, Symbol(): ƒ, …}
age: 18
down: ƒ ()
name: "qy"
up: ƒ ()
Symbol(): ƒ ()
Symbol(): ƒ ()
__proto__: Object
*/
~~~

在对象中添加Symbol方法，要加上中括号

~~~js
let down=Symbol('say')
let up=Symbol('zibao')
let zidingyi={
    name:'qy',
    [down]:function(){
        console.log('say')
    },
    [up]:function(){
        console.log('zib')
    }
}
zidingyi[down]();
~~~

### 4.内置属性

当使用Symbol类型数据被某些方法调用或者使用某些方法时，会自动触发特定的内置属性，不需要手动执行内置方法

（1）Symbol.hasInstance

对象的Symbol.hasInstance属性，指向一个内部方法，当其他对象使用instanceof运算符，判断是否为该对象的实例时，会调用这个方法

~~~js
class Person {}
let p1 = new Person;
console.log(p1 instanceof Person); //true
// instanceof  和  [Symbol.hasInstance]  是等价的
console.log(Person[Symbol.hasInstance](p1)); //true
console.log(Object[Symbol.hasInstance]({})); //true


//Symbol内置值得使用，都是作为某个对象类型的属性去使用
class Person {
    static[Symbol.hasInstance](params) {
        console.log(params)
        console.log("有人用我来检测类型了")
        //可以自己控制 instanceof 检测的结果
        return true
        //return false
    }
}
let o = {}
console.log(o instanceof Person)    //重写为true

~~~

（2）Symbol.isConcatSpreadable

值为布尔值，表示该对象用于Array.prototype.concat()时，是否可以展开

~~~js
let arr = [1, 2, 24, 23]
let arr2 = [42, 25, 24, 235]
//控制arr2是否可以展开
arr2[Symbol.isConcatSpreadable] = false
console.log(arr.concat(arr2)) //(5)[1, 2, 24, 23, Array(4)]
//若是true
arr2[Symbol.isConcatSpreadable] = true
console.log(arr.concat(arr2)) //(8) [1, 2, 24, 23, 42, 25, 24, 235]
~~~

## 十二、迭代器

迭代： 在多次循环中**逐步接近结果**

迭代器是一种接口，为各种不同的数据结构提供了统一的访问机制

任何数据结构只要部署Iterator接口，就可以完成遍历操作

Iterator接口：在数据结构中的一个属性。Iterator 接口的目的，**就是为所有数据结构，提供了一种统一的访问机制**，即for…of循环（详见下文）。当使用for…of循环遍历某种数据结构时，该循环会<span style="color:red;font-weight:bold">自动去寻找 Iterator 接口</span>。

**一种数据结构只要部署了Symbol.Iterator 接口，我们就称这种数据结构是“可遍历的”（iterable）**。

ES6创造了一种新的遍历命令for...of循环，Iterator接口主要供for...of调用

原生具有Iterator接口的数据有：Array、Arguments、String等等

### 1.基本使用

~~~js
const xiyou=['西施','王昭君','貂蝉','杨玉环']
        
for(let v in xiyou){
    console.log(v)//0	1	2	3
}

for(let v of xiyou){
    console.log(v)//西施	王昭君	貂蝉	杨玉环
}
~~~

### 2.工作原理

a）创建一个指针对象，指向当前数据结构的起始位置
b）第一次调用对象的next方法，指针自动指向数据结构的第一个成员
c）接下来不断的调用next方法，指针一直往后移动，直到指向最后一个成员
d）每调用next方法返回一个包含value和done属性的对象，当value的值为undefined时，done的值为true，当done的值为true时，调用终止。且此时value值为undefined

~~~js
const xiyou=['西施','王昭君','貂蝉','杨玉环']
let iter = xiyou[Symbol.iterator]();
console.log(iter.next());//{value: "西施", done: false}
console.log(iter.next());//{value: "王昭君", done: false}
console.log(iter.next());//{value: "貂蝉", done: false}
console.log(iter.next());//{value: "杨玉环", done: false}
console.log(iter.next());//{value: undefined, done: true}
~~~

### 3.为对象自定义iterator接口

~~~js
const banji={
    name:'zji',
    mn:['西施','王昭君','貂蝉','杨玉环'],
    [Symbol.iterator](){
        let index=0;
        let _this=this;//此时this是banji这个对象
        return{
            next:function(){
                if(index<_this.mn.length){
                    const result={value:_this.mn[index],done:false}
                    index++;
                    return result;
                }
                else{
                    return {value:undefined,done:true};
                }
            }
        }
    }
}

for(let v of banji){
    console.log(v);//西施	王昭君	貂蝉	杨玉环
}
~~~

### 4.生成器

生成器是一种惰性的序列，它支持一边读取数据，一边生成数据，如果数据比较大时，这种机制能节省很多内容空间。JavaScript 在 ES6 标准中也新增了对生成器的支持。

生成器返回的是一个迭代器

yield是ES6的新关键字，使生成器函数执行暂停，yield关键字后面的表达式的值返回给生成器的调用者。它可以被认为是一个基于生成器的版本的return关键字。（类似于return，加上return语句会暂停）

yield关键字实际返回一个IteratorResult（迭代器）对象，它有两个属性，value和done，分别代表返回值和是否完成。

yield无法单独工作，需要配合generator(生成器)的其他函数，如next，懒汉式操作，展现强大的主动控制特性。

`yield`表达式本身没有返回值，或者说总是返回`undefined`。`next()`方法可以带一个参数，该参数就会被当作上一个`yield`表达式的返回值。

如果yield在其他表达式中，需要用()单独括起来

（1）定义生成器

~~~js
function * gen(){
	console.log('hello')
}
let iter=gen()
console.log(iter)
/*打印结果：
gen {<suspended>}
__proto__: Generator
__proto__: Generator
constructor: GeneratorFunction {prototype: Generator, Symbol(Symbol.toStringTag): "GeneratorFunction", constructor: ƒ}
next: ƒ next()
return: ƒ return()
throw: ƒ throw()
Symbol(Symbol.toStringTag): "Generator"
__proto__:
Symbol(Symbol.iterator): ƒ [Symbol.iterator]()
__proto__: Object
[[GeneratorLocation]]: 13生成器.html:12
[[GeneratorState]]: "suspended"
[[GeneratorFunction]]: ƒ * gen()
[[GeneratorReceiver]]: Window
[[Scopes]]: Scopes[3]
*/
~~~

若想打印生成器内的输出语句

~~~js
function * gen(){
	console.log('hello')
}
let iter=gen()
iter.next();//hello
~~~

（2）生成器的调用

1）只打印生成器内的输出语句

~~~js
function* gen2(){
    console.log(1)
    yield '已知';
    console.log(2)
    yield '未知';
    console.log(3)

}
let iter=gen2();
iter.next();//1
iter.next();//2
iter.next();//3

~~~

2）打印生成器内的输出语句和yield字符串

~~~js
function* gen2(){
    console.log(1)
    yield '已知';
    console.log(2)
    yield '未知';
    console.log(3)

}
let iter=gen2();
console.log(iter.next())
console.log(iter.next())
console.log(iter.next())
/*打印结果：
1
{value: "已知", done: false}
2
{value: "未知", done: false}
3
{value: undefined, done: true}
*/
~~~

（3）生成器的参数

~~~js
function *gen(args){
            
    console.log(args)
    let one=yield 111;
    console.log(one)
    yield 222;

    yield 333;
}
let iter=gen('args');
console.log(iter.next())
console.log(iter.next('BB'))
/*
args
{value: 111, done: false}
BB
{value: 222, done: false}
*/
~~~

next方法中传入的实参就是yield语句返回的结果

第二个next方法中的实参是第一个yield语句返回的结果

第三个next方法中的实参是第二个yield语句返回的结果

（4）生成器的实例

回调地狱：多个嵌套的回调函数

为解决回调地狱，可以利用生成器来实现

~~~js
function one(){
    setTimeout(()=>{
        console.log(111)
    },1000)
}
function two(){
    setTimeout(()=>{
        console.log(222)
    },3000)
}
function three(){
    setTimeout(()=>{
        console.log(333)
    },2000)
}

function *gen(){
    yield one()

    yield two()
    yield three()
}
let iter=gen()
iter.next();
iter.next();
iter.next();
~~~

上述方法会导致执行生成器时，不会按顺序执行，而是按照时间来执行，且每个延时器的间隔为当前减去上一个延时器的时间（上述例子中是每个延时器只间隔一秒）

~~~js
function one(){
    setTimeout(()=>{
        console.log(111)
        iter.next();
    },1000)
}
function two(){
    setTimeout(()=>{
        console.log(222)
        iter.next();
    },3000)
}
function three(){
    setTimeout(()=>{
        console.log(333)
        iter.next();
    },2000)
}

function *gen(){
    yield one()

    yield two()
    yield three()
}
let iter=gen()
iter.next();
~~~

上述方法中，生成器内的返回的迭代器对象按照顺序执行，且每一个延时器的间隔为当前延时器的延时时间

依次接受数据

~~~js
function getUser(){
    setTimeout(()=>{
        let data='用户数据'
        //调用next方法，并将数据传入
        iter.next(data)
    },1000)
}
function getOrder(){
    setTimeout(()=>{
        let data='订单数据'
        iter.next(data)
    },1000)
}
function getGoods(){
    setTimeout(()=>{
        let data='商品数据'
        iter.next(data)
    },1000)
}

function *gen(){
    let user=yield getUser()
    console.log(user)
    let order=yield getOrder()
    console.log(order)
    let goods=yield getGoods()
    console.log(goods)
}
let iter=gen();
iter.next()
~~~

## 十三、Promise

Promise是ES6中引入的异步编程的新解决方案（之前可以用生成器来解决），语法上Promise是一个构造函数，用来封装异步操作并可以获取其成功或失败的结果

可以将异步操作队列化，按照期望的顺序执行，返回符合预期的结果
可以在对象之间传递和操作promise，帮助我们处理队列

resolve作用是，将Promise对象的状态从“未完成”变为“成功”（即从 pending 变为 resolved），在异步操作成功时调用，并将异步操作的结果，作为参数传递出去；
 reject作用是，将Promise对象的状态从“未完成”变为“失败”（即从 pending 变为 rejected），在异步操作失败时调用，并将异步操作报出的错误，作为参数传递出去。

promise有三个状态：
 （1）pending[待定]初始状态
 （2）fulfilled[实现]操作成功
 （3）rejected[被否决]操作失败
 当promise状态发生改变，就会触发then()里的响应函数处理后续步骤；
 promise状态一经改变，不会再变。

Promise对象的状态改变，只有两种可能：
 从pending变为fulfilled
 从pending变为rejected。
 这两种情况只要发生，状态就凝固了，不会再变了。

### 1.基本使用

成功：

~~~js
const p=new Promise(function(resolve,reject){
    setTimeout(function(){
        let data='数据库中的用户数据'
        //对象状态为成功
        resolve(data)
    },1000)
});
//两个回调，第一个是成功，第二个是失败
p.then(function(value){
    //成功打印值
    console.log(value);
},function(reason){

})
~~~

失败：

~~~js
const p=new Promise(function(resolve,reject){
    setTimeout(function(){
        // let data='数据库中的用户数据'
        // //对象状态为成功
        // resolve(data)
        let error='数据读取失败'
        reject(error);
    },1000)
});
//两个回调，第一个是成功，第二个是失败
p.then(function(value){
    //成功打印值
    console.log(value);
},function(reason){
    //失败打印，打印报错语句
    console.error(reason)
})
~~~

### 2.文件读取

（1）调用方法读取文件，本身就是异步操作

缺点：会产生缩进，影响可读性

~~~js
const fs=require('fs')

fs.readFile('../resources/资料.md',(err,data)=>{
    //如果失败则抛出异常
    if(err){
        throw err;
    }
    //如果没有错，则打印
    console.log(data.toString())
})
~~~

（2）使用Promise封装异步操作

~~~js
const fs=require('fs')

const p=new Promise(function(resolve,reject){
    fs.readFile('../resources/资料.md',(err,data)=>{
        if(err){
            reject(err);
        }
        //如果没有错，则打印
        resolve(data);
    })
})

p.then(function(value){
    console.log(value.toString())
},function(reason){
    console.error('读取失败!')
})
~~~

### 3.封装ajax操作

~~~js
const p=new Promise((resolve,reject)=>{
    const xhr=new XMLHttpRequest();
    xhr.open('GET','https://api.apiopen.top/getJoke')
    xhr.send()
    xhr.onreadystatechange=function(){
        if(xhr.readyState===4){
            if(xhr.status>=200&&xhr.status<300){
                //成功时的操作
                resolve(xhr.response)
            }
            else{
                //失败时的操作
                reject(xhr.status);
            }
        }
    }
})   
//指定成功和失败时的回调
p.then(function(value){
    //成功时打印响应结果
    console.log(value)
},function(reason){
    console.error(reason)
})
~~~

### 4.读取多个文件

（1）调用本身方法，但是会造成缩进问题，影响可读性（且调用是嵌套的，层层递进的）

~~~js
const fs=require('fs')
//调用本身的方法
fs.readFile('../resources/资料.md',(err,data1)=>{
    fs.readFile('../resources/资料2.md',(err,data2)=>{
        fs.readFile('../resources/资料3.md',(err,data3)=>{
            let result=data1+'\r\n'+data2+'\r\n'+data3
            console.log(result)
        })
    })
})
~~~

（2）Promise读取多个文件

~~~js
const fs=require('fs')

const p=new Promise((resolve,reject)=>{
    fs.readFile('../resources/资料.md',(err,data)=>{
        //处理数据，并将处理好的数据作为参数传递给后面
        resolve(data)
    })
})

p.then(value=>{
    return new Promise((resolve,reject)=>{
        fs.readFile('../resources/资料2.md',(err,data)=>{
            //先将value和data放在一个数组内
            resolve([value,data]);
        })
    })
}).then(value=>{
    return new Promise((resolve,reject)=>{
        fs.readFile('../resources/资料3.md',(err,data)=>{
            //push方法只能由数组调用

            //此处也可以使用上面的then里的方法
            //resolve([value,data]);
            value.push(data)
            resolve(value)
        })
    })
}).then(value=>{
    //拼接成功后的数据转为字符串，并打印出来
    console.log(value.toString())
})
~~~

### 5.then方法

then方法的返回结果是Promise对象，对象状态有回调函数的执行结果决定（reject还是resolve）

（1）如果回调函数返回的结果是非promise类型的属性，状态为成功，返回值为对象的成功的值

（2）如果回调函数返回的结果是promise类型的值，则状态由返回的 promise对象中的resolve还是reject决定

（3）如果抛出错误，则then方法返回的对象中的状态为reject，且值为抛出的值

<hr/>

then方法可以链式调用

### 6.catch方法

返回失败的结果，可以直接写失败的操作，不需要要成功的操作

~~~js
p.catch(function(reason){
	console.warn(reason)
})
~~~

## 十四、集合Set

集合中的值为自动去重

### 1.Set的基本使用

~~~js

let s2=new Set(['西施','王昭君','貂蝉','杨玉环','西施']);

console.log(s2)//Set(4) {"西施", "王昭君", "貂蝉", "杨玉环"}
//元素个数
console.log(s2.size)//4
//添加元素
s2.add('赵飞燕')
console.log(s2)//Set(5) {"西施", "王昭君", "貂蝉", "杨玉环", "赵飞燕"}
//删除元素
s2.delete('赵飞燕')
console.log(s2)//Set(5) {"西施", "王昭君", "貂蝉", "杨玉环"}
//检测是否含有指定元素
console.log(s2.has('赵飞燕'))//false
//清空集合
s2.clear()
console.log(s2)//Set(0) {}
//集合实现了iterator接口，可以使用let..of..来遍历
for(let v of s2){
    console.log(v)//西施	王昭君	貂蝉	杨玉环
}
~~~

### 2.Set的实践

~~~js
//1.数组去重
let arr=[1,2,3,4,4,5,2,1,9]
//将数组转为集合来自动去重
let res=new Set(arr);
//再用扩展运算符
let resnew=[...res]
console.log(resnew);//(6) [1, 2, 3, 4, 5, 9]

//2.交集
let arr2=[4,5,6,7,6,4]
//过滤符合条件的元素，将返回值为true的值保存下来
let result=[...new Set(arr)].filter(item=>{
    let res2=new Set(arr2)
    return res2.has(item)
})
console.log(result)//(2) [4, 5]

//3.并集:将自动去重后的集合先合并，再转为数组
let union=[...new Set([...arr,...arr2])]
console.log(union)//(8) [1, 2, 3, 4, 5, 9, 6, 7]

//4.差集:当前集合中有，但是另一个集合没有的（主体不一样则结果不一样）
let diff=[...new Set(arr)].filter(item=>{
    let res2=new Set(arr2)
    return !res2.has(item)
})
console.log(diff)//(4) [1, 2, 3, 9]
~~~

## 十五、Map

ES6提供了Map数据结构。它类似于对象（可以用new来创建），也是键值对的集合。但是键的范围不仅限于字符串，各种类型的值（包括对象）都可以当作键。Map也实现了iterator接口，所以可以使用扩展运算符和for...of...进行遍历。Map的属性和方法有：

1.set	返回Map的元素个数

2.delete	根据键名删除对应键值

3.get	获取键名对应的键值

4.has	检测Map是否含有某个元素

5.size	返回Map的元素个数

6.clear	清空集合，返回undefined

~~~js
let m=new Map();
m.set('name','qy')
m.set('change',function(){
    console.log('改变')
})
let key={
    school:'qygg'

}
m.set(key,['北京','上海'])
m.delete('name')
console.log(m)

for(let v of m){
    console.log(v)//返回的是数组，数组中元素为键名和键值
}
~~~

## 十六、class类

ES6提供了更接近传统语言的写法，引入了Class类，作为对象的模板。通过class可以定义类。基本上，ES6的class可以看作是一个语法糖，它的绝大多数功能，ES5都可以做到，新的class写法只是让对象原型的写法更清晰、更像面向对象编程的语法而已

### 1.声明

ES6中的写法（在类中constructor外写的方法相当于ES5中在原型中声明方法）

且constructor中的参数就是构造函数实例化时的参数

~~~~js
class Phone{
    //固定写法，名字不能修改
    constructor(brand,price){  
        this.brand=brand;
        this.price=price;
    }
    call(){
        console.log('可以打电话')
    }
}
let iqoo=new Phone('iqoo',3000)
iqoo.call()//可以打电话
console.log(Phone.constructor)//Phone {brand: "iqoo", price: 3000}
~~~~

等同于ES5中的以下写法

~~~js
function Phone(brand,price){
	this.brand=brand;
	this.price=price;
}
Phone.prototype.call=function(){
	console.log('可以打电话')
}
let iqoo=new Phone('iqoo',3000)
iqoo.call()
console.log(iqoo)
~~~

### 2.静态成员

用static关键字修饰的属性称为静态成员

静态成员只能由定义的本身所调用

而不能由其实例对象调用

~~~js
class Phone{
    static name='iQOO'
	static changge(){
    	console.log('打电话')
	}
}
let iqoo=new Phone()

console.log(iqoo.name)//undefined
iqoo.changge()//报错

console.log(Phone.name)//iQOO
Phone.changge()//打电话
~~~

### 3.继承

ES5继承

~~~js
function Phone(brand,price){
    this.brand=brand;
    this.price=price;
}
Phone.prototype.call=function(){
    console.log('打电话')
}
function SmartPhone(brand,price,color,size){
    //改变this指向
    Phone.call(this,brand,price)
    this.size=size;
    this.color=color;
}
//设置子级构造函数的原型，来继承父级构造函数的原型
SmartPhone.prototype=new Phone();
SmartPhone.prototype.constructor=SmartPhone;

SmartPhone.prototype.photo=function(){
    console.log('我可以拍照')
}
let sphone=new SmartPhone('iQOO',3000,'blue','14yincun');
sphone.call();//打电话
console.log(sphone.brand);//iQOO

sphone.photo()//我可以拍照
~~~

ES6继承

~~~js
class Phone{
    constructor(brand,price){
        this.price=price;
        this.brand=brand;
    }
    call(){
        console.log('我可以打电话')
    }
}
//继承了父类的方法
class SmartPhone extends Phone{
    constructor(brand,price,color,size){
        //等同于Phone.call(this,brand,price)
        super(brand,price);
        this.color=color;
        this.size=size
    }
    photo(){
        console.log('拍照片')
    }
}
let sphone=new SmartPhone('iQOO',3000,'blue','14yincun')
sphone.photo()
sphone.call()
~~~

### 4.重写

在子类中重新定义父类的同名方法，称为	重写

~~~js
class Phone{
    constructor(brand,price){
        this.price=price;
        this.brand=brand;
    }
    call(){
        console.log('我可以打电话')
    }
}
//继承了父类的方法
class SmartPhone extends Phone{
    constructor(brand,price,color,size){
        //等同于Phone.call(this,brand,price)
        super(brand,price);
        this.color=color;
        this.size=size
    }
    photo(){
        console.log('拍照片')
    }
    //在子类中重新定义父类的同名方法
    call(){
        //若想调用父类的同名方法，可以用super.call()调用
        super.call();
        console.log('视频通话')
    }
}
let sphone=new SmartPhone('iQOO',3000,'blue','14yincun')
sphone.photo()
sphone.call()
~~~

这是调用的子类的方法，而不是父类的方法

### 5.get和set

（1）get

get是对象的属性值返回的方法，且不能有参数

可通过调用该属性打印输出

一般对动态属性进行封装

~~~js
class Phone{
    get price(){
        console.log(`价格`)
        return 3
    }
}
let s=new Phone()
console.log(s.price)
/*打印结果：
价格
3
*/
~~~

（2）set

set是修改属性值的方法

设置属性的值，必须有参数

实例化后设置属性值，就相当于调用方法

一般是对值进行判断时使用

~~~js
class Phone{
    get price(){
        console.log(`价格`)
        return 3
    }
    set price(p){
        console.log(`价格为${p}`)
    }
}
let s=new Phone()

s.price=1200//价格为1200
~~~

## 十七、数值扩展

### 1.Number.EPSILON

是js表示的最小精度

该属性的值接近于2.220446049250313*e^(-16)

在js中，大部分浮点数都有误差。

通常这样判断

~~~js
function equal(a,b){
    return Math.abs(a-b)<Number.EPSILON
}
console.log(0.1+0.2==0.3)//false
console.log(equal(0.1+0.2,0.3))//true
~~~

然而不是所有浮点数都有舍入误差。**二进制能精确地表示位数有限且分母是2的倍数的小数**，比如0.5，0.5在计算机内部就没有舍入误差。所以0.5 + 0.5 === 1

### 2.Number.isFinite

检测一个数值是否是有限数

### 3.Number.isNaN

检测一个数值是否是NaN

### 4.Number.parseInt和Number.parseFloat

截取字符串中从头开始的整数或浮点数

~~~js
console.log(Number.parseFloat('12.33a3da'))//12.33
console.log(Number.parseFloat('1123a3da'))//1123
~~~

### 5.Number.isInteger

判断一个数是否是整数

### 6.Math.trunc

将数字的小数部分去掉

### 7.Math.sign

判断一个数是	正数、0、还是负数

正数：返回1

0：返回0

负数：返回-1

## 十八、对象方法的扩展

### 1.Object.is

判断两个值（可以是任意类型的值）是否完全相等



因为在以往的判断中，我们常使用“==”或“===”来判断

当我们使用 == 作比较时，在一些情况下由于类型转换或者说“把两个操作数中的一个转换成另一个，然后在比较”，会出现意想不到的结果。

~~~js
console.log('0 == " "', 0 == ' '); // true
console.log('null == undefined', null == undefined); // true
console.log('[1] == true', [1] == true); // true
~~~

因此 JavaScript 中给我们提供了全等操作符 ===, 它比不全等操作符更加严格并且不会发生类型转换。但是用 === 来进行比较并不是最好的解决方案。你可能会得到：

~~~js
console.log('NaN === NaN', NaN === NaN); // false
//因为NaN和任意数值比较都不相等
~~~

所以在ES6中，新增方法Object.is

~~~js
console.log(Object.is(NaN,NaN))//true
~~~

### 2.Object.assign

对象合并

~~~js
console.log(Object.assign(obj1,obj2))
~~~

参数1被参数2覆盖，并产生一个新的对象，如果有相同属性名，则覆盖，如果有不同的属性名，则加入到新的合并后的对象

### 2.Object.setPrototypeOf和Object.getPrototypeOf

（1）Object.setPrototypeOf

设置原型对象

参数1和参数2都为对象

将参数2放入参数1的原型对象中

~~~js
const school={
	name:"qinghua"
}
const cities={
	city:'北京'
}
Object.setPrototypeOf(school,cities)
console.log(school)
/*
{name: "qinghua"}
	name: "qinghua"
	__proto__: Object
*/
~~~

（2）Object.getPrototypeOf

获取对象的原型对象中的属性

~~~js
console.log(Object.getPrototypeOf(school))
/*
{city: "北京"}
*/
~~~

## 十九、模块化

模块化是将一个大的程序文件，拆分为多个小的文件（互不影响），然后将多个小文件组合起来

优势：

（1）防止命名冲突

（2）代码复用

（3）高维护性

### 1.基本使用

js文件中的代码，属性前要加export	表示向外暴露该属性

~~~js
export let name="qy"

export function action(){
    console.log('说出名字')
}
~~~

HTML部分引入模块

此处type类型要改为module

~~~js
<script type="module">
    //m1为自定义的变量名
    //引入指定文件模块内容
    import *as m1 from "../js/31m1.js"

	console.log(m1)
</script>
~~~

### 2.暴露数据的语法

（1）每一个属性加export（只暴露很少的变量或函数）

~~~js
export let name='qy'
~~~

（2）统一暴露（暴露大量的变量或函数）

~~~js
let name="qy"

function action(){
    console.log('说出名字')
}
export {name,action}
~~~

（3）默认暴露（暴露大量的变量或函数）

js部分

~~~js
export default {
    name:"qy",
    
    action:function(){
        console.log('说出名字')
    }

}
~~~

HTML部分调用属性

~~~js
m2.default.action();

console.log(m2.default.name)
~~~

### 3.引入模块数据的语法

（1）通用的导入模块方法

~~~js
//m1为自定义的变量名
import *as m1 from "../js/31m1.js"
~~~

（2）解构赋值的形式

~~~js
import {name,action} from "../js/31m1.js"

console.log(name)//qy
action()//说出名字
~~~

以该方法导入多个文件时，对象中的属性名不能相同

若相同可以改名

~~~js
import {name as username,action} from "../js/31m2.js"
~~~

此处表示在下面语句中，可以用变量username来代替name

（3）对应默认暴露数据的引入方式

~~~js
import {default as m} from "../js/31m3.js"
~~~

此处的default必须改别名，否则报错

此外还有一种方式，但该方式只能针对默认暴露

~~~js
import m from "../js/31m3.js"
~~~

### 4.模块化引入模块规范

通常将多个引入模块的语句写在一个js文件中，该文件只有引入模块语句，相当于一个入口

则此时，HTML文件中的写法

~~~js
<script src="../src/js"	type="module">
~~~

### 5.ES6模块化代码在项目的使用

主要使用了babel工具，将ES6语法编译为个别浏览器能识别的ES5语法

（1）先安装babel-cli、babel-preset-env、browserify工具

（2）通过命令npx babel js -d dist/js --presets=babel-preset-env来编译

（3）打包命令npx  browserify dist/js/app.js -o dist/bundle.js

### 6.在ES6中引入npm包

以导入jQuery包为例

~~~js
import $ from 'jquery';//等于 const $=require('jquery')
//导入包后执行命令
$('body').css('background','yellow')
~~~

## 二十、ES7新特性

### 1.includes

判断数组中是否含有指定元素

~~~js
const shu=['a','b','c']

console.log(shu.includes('a'))//true
~~~

然而在该特性之前，用indexof来判断

indexof方法，返回指定元素下标，如果没有则返回-1

### 2.幂运算**

~~~js
console.log(2**10)//1024
~~~

而在这之前我们用Math.pow来作幂运算操作

## 二十一、ES8新特性

### 1.async函数

1）基本使用

会返回一个Promise对象

（1）只要返回值不是一个Promise对象，那么最后打印出来的Promise对象的状态都是成功的（resolved），且PromiseValue是返回的值

（2）返回的是一个Promise对象，那么打印出来的promise对象状态由返回的Promise对象的状态决定（与其状态一致），且对象值也就是返回的resolve/reject内的参数值

（3）抛出错误，返回的结果也是一个失败的Promise

<hr/>

2）await

（1）await必须写在async函数中

（2）await后面的表达式一般为promise对象

（3）await返回的是promise成功的值

（4）await的promise失败了，就会抛出异常，需要通过try...catch捕获处理

~~~js
const p=new Promise((resolve,reject)=>{
    resolve('成功的值')
})
async function m(){
    let result=await p;
    console.log(result)
}
m()//成功的值
~~~

如果promise对象状态为失败，则可以用try...catch来捕获

try捕获成功的数据，catch得到失败的数据

~~~js
const p=new Promise((resolve,reject)=>{
    reject('失败的值')
})
async function m(){
    try{
        let result=await p;
        console.log(result)
    }
    catch(e){
        console.log(e)
    }

}
m()//失败的值
~~~

3）async和await结合使用读取文件

~~~js
const fs=require('fs')

function readWei(){
    return new Promise((resolve,reject)=>{
        fs.readFile('../resources/资料.md',(err,data)=>{
            if(err)reject(err)

            resolve(data)
        })
    })
}
function readmd(){
    return new Promise((resolve,reject)=>{
        fs.readFile('../resources/资料2.md',(err,data)=>{
            if(err)reject(err)

            resolve(data)
        })
    })
}

async function m(){
    let weixue=await readWei()
    let md=await readmd()

    console.log(weixue.toString())
    console.log(md.toString())

}
m();
~~~

4）async和await结合使用发送AJAX请求

~~~js
function sendAjax(url){

    return new Promise((resolve,reject)=>{
        const x=new XMLHttpRequest();

        x.open('GET',url)

        x.send();
        x.onreadystatechange=function(){
            if(x.readyState==4){
                if(x.status>=200&&x.status<300){
                    //成功时接收响应数据
                    resolve(x.response)
                }else{
                    reject(x.status)
                }
            }
        }
    })

}
//Promise内置的then方法来获取响应数据
sendAjax('https://api.apiopen.top/getJoke').then(value=>{
    console.log(value)
},reason=>{

})
//用async函数来获取
async function m2(){
    const re=await  sendAjax('https://api.apiopen.top/getJoke')
    console.log(re)
}
m2()
~~~

### 2.对象方法扩展

（1）Object.keys/values/entries

~~~js
const school={
    name:'qy',
    city:['北京','南京']
}
//获取对象的键名（即属性名），并返回一个数组
console.log(Object.keys(school))//["name", "city"]
//获取对象的键值（即属性值），并返回一个数组
console.log(Object.values(school))//["qy", Array(2)]
//获取对象的每一组 键名以及对应的键值，并返回一个二维数组
console.log(Object.entries(school))
/*
(2) [Array(2), Array(2)]
    0: Array(2)
    0: "name"
    1: "qy"
    length: 2
    
    1: Array(2)
    0: "city"
    1: (2) ["北京", "南京"]
    length: 2
*/
~~~

可以用来创建一个Map对象

~~~js
const m=new Map(Object.entries(school))
console.log(m)//Map(2) {"name" => "qy", "city" => Array(2)}
~~~

（2）Object.getOwnPropertyDescriptors

~~~js
//对象属性的描述，返回的是一个对象
console.log(Object.getOwnPropertyDescriptors(school))
~~~

（3）Object.create

该方法可以创建对象，还可以创建没有原型的对象

~~~js
const obj=Object.create(null,{
        name:{
        value:'qy',
        writable:true,
        configurable:true,
        enumerable:true
    }
})
console.log(obj)
/*
{name: "qy"}
  name: "qy"
*/
~~~

## 二十二、ES9新特性

### 1.对象中的扩展运算符和rest参数

rest参数与扩展运算符在ES6中已经引入，不过ES6中只针对数组

在ES9中为对象提供了像数组一样的rest参数和扩展运算符

~~~js
function connect({host,port,...user}){
    console.log(host)
    console.log(port)
    console.log(user)
}
connect({
    host:'1267.0.0.1',
    port:3306,
    username:'root',
    password:123,
    type:'mm'
})
/*
1267.0.0.1
3306
{username: "root", password: 123, type: "mm"}
*/
~~~

...user为传入实参的其他部分，返回时是一个对象，多的实参在该对象中

<hr/>

扩展运算符在对象中的使用

将多个对象用“...”拆分为一组一组的键值对，再放在一个对象中

~~~js
const q={
    name:'qy',
    getname:function(){
        console.log(`你的名字是${this.name}`)
    }
}
const w={
    name2:'lq',
    getname2:function(){
        console.log(`你的名字是${this.name}`)
    }
}

console.log({...q,...w})//{name: "qy", name2: "lq", getname: ƒ, getname2: ƒ}
~~~

### 2.正则扩展

（？=字符串）：表示要匹配的字符串后面是指定字符串

~~~js
const reg=/\d+(?=啦)/
~~~

该语句表示  匹配1个或多个数字，且数字后面有字符串“啦”

<hr/>

后边多一个？表示懒惰模式（非贪婪模式）。

在表示重复字符元字符，后面加多一个”?”字符即可

必须跟在*或者+后边用
如：

~~~html
<img src="test.jpg" width="60px" height="80px"/>
~~~

如果用正则匹配src中内容非懒惰模式匹配
src=".*"
匹配结果是：src="test.jpg" width="60px" height="80px"
意思是从="往后匹配，直到最后一个"匹配结束

懒惰模式（非贪婪模式）正则：
src=".*?"
结果：src="test.jpg"
因为匹配到第一个"就结束了一次匹配。不会继续向后匹配。因为他懒惰嘛。

.表示除\n之外的任意字符
*表示匹配0-无穷

<hr/>

(.*?)表示要添加在返回的正则匹配结果数组中

<hr/>

（1）命名捕获内容

~~~js
let str = '<a href="http://www.baidu.com">百度</a>'

const reg = /<a href="(.*)">(.*)<\/a>/;

const re = reg.exec(str)

console.log(re)
~~~

exec方法返回的是一个数组，数组内容为匹配的标签文本、（.*）的内容

~~~js
let str = '<a href="http://www.baidu.com">百度</a>'

const reg = /<a href="(?<url>.*)">(?<text>.*)<\/a>/;

const re = reg.exec(str)

console.log(re.groups)//{url: "http://www.baidu.com", text: "百度"}
~~~

然而更推荐的是用命名捕获内容，这样更灵活更便于维护

（2）反向断言

正向断言：

~~~js
let str='jdasd5646你知道12345啦啦啦'

const reg=/\d+(?=啦)/
const res=reg.exec(str)
console.log(res)
~~~

反向断言：

~~~js
let str='jdasd5646你知道么12345啦啦啦'

const reg=/(?<=么)\d+/
const res=reg.exec(str)
console.log(res)
~~~

该正则语句表示：要匹配的	一串数字前是字符串“么”，\d表示要匹配的是数字，+表示一个或多个数字

（3）dotAll模式

~~~js
let str = `
    <ul>
        <li>
            <a>肖申克的救赎</a>
            <p>上映时间:1994-09-01</p>
        </li>
        <li>
            <a>阿甘正传</a>
            <p>上映时间:1994-07-01</p>
        </li>
    </ul>`;

const reg=/<li>.*?<a>(.*?)<\/a>.*?<p>(.*?)<\/p>/gs
// const result = reg.exec(str);
let result;
let data=[];
while(result=reg.exec(str)){

    data.push({title:result[1],time:result[2]})
}
console.log(data)
~~~

## 二十三、ES10新特性

### 1.Object.fromEntries

创建一个对象，但是参数是一个二维数组

也就是说，该方法可以将二维数组转为对象

~~~js
const res=Object.fromEntries([
    ['name','qy'],
    ['city','北京，南京']
])
console.log(res)//{name: "qy", city: "北京，南京"}
~~~

参数也可以是Map对象

~~~js
const m=new Map();
m.set('name','qy')
const result=Object.fromEntries(m)
console.log(result)
~~~

### 2.字符串方法扩展

（1）trimStart

清除字符串左侧空白

~~~js
let str='	i love you	'

console.log(str)//	i love you	
console.log(str.trimStart())//i love you
~~~

（2）trimEnd

清除字符串右侧空白

~~~js
let str='	i love you	'

console.log(str)//	i love you	
console.log(str.trimEnd())//	i love you
~~~

### 3.数组方法扩展

（1）flat

将多维数组转为低维数组，可以从多维转为指定低维度数

参数为深度（当前维度数-要转为的数组的维度数），是一个数字

~~~js
const arr=[1, 2, 343, 4, 566, [5,0,1]]
console.log(arr.flat())//(8) [1, 2, 343, 4, 566, 5, 0, 1]
~~~

（2）flatMap

相当于flat和map方法的结合，在对数组遍历对每个作处理时，并将每个元素降维度数处理

~~~js
const arr=[1,2,3,4]
const res=arr.flatMap(item=>[item*10])
console.log(res)//(4) [10, 20, 30, 40]
~~~

### 4.Symbol.description

获取Symbol类型的字符串描述

~~~js
let s=Symbol('qy')

console.log(s)//Symbol(qy)
console.log(s.description)//qy
~~~

## 二十四、ES11新特性

### 1.私有属性

js中使用"#"声明私有属性

~~~js
class Person{
    name;
    #age;
    #weight;
    constructor(name,age,weight){
        this.name=name;
        this.#age=age;
        this.#weight=weight
    }
    sayinfo(){
        console.log(this.name)
        console.log(this.#age)
        console.log(this.#weight)
    }
}
const girl=new Person('西施',18,'46kg')
console.log(girl.name)
console.log(girl.#age)//报错
console.log(girl.#weight)//报错
girl.sayinfo();
~~~

直接在类外部调用私有属性，是不可以的

只可以通过类内部的方法来打印私有属性

### 2.Promise.allSettled

将多个Promise对象的状态和值封装在一个数组内，并将该数组放在一个新的Promise对象的值内（且这个新的Promise对象始终是成功的）

该方法可以用在无论成功还是失败都继续执行的操作

~~~js
const p1=new Promise((resolve,reject)=>{
    setTimeout(()=>{
        resolve('商品数据1')
    },2000)
})

const p2=new Promise((resolve,reject)=>{
    setTimeout(()=>{
        resolve('商品数据2')
    },2000)
})
const res=Promise.allSettled([p1,p2])
console.log(res)
/*
Promise {<pending>}
__proto__: Promise
[[PromiseState]]: "fulfilled"
[[PromiseResult]]: Array(2)
   0: {status: "fulfilled", value: "商品数据1"}
   1: {status: "fulfilled", value: "商品数据2"}
   length: 2
   __proto__: Array(0)
*/
~~~

此外还有一个all方法，与allSettled很像，但是该方法只有在多个Promise对象都成功才会成功，只要有一个失败就会失败

### 3.String.matchAll

批量提取数据中的所需信息

~~~js
let str = `
    <ul>
        <li>
            <a>肖申克的救赎</a>
            <p>上映时间:1994-09-01</p>
        </li>
        <li>
            <a>阿甘正传</a>
            <p>上映时间:1994-07-01</p>
        </li>
    </ul>`;

const reg=/<li>.*?<a>(.*?)<\/a>.*?<p>(.*?)<\/p>/sg
const res=str.matchAll(reg)
console.log([...res])//(2) [Array(3), Array(3)]
~~~

### 4.可选链操作符

？.表示	先判断前面是否有，有就判断其内容中是否有指定属性

即使没有传实参，也不会报错，只会返回undefined

~~~js
function m(config){
    const dbHost=config?.db?.host;
    console.log(dbHost) //127.0.0.1
}
m({
    db:{
        host:'127.0.0.1',
        username:'root'
    },
    cache:{
        host:'192.168.1.200',
        username:'admin'
    }
})
~~~

注：？.表示进入对象中查找，直接写属性，不需要通过对象来调用属性

### 5.动态import

用到的时候加载，没用到不加载

import('url')返回的是一个Promise对象，而它要处理的Promise成功的值就是import的URL中的要暴露的对象

~~~html
//html文件body中的代码
<button id='btn'>点我</button>
<script src="../js/app-66.js" type='module'></script>
~~~

~~~js
//要暴露的模块
export function hello(){
    alert('hello')
}
~~~

~~~js
//入口文件
const btn=document.getElementById('btn')
btn.onclick=function(){
    import('./hello-66.js').then(module=>{
        // console.log(module)
        //调用对象中的方法
        module.hello();
    })
}
~~~

### 6.新的数据类型BigInt

主要用来作大的整型数值的运算

且参数只能为整型运

BigInt型也只能和BigInt型作运算

~~~js
let n=123
console.log(BigInt(n))
~~~

### 7.globalThis

新引入的一个指向全局的全局变量

无论什么环境，都始终指向全局变量

在不同环境中，如果想对全局变量操作，只要对该吧变量操作就可以了







## 学习过程中忘记的知识点

### 1.for循环绑定单击响应函数的相关问题的解决

错误示例：

~~~js
var li=document.getElementsByTagName("li");
		
for (var i = 0; i < li.length; i++) {
//for循环会在页面加载后就立即执行，且给每一个li都加了监听事件。
    li[i].onclick=function(){

        li[i].style.background='yellow';
    }
}
~~~

注意：该错误出问题的是i，不是加监听出的错。

for循环会在页面加载后就立即执行，且给每一个li都加了监听事件。

此时，已经每一个li都已经加好了监听事件

然而在点击事件触发时，此时i已经不再是点击的那个li的索引，而是for循环遍历后的i的索引

所以要对事件中的i进行处理

以下是各种解决方法：

第一种：

~~~js
var li=document.getElementsByTagName("li");
		
for (var i = 0; i < li.length; i++) {

    li[i].index=i;//给每个标签的index属性赋值

    li[i].onclick=function(){

        li[i].style.background='yellow';
    }
}
~~~

第二种：

使用let声明变量，使变量只在块级作用域内有效

~~~js
var li=document.getElementsByTagName("li");
		
for (let i = 0; i < li.length; i++) {

    li[i].onclick=function(){

        li[i].style.background='yellow';
    }
}
~~~

则此时的代码相当于

~~~js
{
	let i=0;
    li[i].onclick=function(){

        li[i].style.background='yellow';
    }
}
~~~

第三种:

通过自执行匿名函数来循环绑定监听事件

### 2.异步

事件会放在事件队列中，

同步代码执行完毕才会执行异步代码

### 3.实现异步编程的几种方法

此处是将异步变为同步

~~~js

let girlName = "裘千尺"

function hr(callBack) {
    setTimeout(() => {
        girlName = "黄蓉"
        console.log('我是黄蓉');
        callBack()
    }, 0);
}

function gj() {
    console.log(`${girlName}你好，我是郭靖，认识一下吧`);
}
hr(gj)
//我是黄蓉
//黄蓉你好，我是郭靖，认识一下吧
~~~

1. 回调函数
2. 事件监听
3. 发布订阅模式
4. Promise
5. Generator (ES6)
6. async (ES7)