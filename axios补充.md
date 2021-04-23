- [一、安装](#一安装)
- [二、在vue项目中的使用](#二在vue项目中的使用)
  - [1.基本使用](#1基本使用)
  - [2.同时发送多个请求](#2同时发送多个请求)
- [三、配置信息](#三配置信息)
- [四、实例和模块封装](#四实例和模块封装)
  - [1.创建实例](#1创建实例)
  - [2.模块封装](#2模块封装)
- [五、拦截器的使用](#五拦截器的使用)
  - [1.请求拦截](#1请求拦截)
  - [2.响应拦截](#2响应拦截)
## 一、安装

~~~
npm install axios --save
~~~

## 二、在vue项目中的使用

### 1.基本使用

~~~js
import axios from 'axios'

axios({
  url:'http://123.207.32.32:8000/home/multidata'
}).then(res=>{
  console.log(res)
})
axios({
  url:'http://123.207.32.32:8000/home/data',
   //通过指定参数来获取接口的数据
  params:{
    type:'pop',
    page:1
  }  
}).then(res=>{
  console.log(res)
})
~~~

### 2.同时发送多个请求

axios. all同时发送多个请求，并返回一个数组

~~~js
axios.all([
  axios({
    url:'http://123.207.32.32:8000/home/multidata'
  }),
  axios({
    url:'http://123.207.32.32:8000/home/data',
    params:{
      type:'pop',
      page:1
    }
  })
]).then(res=>{
  console.log(res) 
})
~~~

在then方法中，使用axios . spread可将数组[res1,res2]，展开为res1，res2两个对象

~~~js
.then(axios.spread((res1,res2)=>{
  console.log(res1)
  console.log(res2) 
}))
~~~

## 三、配置信息

在开发中很多参数是固定的

我们可以进行一些抽取，利用axios的全局配置

~~~js
//url公共部分
axios.defaults.baseURL='http://123.207.32.32:8000/home'
//超出设定时间表示超时
axios.defaults.timeout=5000
~~~

其他的一些常见配置：

![image-20210422232631219](D:\web self-learn\HTML+CSS\axios.assets\image-20210422232631219.png)

## 四、实例和模块封装

### 1.创建实例

很多时候要请求多个端口，就不能使用全局配置了

这时可以创建实例，对每个实例进行其自己的配置

~~~js
const instance = axios.create({
  baseURL: "http://api.jirengu.com",
  timeout: 5000
})
instance({
  url:"/fm/v2/getChannels.php"
}).then(res => {
  console.log(res)
})
~~~

### 2.模块封装

如果每一个组件都要进行网络请求，那么每个组件都要依赖axios，不利于维护

可以将axios网络请求封装在一个文件中，使用时，再导入文件来使用

axios封装文件部分：

~~~js
import axios from 'axios';
export function request(config,success,failure){
    const instance=axios.create({
        baseURL: "http://api.jirengu.com",
        timeout: 5000
    })
    instance(config).then(res=>{
        success(res)
    }).catch(err=>{
        failure(err)
    })
}
~~~

组件使用

~~~js
import {request} from './network/request'
request({
  url:"/fm/v2/getChannels.php"
},res=>{
  console.log(res)
},err=>{
  console.log(err)
})
~~~

<hr/>

axios是基于promise，可以直接这样写

~~~js
import axios from 'axios';
export function request(config){
    const instance=axios.create({
        baseURL: "http://api.jirengu.com",
        timeout: 5000
    })
    return instance(config)
}
~~~

使用时

~~~js
import {request} from './network/request'
request({
  url:"/fm/v2/getChannels.php"
}).then(res=>{
  console.log(res)
}).catch(err=>{
  console.log(err)
})
~~~

## 五、拦截器的使用

axios提供了拦截器，用于我们在发送每次请求或者得到响应后，进行对应的处理

### 1.请求拦截

~~~js
import axios from 'axios';
export function request(config){
    const instance=axios.create({
        baseURL: "http://api.jirengu.com",
        timeout: 5000
    })
	//请求拦截
    instance.interceptors.request.use(res=>{
        console.log(res)
        //此处拦截后，必须还要再将结果返回
        return res
    },err=>{
        console.log(err)
    })

    return instance(config)
}
~~~

### 2.响应拦截

~~~js
import axios from 'axios';
export function request(config){
    const instance=axios.create({
        baseURL: "http://api.jirengu.com",
        timeout: 5000
    })

    instance.interceptors.response.use(res=>{
        console.log(res)
        //如果想要返回结果，必须要return res
        return res
    },err=>{
        console.log(err)
    })

    return instance(config)
}
~~~





































