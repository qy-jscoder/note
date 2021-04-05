[TOC]- AJAX
- [一、Ajax简介](#一ajax简介)
  - [1.优点](#1优点)
  - [2.缺点](#2缺点)
- [二、AJAX学习所需的知识点](#二ajax学习所需的知识点)
  - [1.请求报文](#1请求报文)
  - [2.响应报文](#2响应报文)
  - [3.GET和POST两种请求方式](#3get和post两种请求方式)
  - [4.GET和POST的区别](#4get和post的区别)
  - [5.使用原生js进行ajax请求的大致步骤](#5使用原生js进行ajax请求的大致步骤)
  - [6.ie缓存的影响](#6ie缓存的影响)
  - [7.readyState](#7readystate)
- [三、原生js实现ajax请求](#三原生js实现ajax请求)
  - [1.GET方式发送请求](#1get方式发送请求)
  - [2.POST方式发送请求](#2post方式发送请求)
  - [3.服务端响应JSON数据](#3服务端响应json数据)
  - [4.IE缓存问题](#4ie缓存问题)
  - [5.请求超时与异常处理](#5请求超时与异常处理)
  - [6.取消请求](#6取消请求)
  - [7.重复发送请求](#7重复发送请求)
- [四、jQuery发送AJAX请求](#四jquery发送ajax请求)
- [五、AXIOS实现AJAX请求](#五axios实现ajax请求)
- [六、使用fetch函数实现AJAX请求](#六使用fetch函数实现ajax请求)
- [六、同源策略](#六同源策略)
- [七、解决跨域问题](#七解决跨域问题)
  - [1.JSONP](#1jsonp)
  - [2.CORS](#2cors)

## 一、Ajax简介

### 1.优点

可以无需刷新页面而与服务器进行通信（异步通信）

允许根据用户事件来更新部分页面内容

### 2.缺点

没有浏览历史，不能回退

存在跨域问题（一个网站不能向另一个网站发送请求）

SEO（搜索引擎优化）不友好

## 二、AJAX学习所需的知识点

HTTP，超文本传输协议。协议规定了浏览器和万维网服务器之间互相通信的规则

当客户端请求一个网页时，会先通过**http**协议将请求的内容封装在**http**请求报文之中，服务器收到该请求报文后根据协议规范进行报文解析，然后向客户端返回响应报文。

### 1.请求报文

重点是格式与参数

起始行：POST（请求的方法） /s?ie=utf-8（请求的URL）  http/1.1（协议类型和版本）

头部：Host：atguigu.com

​		Cookie：name=guigu

​		等等

空行

主体：username=admin&password=123（发 送的数据）

如果是GET请求，请求体是空的，但是有响应体内容；如果是POST请求，请求体可以不为空，若响应是一个跳转，则响应体为空的

POST的请求体在浏览器的Form Data中

### 2.响应报文

起始行：HTTP/1.1（版本）  200（状态码） OK（状态字符串，即状态码的描述）（状态字符串与状态码对应）

头部：Content-Type：。。。

​		   Content-length：。。。

​			等等

空行

主体（主要返回结果）：返回HTML内容，让浏览器将响应结果提取出来并解析，然后渲染为页面

### 3.GET和POST两种请求方式

（1）GET
向特定的资源发出请求。它本质就是发送一个请求来取得服务器上的某一资源。资源通过一组HTTP头和呈现数据（如HTML文本，或者图片或者视频等）返回给客户端。
（2）POST
向指定资源提交数据进行处理请求（例如提交表单或者上传文件）。数据被包含在请求体中。POST请求可能会导致新的资源的建立和/或已有资源的修改。

### 4.GET和POST的区别

- GET方法的数据参数是暴露在起始行的URL中的，而POST方法的数据参数是在报文主体中的。
- GET方法相对来说没有POST安全，因为它的数据参数可以直接从URL中获取，但是GET的效率更高。
- GET方法的数据参数大小有一定的限制（1024）（原因也是因为它的数据参数是放在URL中的），而POST对数据大小是没有限制的。

本质区别是**GET是从服务器上请求数据，而POST是向服务器发送数据**

### 5.使用原生js进行ajax请求的大致步骤

```js
//创建 XMLHttpRequest 对象
var ajax = new XMLHttpRequest();
//规定请求的类型、URL 以及是否异步处理请求。
ajax.open('GET',url,true);
//发送信息至服务器时请求头的内容编码类型
ajax.setRequestHeader("Content-type", "application/x-www-form-urlencoded"); 
//发送请求，若请求类型为get，则send内为空，若请求类型为post，则send内要输入数据
ajax.send();  
//接受服务器响应数据
ajax.onreadystatechange = function () {
    if (ajax.readyState === 4)
        if(ajax.status >= 200 && ajax.status<300) { 
            .....
        }
};
```

### 6.ie缓存的影响

若是在ie浏览器进行ajax请求，则第一次时会将服务器响应结果保存在本地缓存中，导致第二次不能正常显示响应结果

为了解决该影响，则在设置请求对象初始化时，进行处理

~~~js
xhr.open('GET','http://127.0.0.1:8000/ie?t='+Date.now());
~~~

用时间戳来解决ie缓存的影响

### 7.readyState

~~~markdown
请求对象.readyState的值及解释：

0：请求未初始化（还没有调用 open()）。
1：请求已经建立，但是还没有发送（还没有调用 send()）。
2：请求已发送，正在处理中（通常现在可以从响应中获取内容头）。
3：请求在处理中；通常响应中已有部分数据可用了，但是服务器还没有完成响应的生成。
4：响应已完成；您可以获取并使用服务器的响应了。
~~~

## 三、原生js实现ajax请求

### 1.GET方式发送请求

HTML部分

~~~html
<body>
    <button>点击发送请求</button>
    <div id="result"></div>

    <script>
        //获取button元素
        const btn = document.getElementsByTagName('button')[0];
        const result = document.getElementById("result");
        //绑定事件
        btn.onclick = function() {
            //1. 创建对象
            const xhr = new XMLHttpRequest();
            //2. 初始化 设置请求方法和 url
            xhr.open('GET', 'http://127.0.0.1:8000/server?    
                     a=100&b=200&c=300');
            //3. 发送
            xhr.send();
            //4. 事件绑定 处理服务端返回的结果
            // on  when 当....时候
            // readystate 是 xhr 对象中的属性, 表示状态 0 1 2 3 4
            /* 
            0表示未初始化
            1表示open已经调用完毕
            2表示send已经调用完毕
            3代表返回部分结果
            4表示返回所有结果
            */
            // change  改变
            xhr.onreadystatechange = function() {
                //判断 (服务端返回了所有的结果)
                if (xhr.readyState === 4) {
                    //判断响应状态码 200  404  403 401 500
                    // 2xx 成功
                    if (xhr.status >= 200 && xhr.status < 300) {
                        //处理结果  行 头 空行 体
                        //响应 
                        // console.log(xhr.status);//状态码
                        // console.log(xhr.statusText);//状态字符串
                        // console.log(xhr.getAllResponseHeaders());//所有响应头
                        // console.log(xhr.response);//响应体
                        //设置 result 的文本
                        result.innerHTML = xhr.response;
                    } 
                }
            }


        }
    </script>
</body>

~~~

js部分（服务端部分的代码）

~~~js
const express = require('express');

//2. 创建应用对象
const app = express();

//3. 创建路由规则
// request 是对请求报文的封装
// response 是对响应报文的封装
//server为自定义，只要与前端页面的URL后的名字相同即可
app.get('/server', (request, response) => {
    //设置响应头
    response.setHeader('Access-Control-Allow-Origin', '*');
    //设置响应体
    response.send('HELLO AJAX');
});

//4. 监听端口启动服务（此处的端口号为自定义的）
app.listen(8000, () => {
    console.log("服务已经启动, 8000 端口监听中....");
});
~~~

### 2.POST方式发送请求

html部分

~~~html
<body>
    <div id="result"></div>
    <script>
        //获取元素对象
        const result = document.getElementById("result");
        //绑定事件
        result.addEventListener("mouseover", function() {
            //1. 创建对象
            const xhr = new XMLHttpRequest();
            //2. 初始化 设置类型与 URL
            xhr.open('POST', 'http://127.0.0.1:8000/server');
            //设置请求头
            xhr.setRequestHeader('Content-Type', 'application/x-www-form-urlencoded');
            xhr.setRequestHeader('name', 'atguigu');
            //3. 发送
            xhr.send('a=100&b=200&c=300');
            // xhr.send('a:100&b:200&c:300');
            // xhr.send('1233211234567');

            //4. 事件绑定
            xhr.onreadystatechange = function() {
                //判断
                if (xhr.readyState === 4) {
                    if (xhr.status >= 200 && xhr.status < 300) {
                        //处理服务端返回的结果
                        result.innerHTML = xhr.response;
                    }
                }
            }
        });
    </script>
</body>
~~~

js部分（服务端部分的代码）

~~~js
app.post('/server', (request, response) => {
    //设置响应头,允许所有网站向服务端发送请求
    response.setHeader('Access-Control-Allow-Origin', '*');
    //设置响应体
    response.send('HELLO AJAX POST');
});
~~~

### 3.服务端响应JSON数据


html部分

~~~html
<body>
    <div id="result"></div>
    <script>
        const result = document.getElementById('result');
        //绑定键盘按下事件
        window.onkeydown = function() {
            //发送请求
            const xhr = new XMLHttpRequest();
            //设置响应体数据的类型
            xhr.responseType = 'json';
            //初始化
            xhr.open('GET', 'http://127.0.0.1:8000/json-server');
            //发送
            xhr.send();
            //事件绑定
            xhr.onreadystatechange = function() {
                if (xhr.readyState === 4) {
                    if (xhr.status >= 200 && xhr.status < 300) {
                        //
                        // console.log(xhr.response);
                        // result.innerHTML = xhr.response;
                        // 1. 手动对数据转化
                        /*  let data = JSON.parse(xhr.response);
                         console.log(data);
                         result.innerHTML = data.name; */
                        // 2. 自动转换
                        console.log(xhr.response);
                        result.innerHTML = xhr.response.name;
                    }
                }
            }
        }
    </script>
</body>
~~~

js部分（服务端部分的代码）

~~~js
app.all('/json-server', (request, response) => {
    //设置响应头
    response.setHeader('Access-Control-Allow-Origin', '*');
    response.setHeader('Access-Control-Allow-Headers', '*');
    //响应一个数据
    const data = {
        name: 'hahaha'
    };
    //对对象进行字符串转换
    let str = JSON.stringify(data);
    //设置响应体
    response.send(str);
});
~~~

### 4.IE缓存问题

利用时间戳来实时更新，解决缓存问题

html部分

~~~html
<body>
    <button>点击发送请求</button>
    <div id="result"></div>
    <script>
        const btn = document.getElementsByTagName('button')[0];
        const result = document.querySelector('#result');

        btn.addEventListener('click', function() {
            const xhr = new XMLHttpRequest();
            //利用时间戳来实时更新，解决缓存问题
            xhr.open("GET", 'http://127.0.0.1:8000/ie?t=' + Date.now());
            xhr.send();
            xhr.onreadystatechange = function() {
                if (xhr.readyState === 4) {
                    if (xhr.status >= 200 && xhr.status < 300) {
                        result.innerHTML = xhr.response;
                    }
                }
            }
        })
    </script>
</body>
~~~

服务端

~~~js
app.all('/ie', (request, response) => {
    //设置响应头
    response.setHeader('Access-Control-Allow-Origin', '*');
    response.setHeader('Access-Control-Allow-Headers', '*');
    //设置响应体
    response.send('HELLO IE');
});
~~~

### 5.请求超时与异常处理

html部分

~~~html
<body>
    <button>点击发送请求</button>
    <div id="result"></div>
    <script>
        const btn = document.getElementsByTagName('button')[0];
        const result = document.querySelector('#result');

        btn.addEventListener('click', function() {
            const xhr = new XMLHttpRequest();
            //超时设置 2s 设置
            xhr.timeout = 2000;
            //只要超出自定义的时间就会回调
            xhr.ontimeout = function() {
                    alert("网络异常, 请稍后重试!!");
                }
             //网络异常回调
            xhr.onerror = function() {
                alert("你的网络似乎出了一些问题!");
            }

            xhr.open("GET", 'http://127.0.0.1:8000/delay');
            xhr.send();
            xhr.onreadystatechange = function() {
                if (xhr.readyState === 4) {
                    if (xhr.status >= 200 && xhr.status < 300) {
                        result.innerHTML = xhr.response;
                    }
                }
            }
        })
    </script>
</body>
~~~

服务端

~~~js
app.all('/delay', (request, response) => {
    //设置响应头
    response.setHeader('Access-Control-Allow-Origin', '*');
    setTimeout(() => {
            response.send("延时响应");
        }, 3000)
});
~~~

### 6.取消请求

html部分

~~~html
<body>
    <button>点击发送</button>
    <button>点击取消</button>
    <script>
        //获取元素对象
        const btns = document.querySelectorAll('button');
        let x = null;

        btns[0].onclick = function(){
            x = new XMLHttpRequest();
            x.open("GET",'http://127.0.0.1:8000/delay');
            x.send();
        }

        // abort
        btns[1].onclick = function(){
            x.abort();
        }
    </script>
</body>
~~~

服务端

~~~js
//js代码如上，主要是在前端进行取消操作
~~~

### 7.重复发送请求

重复发送请求，就自动取消重复的请求

html部分

~~~html
<body>
    <button>点击发送</button>
    <script>
        //获取元素对象
        const btns = document.querySelectorAll('button');
        let x = null;
        //标识变量
        let isSending = false; // 是否正在发送AJAX请求

        btns[0].onclick = function(){
            //判断标识变量
            if(isSending) x.abort();// 如果正在发送, 则取消该请求, 创建一个新的请求
            x = new XMLHttpRequest();
            //修改 标识变量的值
            isSending = true;
            x.open("GET",'http://127.0.0.1:8000/delay');
            x.send();
            x.onreadystatechange = function(){
                if(x.readyState === 4){
                    //修改标识变量
                    isSending = false;
                }
            }
        }

        // abort
        btns[1].onclick = function(){
            x.abort();
        }
    </script>
</body>
~~~

服务端

~~~js
//js代码如上，只要是在前端进行取消操作
~~~



## 四、jQuery发送AJAX请求

jQuery封装了三种请求方法

（1）get

~~~js
$('button').eq(0).click(function(){
	//发送请求的URL，发送内容（对象），回调函数,响应体类型
    $.get('http://127.0.0.1:8000/jquery-server',{a:100,b:200},function(data){
    console.log(data);
    },'json')
})
~~~

（2）post

~~~js
$('button').eq(1).click(function(){
    //发送请求的URL，发送内容（对象），成功时的回调函数,从服务端传来的响应体类型（默认是字符串）
    $.post('http://127.0.0.1:8000/jquery-server',{a:100,b:200},function(data)	{
       console.log(data);
    })

})
~~~

（3）通用方法ajax

~~~js
//jQuery的通用型方法，可以控制多个信息，推荐该方法（若自定义程度较低可以用上两种）
$('button').eq(2).click(function(){
    $.ajax({
        url:'http://127.0.0.1:8000/jquery-server',
        data:{a:100,b:200},
        type:'GET',
        //响应体结果
        dataType:'json',
        success:function(data){
            console.log(data);
        },
        //此时设置超时时间为2秒，超出该时间就自动取消请求
        timeout:2000,
        error:function(){
            console.log('出错了');
        },
        //头信息
        headers:{
            c:300,
            d:400
        }
    })

})
~~~

## 五、AXIOS实现AJAX请求

Axios 是一个基于 promise 的 HTTP 库，可以用在浏览器和 node.js 中。

<h4>特性：</h4>

- 从浏览器中创建 [XMLHttpRequests](https://developer.mozilla.org/en-US/docs/Web/API/XMLHttpRequest)

- 从 node.js 创建 [http](http://nodejs.org/api/http.html) 请求

- 支持 [Promise](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Promise) API

- 拦截请求和响应

- 转换请求数据和响应数据

- 取消请求

- 自动转换 JSON 数据

- 客户端支持防御 [XSRF](http://en.wikipedia.org/wiki/Cross-site_request_forgery)

  

  （1）get

~~~js
const btns=document.getElementsByTagName('button');

//配置URL baseURL
axios.defaults.baseURL='http://127.0.0.1:8000';

btns[0].onclick=function(){
    //由于已经配置过baseURL，此时可以不写baseURL直接写其后的地址
    axios.get('/server-axios',{
        //参数
        params:{
            id:100,
            vip:7
        },
        //自定义的头信息
        headers:{
            name:'qq',
            age:20
        }
        //想要处理服务端返回的结果则用then
        //value是自定义的变量
    }).then(value=>{
        //此处的value是自己配置信息的对象
        console.log(value);
    })
}
~~~

（2）post

~~~js
btns[1].onclick = function () {
    //由于已经配置过baseURL，此时可以不写baseURL直接写其后的地址
    
    //post的参数有三个：URL，data，config
    axios.post('/server-axios', {
        //请求体
        username: 'qq',
        password: 123
    }, {
        params: {
            id: 200,
            vip: 8
        },
        headers: {
            name: 'qqq',
            age: 22
        }
    })

}
~~~

（3）axios

该方法最清晰明了

~~~js
btns[2].onclick = function () {
    //由于已经配置过baseURL，此时可以不写baseURL直接写其后的地址
    axios({
        //设置请求方法
        method:'POST',
        //设置地址
        url:'/server-axios',
        //参数
        params: {
            id: 300,
            vip: 3
        },
        headers: {
            name: 'qqq',
            age: 22
        },
        //请求体
        data:{
            username:'ss',
            password:12312
        }
    }).then(response=>{
        //响应状态码
        console.log(response.status);
        //响应状态字符串
        console.log(response.statusText);
        //响应头信息
        console.log(response.headers);
        //响应体
        console.log(response.data);
    })
}
~~~

## 六、使用fetch函数实现AJAX请求

fetch是window对象自带的一个实现ajax请求的方法（返回的也是一个Promise对象）

~~~js
btn.onclick=function(){
    fetch('http://127.0.0.1:8000/server-fetch?vip=10&&id=fetch',{

        method:'POST',
        headers:{
            name:'qy'
        },
        body:'username=admin&&password=123'

    }).then(response=>{
		//若返回的是一个json对象，则可用该方法将其转为对象
        //一般情况用text方法
        return response.json();
    }).then(response=>{
        console.log(response)
    })
}
~~~

## 六、同源策略

同源策略是浏览器的一种安全策略

同源：协议、域名、端口号，必须完全相同（有一个不同就是非同源）

违背同源策略就是跨域

而在实现ajax请求时，默认是遵守同源策略的

## 七、解决跨域问题

此处只记录了主要使用的解决方式

### 1.JSONP

只支持get请求

在网页中有些标签天生就具备跨域能力，如：link，script，img等等

实际例子有：开发时调用的css库，js库时，直接调用的网上的URL就是跨域

~~~html
<script src="https://cdn.bootcdn.net/ajax/libs/axios/0.21.1/axios.min.js"></script>
~~~

JSONP就是利用script标签的跨域能力来发送请求的

 **jsonp 的核心则是动态添加 script标签来调用服务器提供的 js 脚本**。

html部分

~~~html
<body>
    用户名: <input type="text" id="username">
    <p></p>
    <script>
        //获取 input 元素
        const input = document.querySelector('input');
        const p = document.querySelector('p');
        
        //声明 handle 函数
        function handle(data){
            input.style.border = "solid 1px #f00";
            //修改 p 标签的提示文本
            p.innerHTML = data.msg;
        }

        //失去焦点触发事件
        input.onblur = function(){
            //获取用户的输入值
            let username = this.value;
            //向服务器端发送请求 检测用户名是否存在
            //1. 创建 script 标签
            const script = document.createElement('script');
            //2. 设置标签的 src 属性
            script.src = 'http://127.0.0.1:8000/check-username';
            //3. 将 script 插入到文档中
            document.body.appendChild(script);
        }
    </script>
</body>
~~~

服务端

~~~js
app.all('/check-username',(request, response) => {
    const data = {
        exist: 1,
        msg: '用户名已经存在'
    };
    //将数据转化为字符串
    let str = JSON.stringify(data);
    //返回结果
    response.end(`handle(${str})`);
});
~~~

### 2.CORS

CORS是一个W3C标准，全称是"跨域资源共享"（Cross-origin resource sharing）。

它允许浏览器向跨源服务器，发出[`XMLHttpRequest`](http://www.ruanyifeng.com/blog/2012/09/xmlhttprequest_level_2.html)请求，从而克服了AJAX只能同源使用的限制。

CORS需要浏览器和服务器同时支持。目前，所有浏览器都支持该功能，IE浏览器不能低于IE10。

整个CORS通信过程，都是浏览器自动完成，不需要用户参与。对于开发者来说，CORS通信与同源的AJAX通信没有差别，代码完全一样。浏览器一旦发现AJAX请求跨源，就会自动添加一些附加的头信息，有时还会多出一次附加的请求，但用户不会有感觉。

因此，实现CORS通信的关键是服务器（即不需要在客户端操作，只在服务端操作）。只要服务器实现了CORS接口，就可以跨源通信。



CORS通过设置响应头信息来允许跨域请求

（1）允许所有的URL都可以向服务器发送请求，实现跨域

~~~js
response.setHeader("Access-Control-Allow-Origin","*")
~~~

（2）允许特定的URL跨域（此处是允许默认端口向服务器跨域）

~~~js
response.setHeader("Access-Control-Allow-Origin","http://127.0.0.1:5500")
~~~
