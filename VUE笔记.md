- [一、介绍](#一介绍)
  - [1.主要信息](#1主要信息)
  - [2.主要特点](#2主要特点)
  - [3.常用扩展插件](#3常用扩展插件)
- [二、最基本的使用](#二最基本的使用)
- [三、v-for](#三v-for)
  - [1. v-for介绍](#1-v-for介绍)
  - [2. v-for例子](#2-v-for例子)
  - [3. v-for的key属性](#3-v-for的key属性)
- [四、v-on监听事件](#四v-on监听事件)
  - [1.参数的注意事项](#1参数的注意事项)
  - [2.实际例子](#2实际例子)
  - [3.常用修饰符](#3常用修饰符)
- [五、MVVM](#五mvvm)
- [六、Vue的生命周期](#六vue的生命周期)
- [七、mustache语法](#七mustache语法)
- [八、其他的一些指令](#八其他的一些指令)
  - [1. v-once](#1-v-once)
  - [2. v-html](#2-v-html)
  - [3. v-pre](#3-v-pre)
  - [4. v-cloak](#4-v-cloak)
  - [5. v-bind](#5-v-bind)
  - [6. v-if、v-else、v-else-if](#6-v-ifv-elsev-else-if)
  - [7. v-if实例](#7-v-if实例)
  - [8. v-show](#8-v-show)
- [九、计算属性](#九计算属性)
  - [1.基本使用](#1基本使用)
  - [2. computed内置的setter和getter](#2-computed内置的setter和getter)
  - [3.计算属性和methods的区别](#3计算属性和methods的区别)
- [十、常见的数组的响应式内置方法](#十常见的数组的响应式内置方法)
  - [1. push](#1-push)
  - [2. pop](#2-pop)
  - [3. shift](#3-shift)
  - [4. unshift](#4-unshift)
  - [5. splice](#5-splice)
  - [6. sort](#6-sort)
  - [7. reserve](#7-reserve)
- [十一、v-model](#十一v-model)
  - [1.简单使用](#1简单使用)
  - [2.结合radio使用](#2结合radio使用)
  - [3.结合checkbox使用](#3结合checkbox使用)
  - [4.结合select使用](#4结合select使用)
  - [5. input的值绑定](#5-input的值绑定)
  - [6.常用修饰符](#6常用修饰符)
- [十二、组件](#十二组件)
  - [1.使用步骤](#1使用步骤)
  - [2.基本使用](#2基本使用)
  - [3.全局组件和局部组件](#3全局组件和局部组件)
  - [4.父组件和子组件](#4父组件和子组件)
  - [5.组件模板分离](#5组件模板分离)
  - [6.组件中的data](#6组件中的data)
  - [7.父子组件通信](#7父子组件通信)
  - [8.父子通信结合双向绑定](#8父子通信结合双向绑定)
  - [9. watch侦听器](#9-watch侦听器)
  - [10.父组件直接访问子组件](#10父组件直接访问子组件)
  - [11.子组件直接访问父组件](#11子组件直接访问父组件)
  - [12.插槽slot](#12插槽slot)
  - [13.作用域插槽](#13作用域插槽)
- [十三、webpack](#十三webpack)
  - [1.基本使用](#1基本使用-1)
  - [2.使用优化](#2使用优化)
  - [3. loader](#3-loader)
  - [4.使用vue的配置](#4使用vue的配置)
  - [5. plugin](#5-plugin)
  - [6.配置文件分离](#6配置文件分离)
- [十四、vue组件化开发](#十四vue组件化开发)
- [十五、vue CLI脚手架](#十五vue-cli脚手架)
  - [1.安装脚手架](#1安装脚手架)
  - [2. runtime-only和runtime-compiler的区别](#2-runtime-only和runtime-compiler的区别)
  - [3.自定义配置文件](#3自定义配置文件)
- [十六、路由vue-router](#十六路由vue-router)
  - [1.基础概念](#1基础概念)
  - [2. url的hash和h5的history](#2-url的hash和h5的history)
  - [3.安装](#3安装)
  - [4.使用步骤](#4使用步骤)
  - [5.简单使用例子](#5简单使用例子)
  - [6. router-link的其他属性](#6-router-link的其他属性)
  - [7.通过代码实现路由跳转](#7通过代码实现路由跳转)
  - [8.动态路由的使用](#8动态路由的使用)
  - [9.懒加载](#9懒加载)
  - [10.嵌套路由](#10嵌套路由)
  - [11.传递参数的方式](#11传递参数的方式)
  - [12.$router和$route的区别](#12router和route的区别)
  - [13.路由导航守卫](#13路由导航守卫)
  - [14. keep-alive](#14-keep-alive)
- [十七.前后端分离](#十七前后端分离)
- [十八、Vuex](#十八vuex)
  - [1.状态管理](#1状态管理)
  - [2.安装vuex插件](#2安装vuex插件)
  - [3.简单使用](#3简单使用)
  - [4. state单一状态树](#4-state单一状态树)
  - [5. vuex的getters属性](#5-vuex的getters属性)
  - [6. mutation状态更新](#6-mutation状态更新)
  - [7. vuex的响应式方法](#7-vuex的响应式方法)
  - [8. mutation常量类型](#8-mutation常量类型)
  - [9. action异步操作](#9-action异步操作)
  - [10. modules](#10-modules)
  - [11.目录组织结构](#11目录组织结构)

## 一、介绍

### 1.主要信息

Vue (读音 /vjuː/，类似于 **view**) 是一套用于构建用户界面的**渐进式框架**，作者为尤雨溪。与其它大型框架不同的是，Vue 被设计为可以自底向上逐层应用。Vue 的核心库只关注视图层，不仅易于上手，还便于与第三方库或既有项目整合。

渐进式：一个项目中可以只使用框架的一部分，并不是只用了一点就必须要使用全部了

例如：原来的项目使用的是jquery，但是还是可以将vue一点一点地引入，然后使用vue。
最后全部替换成vue。

### 2.主要特点

遵循MVVM模式

解耦视图

可复用的组件

前端路由技术

状态管理

虚拟DOM

### 3.常用扩展插件

（1）Vue-cil : Vue脚手架

（2）Vue-resource（axios）: ajax请求

（3）Vue-router : 路由

（4）vuex : 状态管理

（5）Vue-lazyload : 图片懒加载

（6）Vue-scroller : 页面滑动相关

（7）mint-ui : 基于Vue的UI组件库（移动端）

（8）element-ui : 基于Vue的UI组件库（PC端）

## 二、最基本的使用

HTML部分

~~~html
<div id="app">
    <h2>{{message}}</h2>
    <h3>{{name}}</h3>
</div>
~~~

js部分

~~~js
const app=new Vue({
    el:"#app",//用于挂载要管理的元素，此处可以用document.querySelector()表示选择器
    data:{//定义数据
        message:"vue你好!",
        name:"hello"
    }
})
console.log(app.message)//vue你好!
console.log(app.name)//hello
~~~

## 三、v-for

### 1. v-for介绍

vue里封装了v-for指令，可以用来循环操作

v-for指令需要使用 item in items形式的特殊语法，其中 items可以是数组是也可以对象，而 item 则是被迭代的数组元素。

items为数组：

​	格式为（value ，index）in items	（若括号内只有一个参数，则默认为元素）

items为对象：

​	格式为（value，key，index）in items	（若括号内只有一个参数，则默认为属性值）

### 2. v-for例子

HTML部分

~~~html
<div id="app">
    <ul>
        <li v-for="(item, index) in movies" :key="index">第{{index}}个是{{item}}</li>
    </ul>
</div>
~~~

js部分

~~~js
const app=new Vue({
    el:"#app",//用于挂载要管理的元素
    data:{//定义数据
        message:"vue你好!",
        movies:['复仇者联盟','雷神','蝙蝠侠','超人','钢铁侠']
    }
})
~~~

### 3. v-for的key属性

当某一层有很多相同的节点时，也就是列表节点，我们希望插入一个新的节点。

假设此处要在B和C之间插入一个F，Diff算法默认是把C更新为F，D更新为C，E更新为D，直到列表最后一个节点更新结束。这样子是非常没有效率的

我们可以使用key来给每个节点做一个唯一的标识（节点里的值不能重复），这样子diff算法就可以正确的识别此节点，并找到正确的位置插入新的节点。（不会更新对应位置的后面位置的所有节点，更有效率）

总的来说，key的作用主要是为了高效的更新虚拟DOM

注：key属性的值必须是所展示的值

## 四、v-on监听事件

可以用 v-on 指令监听 DOM 事件，并在触发时运行一些 JavaScript 代码。

语法：v-on : click=" (方法名) "

同时也可以使用缩写的形式。	语法：@click=“ (方法名) ”

### 1.参数的注意事项

（1）如果调用的方法没有参数，则可以写带括号的形式，也可以直接写方法名

~~~html
<!--下面二者相同-->
<button v-on:click="say()">Say</button>
<button v-on:click="say">Say</button>
~~~

（2）如果调用的方法有一个参数，但是在v-on指令中以括号的形式调用（不传实参），则会返回undefined；如果直接以方法名的形式调用，则会返回一个MouseEvent 对象（Vue会默认将浏览器生成的event对象当作参数传给方法）

（3）如果调用的方法有两个参数，同样的在v-on指令中直接以方法名的形式调用，则第一个形参对应的返回一个event对象，第二个返回的是undefined

html部分

~~~html
<button v-on:click="handle">点击</button>
~~~

js部分

~~~js
const app = new Vue({
    el: "#app",//用于挂载要管理的元素
    methods: {
        handle(a,e){
            console.log(a,e)
        }
    }
})
~~~

控制台输出

~~~
MouseEvent {isTrusted: true, screenX: 36, screenY: 128, clientX: 36, clientY: 26, …} undefined
~~~

（4）如果想手动获取浏览器参数的event对象，则用$event表示即可

~~~html
<button v-on:click="handle(1,$event)">点击</button>
~~~

### 2.实际例子

HTML部分

~~~html
<div id="app">
    <h2>当前计数:{{counter}}</h2>
    <button v-on:click="add">+</button>
    <button v-on:click="minus">-</button>
</div>
~~~

在HTML中也可以直接执行方法

~~~html
<button v-on:click="say('hi')">Say hi</button>
~~~

js部分

~~~js
const app=new Vue({
    el:"#app",//用于挂载要管理的元素
    data:{//定义数据
        counter:0
    },
    methods:{
        add:function(){
            this.counter++;
        },
        minus:function(){
            this.counter--;
        }
    }
})
~~~

### 3.常用修饰符

（1）@事件.stop

相当于调用了原生js的event . stopPropagation（）

阻止事件冒泡

（2）@事件.prevent

相当于调用了原生js的event . preventDefault（）

阻止默认行为

（3）@keyup . 对应按键的编码

松开对应按键时，会触发事件

（4）@事件 . once

事件第一次触发时才会执行

## 五、MVVM

![image-20210408204555211](D:\web self-learn\HTML+CSS\VUE笔记.assets\image-20210408204555211.png)

模型图

![image-20210408204635290](D:\web self-learn\HTML+CSS\VUE笔记.assets\image-20210408204635290.png)

## 六、Vue的生命周期

每个 Vue 实例在被创建时都要经过一系列的初始化过程——例如，需要设置数据监听、编译模板、将实例挂载到 DOM 并在数据变化时更新 DOM 等。同时在这个过程中也会运行一些叫做**生命周期钩子**的函数，这给了用户在不同阶段添加自己的代码的机会。

![lifecycle](D:\web self-learn\HTML+CSS\VUE笔记.assets\lifecycle.png)

## 七、mustache语法

Mustache 是一款经典的前端模板引擎，在前后端分离的技术架构下面，前端模板引擎是一种可以被考虑的技术选项。随着重型框架（AngularJS、ReactJS、Vue）的流行，前端的模板技术已经成为了某种形式上的标配。Mustache 在使用的时候，会在页面上出现 {{xxx}} 这样的形式。

在{{	}}内可以放入变量，还可以直接放入一些简单的表达式

~~~html
<div id="app">{{message}}</div>
~~~

~~~html
<div id="app">{{counter*2}}</div>
~~~

~~~html
<div id="app">{{firstName + lastName}}</div>
~~~

## 八、其他的一些指令

### 1. v-once

该指令后不需要跟任何表达式

该指令表示元素和组件只渲染一次，不会随着数据的改变而改变（修改其值时，不会改变）

### 2. v-html

双大括号会将数据解释为普通文本，而非 HTML 代码。为了输出真正的 HTML，则需要使用 v-html 指令

简单来说，就是将	字符串形式的HTML代码	转为	真正的可执行的HTML代码

HTML部分

~~~html
<div id="app">
	<h2 v-html="url"></h2>
</div>
~~~

js代码

~~~js
const app = new Vue({
    el: "#app",//用于挂载要管理的元素
    data: {//定义数据
        url:"<a href='http://www.baidu.com'>百度一下</a>"
    }
})
~~~

### 3. v-pre

vue会将{{	}}形式的mustache语法解析为data中的数据

但是有时，我们并不想解析为数据，只想表示为{{变量}}的形式，此时可以使用v-pre指令来实现

~~~html
<h2 v-pre>{{counter}}</h2>
~~~

### 4. v-cloak

这个指令保持在元素上，直到关联实例结束编译。和 CSS 规则如 [v-cloak] { display: none }一起用时，这个指令可以隐藏未编译的 Mustache 标签直到实例准备完毕。

简单来说，当网络出问题或者浏览器卡住时，Mustache 语句会被隐藏，只有当Vue解析结束后，才会显示出来。同时v-cloak属性也会在Vue解析结束后跟着消失

~~~html
<h1 id="app" v-cloak>{{hi}}</h1>
~~~

### 5. v-bind

动态地绑定一个或多个 attribute，或一个组件 prop 到表达式。

在绑定 class或style的attribute 时，支持其它类型的值，如数组或对象。

如果动态绑定的属性表达式过于复杂，属性值可以为计算属性

语法：给要动态添加属性值的属性前加上 v-bind :

缩写：将v-bind:换成 :

（1）给普通attribute属性绑定

HTML部分

~~~html
<div id="app">
    <img v-bind:src="imgSrc" alt="">
    <a v-bind:href="aHref">百度一下</a>
</div>
~~~

js部分

~~~js
const app = new Vue({
    el: "#app",//用于挂载要管理的元素
    data: {//定义数据
        aHref: "http://www.baidu.com",
        imgSrc:"../img/logo.png"
    }
})
~~~

（2）给class属性绑定

对象语法：

语法：v-bind : class="{类名1:布尔值，类名2:布尔值}"（此处的布尔值表示是否使用该类选择器的样式）

用该方法来加上类选择器样式，不会与直接用class类选择器冲突（同名类选择器会覆盖），而是加起来

在该语法中，可以用，在data中定义，且值为布尔值的变量来代替该指令中的布尔值，如下所示。

HTML部分

~~~html
<h2 :class="{red:isRed,blue:isBlue}">{{title}}</h2>
~~~

此处的对象中的key是类选择器名

js部分

~~~js
const app = new Vue({
    el: "#app",//用于挂载要管理的元素
    data: {//定义数据
        isRed:true,//在此处定义v-bind绑定的类名的布尔值
        isBlue:false
    }
})
~~~

<hr/>

此处也可以将样式对象写在函数内：

HTML部分

注意，此处是用调用方法的方式来完成，所以要执行函数（加上括号）

~~~html
<h2 :class="getClasses()">{{title}}</h2>
~~~

js部分

~~~js
const app = new Vue({
    el: "#app",//用于挂载要管理的元素
    data: {//定义数据
        isRed:true,//在此处定义v-bind绑定的类名的布尔值
        isBlue:false
    }，
    methods: {
        getClasses: function () {
            return {//注意，此处使用的data中的变量，要用this来引用
                red: this.isRed, blue: this.isBlue
        	}
    	}
    }
})
~~~

<hr/>

数组语法（该方式用的少）：

~~~html
<h2 :class="['blue']">{{title}}</h2>
~~~

此处的数组中的key要加上引号，不加则表示此处的key只是一个变量

js部分，也可以如上所示，在methods属性中加上一个返回数组的方法（数组中是类选择器）

（3）给style绑定

对象语法：

HTML部分

~~~html
<h2 v-bind:style="{color:'red'}">哈哈</h2>
~~~

此处的属性值应当为字符串形式，若不是字符串形式，则表示一个变量

然而在标签中直接写样式，太过臃肿且只能写死，不能动态改动属性值，所以一般传入一个变量来代替属性值

~~~html
<h2 v-bind:style="{color:colorRed}">哈哈</h2>
~~~

~~~js
const app = new Vue({
    el: "#app",//用于挂载要管理的元素
    data: {//定义数据
        colorRed:'red'
    }
})
~~~

同样的，也可以用在一个方法内返回样式对象的方式来实现

<hr/>

数组语法：

在data中定义样式对象，再在标签中使用时，将对象以变量名存放在数组内

### 6. v-if、v-else、v-else-if

v-if 指令用于条件性地渲染一块内容。这块内容只会在指令的表达式返回 true 值的时候被渲染。

v-if="true"会渲染出来

v-if="false"不会渲染出来

一般用变量来存放布尔值，或者用表达式来表达布尔值（表达式繁琐，则可以放在方法内）

一般与v-else或者v-else-if配合使用（v-else不需要表达式，直接写上即可），用法与if...else...或者if...else if...类似，动态的决定是否渲染

### 7. v-if实例

~~~html
 <div id="app">
     <span v-if="isUser">
         <label for="username">用户账号</label>
         <input type="text" id="username" key="aa">
     </span>
     <span v-else>
         <label for="email">用户邮箱</label>
         <input type="text" id="email" key="aaa">
     </span>
     <button @click="toggle()">切换</button>
</div>
~~~

在输入框内输入值后，点击按钮切换，则会出现值没有变化，不会自动清空

这是因为dom放在浏览器上渲染时，出于性能考虑，会将已渲染的相同标签保存，以便于下次相同标签的再次渲染 。

但是复用的时候，对于变化的地方会做出相应的变化

为了解决以上情况，则给复用的多个标签加上key属性，并设置不同的值，这样就会实现value的自动清空

### 8. v-show

用法和功能与v-if基本一致

二者区别：

​	当v-if条件为false时，包含v-if指令的元素，根本不会存在dom中（直接删除dom）

​	当v-show条件为false时，只是给元素添加了一个样式 display : none

## 九、计算属性

模板内的表达式非常便利，但是设计它们的初衷是用于简单运算的。在模板中放入太多的逻辑会让模板过重且难以维护。

对于任何复杂逻辑，都应当使用**计算属性**。

### 1.基本使用

计算属性的方法写在Vue的computed属性内

~~~js
const app = new Vue({
    el: "#app",//用于挂载要管理的元素
    data: {//定义数据
        name:"huahua"
    },
    //计算属性
    computed:{
        fullName:function(){
            return this.name+" "+this.name
        }
    }
})
~~~

此处HTML的{{	}}内要使用计算属性方法，则可以直接写方法名。因为此处只是一个属性

~~~html
<div id="app">
    <h2>{{fullName}}</h2>
</div>
~~~

### 2. computed内置的setter和getter

计算属性一般是没有set方法的，是只读属性

因为通常只用到get方法，所以为了简写，才直接写成常用的方法声明的形式

差不多就是ES5的访问器

### 3.计算属性和methods的区别

计算属性有缓存，相同代码只会执行一次

methods是执行函数，调用多少次就执行多少次

当有大量重复操作（for循环之类）时，更推荐用计算属性

## 十、常见的数组的响应式内置方法

### 1. push

数组.push('xx')

在数组末尾添加元素

### 2. pop

数组.pop('xx')

删除数组最后一个元素

### 3. shift

数组.shift('xx')

删除数组中的第一个元素

### 4. unshift

数组.unshift('xx')

在数组开头添加元素

### 5. splice

数组.splice('xx','xx','xx',......)

找到数组指定位置，删除指定个数的元素，并替换或插入指定元素

### 6. sort

数组.sort( )

数组排序

### 7. reserve

数组.reserve( )

翻转数组元素



注：直接通过数组索引来修改数组元素，不是响应式的

## 十一、v-model

在表单控件或者组件上创建双向绑定

v-model实际上是一个语法糖，背后的本质是两个操作：1. v-bind绑定一个value属性。2. v-on指令给当前元素绑定input事件

也就是说

~~~html
<input type="text" v-model="message">
~~~

等同于

~~~html
<input type="text" v-on:input="message=$event.target.value" v-bind:value="message">
~~~

### 1.简单使用

~~~html
<div id="app">
    <input type="text" v-model="message">{{message}}
</div>
~~~

此处的message仅仅只是一个变量

页面加载后，输入框内就会自动出现message变量的值

并且，只要输入框内的值无论是添加还是删除字符，对应的{{message}}也会变化

这时，无论是更改代码中的变量值，还是直接在页面的输入框内修改值，都会对应的立即变化，这就是双向绑定

### 2.结合radio使用

~~~html
<div id="app">
    <label for="male">
        <input type="radio" id="male" value="男" v-model="sex">男
    </label>
    <label for="female">
        <input type="radio" id="female" value="女" v-model="sex">女
    </label>
    <h2>{{sex}}</h2>
</div>
~~~

双向绑定一个变量sex后，点击radio时会将对应的value值赋给变量sex

v-model绑定变量相同，则实现了radio互斥的效果，和name相同实现互斥一致

### 3.结合checkbox使用

~~~html
<div id="app">
    <input type="checkbox" value="篮球" v-model="hobby">篮球
    <input type="checkbox" value="足球" v-model="hobby">足球
    <input type="checkbox" value="羽毛球" v-model="hobby">羽毛球
    <input type="checkbox" value="排球" v-model="hobby">排球
    <h2>你的爱好是:{{hobby}}</h2>
</div>
~~~

将多个CheckBox的value存放入hobby数组中

### 4.结合select使用

（1）选择一个

~~~html
<div id="app">
    <select name="a" id="" v-model="fruit">
        <option value="苹果">苹果</option>
        <option value="香蕉">香蕉</option>
        <option value="荔枝">荔枝</option>
        <option value="葡萄">葡萄</option>
    </select>
    <h2>{{fruit}}</h2>
</div>
~~~

（2）选择多个

添加multiple 属性规定可同时选择多个选项。

注意，要将选择的值放在一个数组内

~~~html
<div id="app">
    <select name="a" v-model="fruits" multiple>
        <option value="苹果">苹果</option>
        <option value="香蕉">香蕉</option>
        <option value="荔枝">荔枝</option>
        <option value="葡萄">葡萄</option>
    </select>
    <h2>{{fruits}}</h2>
</div>
~~~

### 5. input的值绑定

动态绑定input的值

~~~html
<label v-for="item in arr">
    <input type="checkbox" :value="item" v-model="ff">{{item}}
</label>
~~~

### 6.常用修饰符

（1）.lazy

只有在失去焦点或者在输入框内回车时，才会实时绑定

（2）.number

在输入框内输入数字时，会自动将数字转为字符串类型。

加了number修饰符后，双向绑定的变量会一直是number类型

（3）.trim

去除输入内容首尾空格

## 十二、组件

组件化是Vue.js的重要思想

提供了一种抽象，让我们可以开发出来一个个独立可复用的小组件来构造我们的应用

任何的应用都会被抽象成一颗组件树

组件是可复用的 Vue 实例，且带有一个名字。所以它们与 new Vue接收相同的选项，例如 data、computed、watch、methods以及生命周期钩子等。仅有的例外是像 el这样根实例特有的选项。

所有的组件都继承自vue类的原型，可以给vue的原型中添加方法或属性，即给组件添加属性或方法

### 1.使用步骤

（1）创建组件构造器

（2）注册组件

（3）使用组件

### 2.基本使用

html部分

~~~html
<div id="app">
    <myfirstcpn></myfirstcpn>
    <myfirstcpn></myfirstcpn>
</div>
~~~

js部分

~~~js
//创建组件构造器对象
const cpn=Vue.extend({
    //自定义组件的模板
    template:`
<div>
	<h2>你好</h2>
</div>`
})
//注册组件
Vue.component('myfirstcpn',cpn)

const app=new Vue({
    el:"#app",
    data:{
    }
})
~~~

组件必须挂载在某个Vue实例下，否则不会生效

现在几乎不再使用vue . extend的写法，而是直接使用，注册的语法糖vue . component来注册组件（需要传递两个参数，参数1为注册组件的标签名，参数2为组件构造器，组件构造器对在该语法糖中是一个对象字面量形式）

### 3.全局组件和局部组件

（1）全局组件

全局组件可以放在多个Vue实例里面使用

直接在全局作用域下注册组件后，就可以直接使用

~~~js
Vue.component('cpn',{
    template:`
        <div>
            <h2>你好,我是全局</h2>
        </div>`
})
~~~

（2）局部组件

在vue实例的选项中的components属性中，注册的组件

~~~js
const app=new Vue({
    el:"#app",
    components:{
        //此处属性为组件名，属性值为组件构造器对象
        mypn:{
            template:`
            <div>
                <h2>你好，我是局部</h2>
            </div>`
        }
    }
})
~~~

### 4.父组件和子组件

vue实例也可以看作是一个组件，为root组件

~~~~js
const cpn2=Vue.extend({
    template:`
	<div>
		<h2>你好,我是son</h2>
	</div>`
})
const cpn1=Vue.extend({
    //在父组件中使用子组件
    template:`
	<div>
		<h2>你好,我是dad</h2>
		<cpnson></cpnson>
	</div>`,
    components:{
        cpnson:cpn2
    }
})
const app=new Vue({
    el:"#app",
    components:{
        cpndad:cpn1
    }
})
~~~~

此处cpndad是父组件，cpnson是子组件，并要在父组件下注册子组件之前，就创建好构造器对象，否则报错

注意：如果想要使用组件，则必须在全局或局部中注册过组件。只在父组件中注册的子组件，也只能在当前父组件中使用。

### 5.组件模板分离

（1）抽离出来写在script标签内

可以将组件中的template模板语句抽离出来，写在script标签内，注意type的变化，并加上一个id

然而这种方法使用率很低

~~~html
<script type="text/x-template" id="cpn">
    <div>
        <h2>分离模板写法</h2>
    </div>
</script>
~~~

使用

~~~js
 Vue.component('cpn',{
 	template:"#cpn"
 })
~~~

（2）写在template标签内

这种方法最常用

~~~js
<template id="cpn">
    <div>
        <h2>分离模板写法</h2>
    </div>
</template>
~~~

使用

~~~js
 Vue.component('cpn',{
 	template:"#cpn"
 })
~~~

### 6.组件中的data

组件是一个单独功能模块的封装

这个模块具有自己的HTML模板，也可以有属性自己的数据data，data必须是函数，且data必须返回一个对象

组件不能直接访问vue实例的data

（1）基本使用

组件模板部分

~~~html
<template id="cpn">
    <div>
        <h2>分离模板写法</h2>
        <h2>{{message}}</h2>
    </div>
</template>
~~~

js部分

~~~js
Vue.component('cpn',{
    template:"#cpn",
    data(){
        return {
            message:"nihao"
        }
    }
})
const app=new Vue({
    el:"#app"
})
~~~

（2）data为什么是函数

每次调用data的数据时，会执行一次，产生一个新的函数对象，地址值不同，对象不同，则不同的组件的相同变量互不影响。

且组件的data中的变量和vue实例中的data的变量是不同的，浏览器解析组件时不会查找vue中的同名变量

### 7.父子组件通信

在开发中，一些数据需要从上层传递给下层

如果在一个页面中，我们从服务器中请求了很多的数据

其中一部分数据，并非是我们整个页面的大组件来展示，而是需要下面的子组件进行展示

但是，并不会让子组件再次发送一个网络请求，而是直接让父组件将数据传递给给子组件

（1）父组件通过props向子组件传递数据



1）props属性值为数组（该方法不常使用）

props的属性值可以是一个数组，数组中存放的是用来接收父组件的数据的变量，但是要以字符串的形式存放

~~~js
const cpn={
    template:'#cpn',
    props:['cmovies']
}
const app=new Vue({
    el:"#app",
    data:{
        message:"你好",
        movies:['复仇者联盟','雷神','蝙蝠侠','超人','钢铁侠']
    },
    components:{
        //此处的cpn就是ES6的增强写法，相当于cpn:cpn
        cpn
    }
})
~~~

HTML部分要用v-bind来给组件动态绑定数据。此处表示，子组件props的属性值中的字符串变量，来接收父组件数据

注意，此处绑定时，要将字符串转为变量的形式后，再绑定

~~~html
<div id="app">
    <cpn :cmovies="movies"></cpn>
</div>
~~~

2）props属性值为对象（该方法最常使用）

注意在props中的属性不能使用驼峰命名法，如果要在组件模板中，使用驼峰命名法命名的变量，必须将其转换形式。例如:**c Info—>c-info**

属性值为对象，可以在对象中实现类型验证，类型也可以是自定义的构造函数类型

**如果属性值为对象的形式，则该变量要用v-bind绑定**

**如果属性值为无意义的字符串的形式，则该变量可以不用v-bind绑定，而直接作为一个属性加在标签上**

~~~js
props:{
	cmovies:Array,
    cmessage:String
}
~~~

可以提供一些默认值

默认值是组件还未通信时的初始值

还可以设置该属性的值是必须要传递的

~~~js
props:{
	cmessage:{
		type:String,
        //此处是设置cmessage的默认值
		default:'aaaa'，
        required:true
	}
}
~~~

然而当变量类型是对象或数组时，默认值必须是一个**函数**

~~~js
props:{
	cmovies:{
		type:Array,
        //此处是设置cmessage的默认值
		default(){
            return []
        }，
        required:true
	}
}
~~~

当变量类型可能是多种类型时

~~~js
props:{
	cmessage:{
		type:[String,Number]
	}
}
~~~

（2）子传父

发生场景：子组件触发事件，需要展示数据，向父组件发射请求，父组件根据子组件的请求，来发送给子组件所需的数据

在子组件中的methods里，写一个函数。

通过this.$emit来发射自定义事件到父组件，以此来实现子传父通信

~~~js
methods:{
    btnClick(){
        //子组件向父组件发射一个自定义事件
        this.$emit('btndad-click')
    }
}
~~~

子组件模板

每执行一次点击事件，就发送一次自定义事件到父组件

~~~html
<div>
    <button v-for="(item, index) in movies" @click="btnClick()">{{item.name}}</button>
</div>
~~~

父组件模板

通过v-on来监听，子组件发射过来的自定义事件，并在父组件中定义执行函数，来实现相关操作

~~~html
<div id="app">
    <cpn @btndad-click="cpnClick"></cpn>
</div>
~~~

### 8.父子通信结合双向绑定

js部分

~~~js
const app = new Vue({
    el: "#app",
    data: {
        num1: 0,
        num2: 1
    },
    methods:{
        changeinput11(val){
            this.num1=parseInt(val)
        },
        changeinput21(val){
            this.num2=parseInt(val)
        }
    }，
    components: {
        //此处的cpn就是ES6的增强写法，相当于cpn:cpn
        cpn: {
            template: '#cpn',
            props: {
                //定义两个变量来接收父组件的变量
                number1: Number,
                number2: Number
            },
            data() {
                return {
                    //不能直接绑定number，必须要中转一下
                    dnumber1: this.number1,
                    dnumber2: this.number2
                }
            }，
            methods:{
                //每次输入框中输入时，就向父组件
                //发送事件，改变父组件中的变量
                inputnum1(e){
                    this.dnumber1=e.target.value
                    this.$emit('changeinput1',this.dnumber1)
                },
                inputnum2(e){
                    this.dnumber2=e.target.value
                    this.$emit('changeinput2',this.dnumber2)
                }
            }
        }
    }
})
~~~

子组件模板

此处的输入框，不能直接双向绑定props的变量，必须通过data或者计算属性来双向绑定

~~~html
<div>
    <h2>props:{{number1}}</h2>
    <h2>data:{{dnumber1}}</h2>
    <input type="text" :value="dnumber1" @input="inputnum1">
    <h2>props:{{number2}}</h2>
    <h2>data:{{dnumber2}}</h2>
    <input type="text" :value="dnumber2" @input="inputnum2">
</div>
~~~

父组件模板

~~~html
<div id="app">
    <!--父组件的变量动态绑定子组件的props变量-->
    <cpn :number1="num1" :number2="num2" @changeinput1="changeinput11" @changeinput2="changeinput21"></cpn>
</div>
~~~

### 9. watch侦听器

vue实例选项中的watch属性，与data、methods等属性同级

监听属性变化，做出变化的相应操作

### 10.父组件直接访问子组件

使用$children或者$refs

（1）$children

可以访问到父组件的所有子组件

通过$children返回的是一个组件对象数组。要先知道子组件的索引值，才可以访问。使用较为不便，不推荐使用

~~~js
const app = new Vue({
    el: "#app",
    data: {
        message: "你好"
    },
    methods:{
        btnClick(){
            //通过$children返回的是一个组件对象数组
            let cpn=this.$children[0]
            console.log(this.$children)//(2) [VueComponent, VueComponent]
            cpn.showMessage()//子组件的方法
            console.log(cpn.name)//qy
        }
    },
    components: {
        cpn:{
            template:"#cpn",
            methods:{
                showMessage(){
                    console.log('子组件的方法');
                }
            },
            data(){
                return {
                    name:'qy'
                }
            }
        }
    }
})
~~~

（2）$refs

给子组件加上属性ref，相当于给该组件命名为指定值

~~~html
<div id="app">
    <cpn ref="zujian"></cpn>
    <button @click="btnClick">按钮</button>
</div>
~~~

调用时，可以直接根据命名，来获取指定组件对象

且this.$refs返回的是一个对象，默认是一个空对象

~~~js
methods:{
    btnClick(){
        console.log(this.$refs.zujian)
    }
}
~~~

### 11.子组件直接访问父组件

（1）$parent

访问当前组件的父组件

返回的是一个组件对象

~~~js
const app = new Vue({
    el: "#app",
    data: {
        message: "你好"
    },
    components: {
        cpn: {
            template: "#cpn",
            data(){
                return {
                    name:"中间组件"
                }
            },
            components: {
                cpnc: {
                    template: "#cpnc",
                    methods: {
                        btnClick() {
                            console.log(this.$parent)
                        }
                    }
                }
            }
        }
    }
})
~~~

（2）$root

访问根组件

返回的是一个对象

~~~js
components: {
    cpnc: {
        template: "#cpnc",
            methods: {
                btnClick() {
                    console.log(this.$root.message)
                }
            }
    }
}
~~~

### 12.插槽slot

组件的插槽是为了让我们封装的组件更具有扩展性

相当于事先预留一块位置

当有一样的东西抽取到组件中，将不同的地方用插槽来替换。这样就可以让使用者根据自己的需求，来决定插槽中插入什么内容

（1）基本使用

子组件模板

预留一块位置，写上slot标签

slot标签数不限

slot标签

~~~html
<div>
    <h2>组件</h2>
    <p>我是组件</p>
    <slot></slot>
</div>
~~~

可以直接在模板内，给插槽里写内容，表示为默认值，使用时会调用默认值

如果有的组件，插槽处布局不同，则可以直接写上，会直接覆盖默认值

~~~html
<div>
    <h2>组件</h2>
    <p>我是组件</p>
    <slot>
    	<button>按钮</button>
    </slot>
</div>
~~~

使用模板时，直接在组件内写，就相当于在预留的插槽处写

且不限于一个标签，也可以是多个标签

~~~html
<div id="app">
    <mycpn>
        <button>按钮</button>
    </mycpn>
    <mycpn>
        <input type="text">
    </mycpn>
</div>
~~~

（2）具名插槽

在模板里，给每个slot标签加上name属性。这样，无论模板中怎么写。在使用模板时，所写内容都不会覆盖默认值

若要在使用时，使覆盖指定slot标签的默认值，可以给组件标签加上v-slot : （指定slot标签的name的属性值）

模板部分

~~~html
<template id="mycpn">
    <div>
        <slot name="h1">
            <button>按钮1</button>
        </slot>
        <slot name="h2">
            <button>按钮2</button>
        </slot>
        <slot name="h3">
            <button>按钮3</button>
        </slot>
    </div>
</template>
~~~

使用模板

1）覆盖一个插槽处内容

~~~html
<div id="app">
    <mycpn v-slot:h2><span>你好</span></mycpn>
</div>
~~~

2）覆盖多个插槽处，且可以自由选择覆盖哪个

~~~html
<div id="app">
    <mycpn>
        <template v-slot:h1>
            <span>按钮1</span>
        </template>
        <template v-slot:h2>
            <span>按钮2</span>
        </template>
        <template v-slot:h3>
            <span>按钮3</span>
        </template>
    </mycpn>
</div>
~~~

### 13.作用域插槽

vue实例的模板在vue实例的作用域中查找相关数据

组件模板在组件作用域中查找相关数据

只会在其对应的作用域内编译

<hr>

让插槽内容能够访问子组件中才有的数据，用父组件来替换插槽的内容，但是父组件的数据来自于子组件

使用组件模板时

使用v-slot指令，给default自定义一个名字，调用子组件数据时，就用自定义的名字，来调用子组件中自定义的属性

v-slot : default="slotla"	缩写是	#default="slotla"

~~~html
<div id="app">
    <mycpn></mycpn>
    <mycpn >
        <template v-slot:default="slotla">
            {{slotla.data}}
        </template>
    </mycpn>
    <mycpn></mycpn>
</div>
~~~

组件模板

此处先给插槽绑定一个自定义属性，并将一个子组件中的变量绑定给该自定义属性

~~~html
<template id="mycpn">
    <div>
        <slot v-bind:data="pLanguages">
            <ul>
                <li v-for="(item, index) in pLanguages">{{item}}</li>
            </ul>
        </slot>
    </div>
</template>
~~~

## 十三、webpack

Webpack 是一个前端资源加载/打包工具。它将根据模块的依赖关系进行静态分析，然后将这些模块按照指定的规则生成对应的静态资源。

Webpack 可以将多种静态资源 js、css、less 转换成一个静态文件，减少了页面的请求。

帮助处理模块间的依赖关系，进行模块化开发管理

且不仅仅是js文件，css、图片、json文件等等在webpack中都可以被当作模块来使用

### 1.基本使用

将多个js文件导入到一个入口文件main . js中

打包时，通过以下命令打包入口文件

~~~npm
webpack ./src/main.js ./dist/res.js
~~~

此处第一个路径是入口js文件的路径，第二个路径是要保存打包结果文件的路径

### 2.使用优化

将webpack的配置信息，写在一个固定名称的js文件中:webpack . config . js

~~~js
//commonJS规范的导入方式
const path=require('path')

module.exports={
    //打包文件所在路径
    entry:"./src/main.js",
    //打包结果文件路径
    output:{
        //此处动态的获得绝对路径
        //此处的第一个参数固定，第二个参数为打包结果所在文件夹
        path:path.resolve(__dirname,'dist'),
        filename:"bundle.js"
    }
}
~~~

打包时，在终端直接输入webpack 即可打包

也可以用 npm run build 命令打包，但是需要先在package.json的scripts中，将该命令和webpack映射起来（如下代码）

且执行时，会优先在本地中找，然后再在全局中找

~~~json
"scripts": {
    "test": "echo \"Error: no test specified\" && exit 1",
    "build":"webpack"
  }
~~~

### 3. loader

loader是webpack中一个非常核心的概念

在开发中不仅要有基本的js代码处理，我们也需要加载css、图片、也包括一些高级的将es6转为es5代码，将typescript转为es5代码，将scss、less转为css，将.jsx、.vue文件转为js文件等等

而webpack本身不具有转换的功能，需要给webpack扩展对应的loader

注意：在npm相关模块时，加上-dev表示只有开发时才依赖

（1）css-loader

在安装后，该工具不能解析css代码，只能加载。所以还需要安装style-loader，该工具负责将样式加到dom上

js入口文件上通过以下语句来导入css文件

~~~js
require('./css/top.css')
~~~

webpack . config.js文件中要加入以下语句

~~~js
module: {
    rules: [
        { test: /\.css$/, use: ['style-loader','css-loader'] }
    ]
}
~~~

（2）图片文件url-loader

webpack . config.js文件中要加入以下语句

注意：当加载的图片小于limit时，会将图片编译成base64字符串形式

​			当加载的图片大于limit时，要使用file-loder模块来加载，否则报错（file-loader模块不需要配置）

~~~js
module: {
    rules: [
      { test: /\.css$/, use: ['style-loader', 'css-loader'] },
      { test: /\.(png|jpg|gif)$/, use: [{ loader: 'url-loader', options: { limit: 8192 } }] }
    ]
  }
~~~

大于limit的图片，打包后会以生成的哈希值为名，出现在打包结果所在的文件夹，且会调用该哈希值名字的图片。要在webpack . config .js的属性output中添加该语句

> publicPath:'dist/'

~~~js
output: {
    //此处应该动态获取该绝对路径
    path: path.resolve(__dirname, 'dist'),
    filename: "bundle.js",
    //将url自动与该属性值拼接
    publicPath:'dist/'
  }
~~~

webpack帮我们生成了一个非常长的名字

但是在实际开发中，可能对打包的图片名字有一定要求

比如，将所有打包后的图片放在一个文件夹中，跟上图片原来的名称，同时也是为了防止重复，可以在图片的配置选项中进行设置

~~~js
{ 
    test: /\.(png|jpg|gif)$/, 
        use: [
        {
            loader: 'url-loader', 
            options: {
                limit: 8192,
                //图片打包后生成的格式
                name:'img/[name].[hash:8].[ext]' 
            }
        }
    ] 
}
~~~

（3） ES6转为ES5	babel-loader

有些浏览器无法识别es6，那么打包时要将es6转为es5

在webpack . config . js中添加以下配置 

~~~js
{
    test:/\.js$/,
        //排除指定文件夹中的js文件
        exclude:/(node_modules|bower_components)/,
            use:{
                loader:'babel-loader',
                    options:{
                        presets:['es2015']
                    }
            }
}
~~~

### 4.使用vue的配置

本地npm安装vue模块（不要加-dev，因为无论是开发时还是打包后，都要依赖vue）

~~~js
npm install vue --save
~~~

使用vue框架，要先导入vue模块

~~~js
import Vue from 'vue'
~~~

如果直接打包使用，则会跳出以下错误

~~~
You are using the runtime-only build of Vue where the template compiler is not available. Either pre-compile the templates into render functions, or use the compiler-included build.
~~~

这是因为vue有两种形式的代码 runtime-compiler（模板）模式和runtime-only模式（运行时），vue模块的package.json的main字段默认为runtime模式， 指向了"dist/vue.runtime.common.js"位置。

在webpack . config .js中的module.exports里添加以下代码，可以解决该问题

~~~js
resolve: {
    alias: {
        'vue$': 'vue/dist/vue.esm.js' 
    }
}
~~~

错误是因为在导入vue时，会查找默认指向的一个文件，这个文件没有runtime-compiler模式。而这里就是更改它的默认指向文件，并且现在的vue是runtime-compiler（模板）模式

### 5. plugin

以下插件都要注意版本问题

（1）版权声明插件使用

在webpack . config . js中先导入webpack自带的这个插件

~~~js
//导入版权声明的plugin
const webpack=require('webpack')
~~~

再在module.export中添加以下语句

~~~js
plugin:[new webpack.BannerPlugin('最终版权归属于@骑士所有')]
~~~

打包后可以看到js文件头部已添加对应的版权信息

（2）打包HTML

在真实发布项目时，发布的是dist文件夹中的内容，但是dist文件夹中如果没有index . html文件，那么打包的js等文件也就没有了意义。

此时，我们需要将开发时的index . html文件也打包到dist文件夹中，这个时候就可以使用HtmlWebpackPlugin插件

该插件的功能：

​		自动生成一个index . html文件。将打包的js文件，自动通过script标签插入到指定body中

安装该插件的命令：

~~~
npm install html-webpack-plugin --save-dev
~~~

配置代码

~~~js
plugins:[
    new HtmlWebpackPlugin({
      template:'index.html'
    })
  ]
~~~

（3）js压缩

开发阶段，不建议使用此插件。

在项目发布前要对文件进行压缩，可以使用uglifyjs-webpack-plugin插件

~~~
npm install uglifyjs-webpack-plugin@1.1.1 --save-dev
~~~

配置代码

~~~js
plugins:[
    //打包生成index.html
    new HtmlWebpackPlugin({
      template:'index.html'
    }),
    //压缩插件
    new uglifyjs()
  ]
~~~

（4）搭建本地服务器

开发时需要搭建，项目发布时，不需要

~~~
npm install webpack-dev-server@2.9.3
~~~

webpack . config .js配置

~~~js
devServer:{
    //为哪个文件夹提供服务
    contentBase:'./dist',
    //表示是否实时监听
    inline:true
  }
~~~

package . json配置

~~~
"scripts": {
    "test": "echo \"Error: no test specified\" && exit 1",
    "build": "webpack",
    //服务器启动配置
    "dev":"webpack-dev-server --open"
  }
~~~

### 6.配置文件分离

在开发时和项目发布时的配置文件是不同的

可以将webpack . config. js放在一个build文件夹中，并分离成三个文件，分别是基础配置文件、开发配置文件、发布配置文件。并在分离的文件中导入基础文件。这样子可以在打包时，省去不必要的配置

安装合并工具命令

~~~
npm install webpack-merge --save-dev
~~~

以开发配置文件为例

~~~js
//合并工具
const webpackMerge = require('webpack-merge')
//导入基础配置
const baseConfig = require('./base.config')
module.exports =webpackMerge(baseConfig, {
    //开发时只需要该配置
  devServer:{
    //为哪个文件夹提供服务
    contentBase:'./dist',
    //表示是否实时监听
    inline:true
  }
})
~~~

发布配置文件，与开发配置文件类似，都是导入基础配置文件，并额外的写相关配置，最终将配置合并

package.json要有相应配置，将分离后的配置文件与原有命令关联起来

~~~
"scripts": {
    "test": "echo \"Error: no test specified\" && exit 1",
    "build": "webpack --config ./build/prod.config.js",
    "dev": "webpack-dev-server --open --config ./build/dev.config.js"
  }
~~~

## 十四、vue组件化开发

在vue实例中同时存在el和template，可以在template中写HTML代码，那么在HTML文件中，template里的HTML代码会将el挂载的div代替掉。

在vue开发中，更加规范的将页面的每一个部分看作组件，组件代码写在vue文件中，最后再导入到入口js文件

在开发中，只留一个入口HTML文件，几乎没有什么代码

vue文件格式

~~~
<template>
  <div>
    <h2>{{message}}</h2>
    <button @click="btnClick">按钮</button>
  </div>
</template>

<script>
  export default {
    name: '',
    data() {
      return {
        message: "你好"
      }
    },
    methods: {
      btnClick() {
        console.log(12)
      }
    }
  }
</script>

<style scoped>
</style>
~~~

在js入口文件中的操作

~~~js
//引入安装好的vue模块
import Vue from 'vue'
//引入自己编写的vue组件
import App from './vue/app.vue'
new Vue({
    el:"#app",
    //此处模板是一个组件，编译时会找是否有这个组件，
    //找到子组件App并使用
    template:'<App/>',
    components:{
        App
    }
})
~~~

但是打包时会报错，因为webpack无法解析vue，需要下载对应的loader和compiler

~~~
//此处是本地安装
npm install --save-dev vue-loader vue-template-compiler
~~~

相应的，在webpack . config .js的module内中要进行相关配置

~~~js
{
	test:/\.vue$/,
	use:['vue-loader']
}
~~~

## 十五、vue CLI脚手架

在开发大型应用时，必然会使用到vue CLI

要考虑到代码目录结构、项目结构和部署、热加载、代码单元测试等事情

如果每个项目都要手动完成这些工作，那么工作会十分低效。所以需要脚手架工具来帮助完成

CLI是 Command-Line Interface，翻译为命令行界面，但是俗称脚手架

Vue CLI是一个官方发布的vue.js项目脚手架

**使用vue-cli可以快速搭建vue开发环境以及对应的webpack配置**

### 1.安装脚手架

安装命令（通常都是全局安装）

~~~
npm install @vue/cli -g
~~~

### 2. runtime-only和runtime-compiler的区别

vue程序运行过程:

1）runtime-compiler

template—>ast（抽象语法树）—>render—>vdom（虚拟dom）—>UI（真实dom）

template解析成ast，ast编译成render函数，render函数走向虚拟dom（vdom），最后虚拟dom渲染成真实的UI

~~~js
new Vue({
  el: '#app',
  components: { App },
  template: '<App/>'
})
~~~

2）runtime-only

render—>vdom—>UI

~~~js
new Vue({
  el: '#app',
  render: h => h(App)//这里的h表示的就是createElement函数
})
~~~

两者相比，runtime-only模式省去了前两步，并将compiler模式的components和template属性用render函数来代替

~~~js
render:function(createElement){
	return createElement('h2',{class:'box'},[''])
}
~~~

createElement是一个回调函数，第一个参数可以是模板、可以是标签，也可以是一个组件，第二个参数是标签属性，第三个参数是一个数组，数组内表示标签的内容（数组内还可以嵌套createElement函数）

<hr/>

而在runtime-only模式中，是直接将template模板编译成render函数，然后从render函数开始进行一步步的处理。这样的直接将template模板编译成render函数的过程是由package.json文件中的配置的vue-template-compiler完成的

### 3.自定义配置文件

固定名称vue.config.js文件，在该文件中设置

## 十六、路由vue-router 

基于路由和组件

路由用于设定访问路径，将路径和组件映射起来

在vue-router的单页面复应用中，页面的路径的改变就是组件的切换

### 1.基础概念

 路由就是通过互联的网络把信息从源地址传输目的地址的活动

路由器提供了两种机制：路由和转送

路由是决定数据包从来源到目的地的路径

转送是将输入端的数据转移到合适的输出端

前端路由描述的是url和页面资源的映射关系。这种映射是单向的，即 URL 变化引起 页面更新（无需刷新页面）。

### 2. url的hash和h5的history

都可以改变url，且不会刷新页面

路由配置时，就是以这两种之一的操作来实现

（1）url的hash

url的hahs也就是锚点，本质上是改变window.location的href属性

我们可以通过直接赋值location.hash来改变href，并且页面不会刷新

~~~js
location.hash='xx'
~~~

（2）h5的history

history 提供了 pushState 和 replaceState 两个方法，这两个方法改变 URL 的 path 部分不会引起页面刷新

 pushState方法，入栈操作

可以通过back方法，移除当前栈顶url（等同于go（-1）），该方法相当于浏览器页面回退操作

可以通过forward方法，将移除的栈顶url压栈（等同于go（1）），该方法相当于浏览器页面回退后再前进操作，回到最后页面

~~~js
history.pushState({},'','xx')
~~~

replaceState 方法，不可以回退，相当于替换掉之前的url

~~~js
history.replaceState ({},'','xx')
~~~

### 3.安装

通过以下命令来安装，由于无论是开发还是发布时，都要用到路由，所以只要用--save

~~~
npm install vue-router --save
~~~

然而在用脚手架创建项目时，有创建vue-router选项，可以提前安装好，无需上述该命令

### 4.使用步骤

（1）创建路由组件

（2）配置路由映射：组件和路径映射关系

（3）使用路由：通过<router-link>和<router-view>

### 5.简单使用例子

入口vue文件App.vue，使用路由实现跳转

~~~html
<template>
  <div id="app">
     <!--设置url后缀，并映射到url对应的页面-->
    <router-link to="/home">首页</router-link>
    <router-link to="/about">关于</router-link>
    <!--router-view决定渲染位置-->
    <router-view></router-view>  
  </div>
</template>
<script>
export default {
  name: 'App'
}
</script>
<style>
</style>
~~~

router-link标签是一个vue-router中已经内置的组件，他会被渲染成一个a标签

router-view标签会根据当前的路径，动态渲染处不同的组件

网页的其他内容，比如顶部的标题/导航，或者底部的一些版权信息等，会和router-view处于同一等级

在路由切换时，切换的是router-view挂载的组件，其他内容不会发生改变

<hr/>

路由的设置，默认是hash模式

要设置url为history模式，则可以给vuerouter实例对象添加代码

~~~js
 mode:'history'
~~~

~~~js
import Vue from 'vue'
//使用vue-router插件，要先导入
import Router from 'vue-router'
//导入组件
import Home from '../components/home'
import About from '../components/about'

//使用插件，要通过vue.use来使用
Vue.use(Router)
const routes = [
  {
    path: '',
    //重定向,将默认页面设置为home
    redirect: '/home'
  },
  {
    path: '/home',
    name: 'Home',
    component: Home
  },
  {
    path: '/about',
    name: 'About',
    component: About
  }
]
//创建vuerouter实例对象
const router = new Router({
  //定义路由
  routes,
   //设置url为history模式
  mode:'history'
})
//要导出router实例对象
export default router
~~~

在一个模块化工程中使用router，必须要通过 `Vue.use()` 明确地安装路由功能

url对应的组件模板，自己编写即可

### 6. router-link的其他属性

（1）tag

可以指定router-link之后渲染成什么组件，比如下面的 代码会被渲染成一个button标签，而不是默认的a标签

~~~html
<router-link to="/home" tag="button">首页</router-link>
~~~

（2）replace

不会留下history记录，在该属性下，后退键不能返回到上一个页面中

replace属性不需要任何属性值

~~~html
<router-link to="/home" tag="button" replace>首页</router-link>
~~~

（3）active-class

当router-link对应的路由匹配成功后，会自动将当前元素设置一个router-link-active的class，设置active-class可以修改默认的名称

可以通过给router实例对象中添加以下代码，给active类选择器添加样式

~~~js
linkActiveClass:'active'
~~~

### 7.通过代码实现路由跳转

template部分

~~~html
<div id="app">
    <button @click="homeClick">首页</button>
    <button @click="aboutClick">关于</button>
    <router-view></router-view>
</div>
~~~

js部分

通过$router来实现，此处的$router指的是router实例对象

~~~js
export default {
  name: 'App',
  methods: {
    homeClick(){
        //this.$router.push('/home').catch(err => err)
      this.$router.replace('/home').catch(err => err)
    },
    aboutClick(){
      this.$router.replace('/about').catch(err => err)
    }
  },
}
~~~

### 8.动态路由的使用

动态绑定上to属性，并在属性值中，用单引号拼接变量（变量自己定义）

~~~html
<router-link :to="'/user/'+userId">用户</router-link>
~~~

同时在设置路由时，要这样写url的格式（:userId 相当于一个形参，“:”表示后面的变量可以任意，但是必须要有）

~~~js
{
    path:'/user/:userId',
    component:User
  }
~~~

如果要在子组件中获取父组件的路径数据，可以这样设置路由

~~~js
{
    path:'/user/:a',
    component:User
  }
~~~

然后在User组件中，通过$route来调用变量a（this.$route表示当前url对应页面）

~~~js
export default {
  computed: {
    userId() {
      return this.$route.params.a;//此处的变量a必须和路由中设置的变量一样
    },
  },
};
~~~

### 9.懒加载

被打包的页面最后都是放在一个js文件里

但是，都放在一个js文件中，必然会造成这个页面非常的大

如果一次性从服务器请求下来这个页面，可能需要花费一定的时间，甚至页面上会出现短暂的空白

这时候就需要懒加载

路由懒加载的主要作用就是将路由对应的组件打包成一个个js代码块

只有在这个路由被访问到的时候，才加载对应的组件



懒加载的方式：

~~~js
const Home=()=>import('../components/home')
~~~

该方式是最常用的一种

打包后的js代码中，一个子组件会对应一个js文件（通常是以数字开头的js文件）

### 10.嵌套路由

比如在一个home页面，我们希望通过/home/news和/home/message访问一些内容

一个路径映射一个组件，访问这两个路径也会分别渲染两个组件

这就是路由的嵌套

嵌套路由例子：

~~~html
<div>
    <h2>我是首页</h2>
    <p>我是首页内容</p>
    <router-link to="/home/news">新闻</router-link>
    <router-link to="/home/message">消息</router-link>
    <router-view></router-view>
</div>
~~~

在被嵌套的路由下，使用children属性来设置嵌套路由，在子路由中设置路径不用加斜杠

~~~js
{
    //给组件设置一个url
    path: '/home',
    name: 'Home',
    component: Home,
    //当前组件对应的url下的组件
    children:[
      {
        //此处路径不需要加斜杠
        path:'message',
        component:HomeMessage
      },
      {
        path:'news',
        component:HomeNews
      }
    ]
  }
~~~

### 11.传递参数的方式

（1）params

配置路由格式：/router/:id（冒号表示是一个动态的变量）

传递的方式：在router-link标签中，动态绑定to属性，在属性值中动态拼接字符串

~~~~html
<router-link :to="'/user/'+userId">用户</router-link>
~~~~

传递后形成的路径：/router/123，/router/abc

且可以通过$route.  params .变量来获取值

（2）query

通过query将数据传递到子组件中

配置路由格式：/router，也就是普通配置

传递的方式：在router-link标签中，动态绑定to属性。属性值为一个对象，对象可以指定路径和query信息

~~~html
<router-link :to="{path:'/profile',query:{name:'qy',age:18}}">档案</router-link>
~~~

传递后形成的路径：/router/？name=xxx&age=xxx

且可以在子组件中，通过$route.query来获取对象数据

~~~vue
{{$route.query.name}}
~~~

如果通过代码实现路由跳转，也可以通过传入对象，在对象中设置path和query属性的方式来实现

### 12.$router和$route的区别

$router为VueRouter实例，想要导航到不同URL，则使用$router.push方法

$route为当前router跳转对象，里面可以获取到name、path、query、params等

### 13.路由导航守卫

（1）基础概念

在HTML中修改页面标题，是通过title标签来修改，然而SPA（单页面富应用）只有一个固定的HTML，切换路由时，标题无法改变

在vue中，通常使用导航守卫来监听路由的进入和离开

vue-router还提供了beforeEach（前置钩子）和afterEach（后置钩子）的钩子函数，他们会在路由即将改变前和改变后触发

可以使用 router.beforeEach 注册一个全局前置守卫（跳转之前所做的操作）：

每个守卫方法接收三个参数：

- to: Route: 即将要进入的目标路由对象
- from: Route: 当前导航正要离开的路由
- next: 调用该方法，才能进入下一个钩子（钩子也是回调）。通常用作登录跳转的判断，参数为一个指定路径

（2）使用例子

index.js中每个路由都添加

~~~js
meta:{
    title:"xxx"
}
~~~

并给router实例对象添加

~~~js
router.beforeEach((to,from,next)=>{
  document.title=to.matched[0].meta.title//存在路由嵌套时，要使用matched数组来调用
  next()
})
~~~

（3）补充

如果是后置钩子afterEach，不需要调用next函数

beforeEach和afterEach都是全局守卫

此外还有，路由独享的守卫：在指定路由中定义beforeEnter函数（参数与全局前置守卫参数一致）

组件内的守卫：在组件中定义beforeRouterEnter/beforeRouterUpdate函数

### 14. keep-alive

（1）简单使用

是vue内置的一个组件，可以使被包含的组件保留状态（不会被销毁），以避免反复重渲染导致的性能问题。

router-view也是一个组件，如果直接被包在keep-alive里面，所有路径匹配到的视图组件都会被缓存

~~~html
<keep-alive><router-view></router-view></keep-alive>
~~~

且生命周期的钩子函数activated和deactivated，只有在使用keep-alive标签时，才是有效的

（2）常用属性

exclude：排除keep-alive下的组件中，满足条件的字符串（name的属性值）或者正则表达式的组件，如果有多个，则可以用逗号隔开（不能加空格）

include：满足条件的字符串（name的属性值）或者正则表达式的组件，会被缓存

## 十七.前后端分离

随着ajax的出现，有了前后端分离的开发模式

后端只提供API来返回数据，前端通过Ajax获取数据，并且可以通过JavaScript将数据渲染到页面中

这样做最大的优点就是前后端责任清晰，后端专注于数据上，前端专注于交互和可视化

并且移动端出现后，后端不需要进行任何处理，依然使用之前的一套API即可

目前很多网站都采用该模式开发

![image-20210417222614145](D:\web self-learn\HTML+CSS\VUE笔记.assets\image-20210417222614145.png)

## 十八、Vuex

vuex是一个专门为vue.js应用程序开发的状态管理模式

是一个插件，需要手动安装

它采用了集中式存储管理应用的所有组件的状态，并以相应的规则保证状态以一种可预测的方式发生变化

### 1.状态管理

把需要多个组件共享的变量存储在一个对象中

然后，将这个对象放在顶层的vue实例中，让其他组件使用。



在实际项目中，多状态在多界面共享的问题。状态信息中共享的一般是用户的登录状态、用户名称、头像、地理位置等等

这些状态信息，我们都可以放在统一的地方，对他进行保存和管理，而且他们还是响应式的

### 2.安装vuex插件

~~~
npm install vuex --save
~~~

### 3.简单使用

一般建议vuex相关设置放在一个文件夹内，文件夹名推荐为store，下面建立一个index.js文件

~~~js
//vuex的相关设置
import Vuex from 'vuex'
import Vue from 'vue';
//安装插件
Vue.use(Vuex)
//创建对象
const store=new Vuex.Store({
    //存放状态信息
    state:{
        counter:0
    },
    //定义方法，默认会有state对象传入方法作为参数
    mutations:{

    },
    //异步操作
    actions:{

    },
    getters:{

    },
    modules:{

    }
})
export default store
~~~

注意此处创建vuex对象的构造函数名为Vue . Store，且实例对象的属性固定

如果要共享state属性内的值，则通过$store. state. xxx来实现

组件App.js

~~~
<template>
  <div id="app">
    <h2>{{$store.state.counter}}</h2>
    <button @click="$store.state.counter++">+</button>
    <button @click="$store.state.counter--">-</button>
    <Hellovuex></Hellovuex>
  </div>
</template>
<script>
import Hellovuex from './components/Hellovuex'

export default {
  name: 'App',
  data(){
    return {
      
    }
  },
  components:{
    Hellovuex
  }
}
</sript>
<style>
</style>
~~~

### 4. state单一状态树

vuex .store实例对象可以创建多个，但是不便于管理

一般推荐只创建一个实例对象，一个state属性 

将多个状态信息存放在一个实例对象的state属性中

### 5. vuex的getters属性

类似于计算属性，对数据进行一些处理（筛选、排序等）

~~~js
getters:{
    powerCounter(state){//参数甚至可以是getters
        return state.counter*state.counter
    }
}
~~~

组件中使用

~~~html
<h2>{{$store.getters.powerCounter}}</h2>
~~~

### 6. mutation状态更新

mutation中的方式必须是同步方法，否则，developtools工具无法有效的跟踪数据

vuex的store状态更新唯一方式：提交mutation

mutation主要包括两部分：

​	字符串的事件类型

​	一个回调函数，该回调函数的第一个参数就是state

要在组件中使用mutation的方法，当前组件的methods中做相应设置

要通过commit函数，并将mutations中的方法名作为字符串参数传入

commit用来提交mutation中的对应方法，count为payload，接收mutation中自定义的参数

~~~js
methods: {
    add(){
      this.$store.commit('increment')
    },
    reduce(){
      this.$store.commit('decrement')
    },
    addCount(count){
      this.$store.commit('addCount',count)
    }
  },
~~~

mutation的方法

~~~js
mutations:{
    increment(state){
        state.counter++;
    },
    decrement(state){
        state.counter--;
    },
    addCount(state,count){
        state.counter+=count
    }
},
~~~

另一种提交方式，commit中传入一个对象

~~~js
addCount(count){
    this.$store.commit({
        type:'addCount',
        count
    })
}
~~~

mutation中的参数，此时是一个对象，要通过.count形式调用count

~~~js
mutations:{
    increment(state){
        state.counter++;
    },
    decrement(state){
        state.counter--;
    },
    addCount(state,payload){
        state.counter+=payload.count
    }
}
~~~

### 7. vuex的响应式方法

一般在state中，用这些方法来修改数据

（1）Vue . set

Vue. set（要修改的对象，索引/属性名，属性值）

（2）Vue.delete

Vue . delete（要修改的对象，属性名/索引）

### 8. mutation常量类型

为了使代码更加规范

推荐将commit传入的参数，作为常量统一放入一个文件中

使用时，再将其导入当前文件

常量类型文件

~~~js
export default {
    INCREMENT:'increment',
    DECREMENT:'decrement',
    ADDCOUNT:'addCount'
}
~~~

使用时

~~~js
import mutationsType from './store/mutation-types'

mutations:{
    [mutationsType.INCREMENT](state){
        state.counter++;
    },
    [mutationsType.DECREMENT](state){
        state.counter--;
    },
    [mutationsType.ADDCOUNT](state,payload){
        state.counter+=payload.count
    }
},
~~~

### 9. action异步操作

处理异步操作的方法

先在mutations中定义同步操作

~~~js
mutations:{
	updateState(state){
	Vue.set(state.info,1,'大佬')
	}
},
~~~

然后在actions中提交mutations中的方法

~~~js
actions:{
    updateState(context,playload){
        setTimeout(()=>{
            context.commit('updateState')
            console.log(playload.message)
        },3000)
    }
}
~~~

最后再想要使用该方法的组件中，用dispatch来获取actions中的方法

~~~js
methods: {
    updateState(){
        this.$store.dispatch('updateState',{
        	message:'已完成'
      })
    }
}
~~~

也可以用Promise来使用actions

### 10. modules

当state中的数据很多时，会十分臃肿

可以将store分割成多个模块，而每个模块也有自己的state，mutations，actions，getters

vuex会默认将子模块中的属性放到state中

当前的模块只能使用当前模块中的数据和方法，但是在vuex.store的实例中调用所有模块中的数据和方法

在子模块的actions中，可以通过rootState和rootGetters，获取根模块的数据

~~~js
const moduleA={
    state:{
        name:'张三',
    }
}
~~~

~~~js
modules:{
    a:moduleA
}
~~~

### 11.目录组织结构

一般建议将vuex.store实例中的各属性的属性值对象，抽离出来。

在store文件夹下新建各属性相同的名字的js文件，将抽离出来的对象放在各文件中，最后再将各文件的内容导入到index .js文件中

如果有子模块，则在store文件夹下新建子模块文件夹，将子模块的代码放在该文件夹下的新建文件里











