### PS：以下第三方中间件或者npm包相关内容需要根据版本而改变



## 一、中间件

从请求到响应的过程中的处理函数

```js
//定义一个简单调度中间件
const express=require('express')

const app=express()

const mw=(req,res,next)=>{
    console.log('简单中间件')
    next()//next必加，否则无法流转到后面
}
//注册为全局有效的中间件
app.use(mw)

app.listen(8080,()=>{
    console.log('启动服务')
}
```

### 1.作用

多个中间件之间共享同一份req和res。基于此特性，可以在上游中间件添加自定义的属性和方法，供下游使用

### 2.局部生效的中间件

```js
//定义一个简单调度中间件
const express=require('express')

const app=express()

const mw=(req,res,next)=>{
    console.log('简单中间件')
    next()//next必加，否则无法流转到后面
}

app.get('/user',mw,(req,res)=>{//该中间件只在当前路由生效
    console.log('局部')
})

app.listen(8080,()=>{
    console.log('启动服务')
}
```

### 3.多个中间件

```js
const mw1=(req,res,next)=>{
    console.log('简单中间件')
    next()//next必加，否则无法流转到后面
}
const mw2=(req,res,next)=>{
    console.log('简单中间件')
    next()//next必加，否则无法流转到后面
}
app.get('/user',mw1,mw2,(req,res)=>{//该中间件只在当前路由生效
    console.log('局部')
})
app.get('/user',[mw1,mw2],(req,res)=>{//该中间件只在当前路由生效
    console.log('局部')
})
```

### 4.错误级别中间件

```js
app.get('/user',req,res)=>{//该中间件只在当前路由生效
    throw new Error('服务器内部发送错误!')
})

app.use((err,req,res,next)=>{
    console.log(error.message)
    next()//next必加，否则无法流转到后面
})
```

### 5.注意事项

（1）一定要在路由之前注册中间件

（2）next()必加

（3）在调用next()后一行，不要再写代码，避免逻辑混乱

（4）错误级别的中间件必须在所有中间件之后

### 6.中间件类型

（1）应用级别的中间件：app.use、app.（请求类型）等

（2）路由级别的中间件：router.use

（3）错误级别的中间件：捕获项目异常（格式：必须有4个形参，err、req、res、next）

### 7.内置中间件

（1）express.static快速托管静态资源

（2）express.json解析json数据（请求体数据需要通过该中间件解析，否则为undefined）

（3）express.urlencodded解析URL-encoded格式的请求体数据

### 8.自定义中间件

例子：解析查询字符串数据

```js
const qs=require('querystring')//解析查询字符串

app.use((req,res,next)=>{
    let str=''//数据过多，客户端会切割数据，分批发送
    req.on('data',(chunk)=>{//监听data事件，来获取客户端发送到服务器的数据
        str+=chunk
    })
    
    req.on('end',()=>{//监听end事件，请求体数据接收完毕后会自动触发
        console.log(str)//此时应当是完整的请求体数据
        
       	const body=qs.parse(str)
        req.body=body
        console.log(body)
        next()
    })
})
```

## 二、创建API

### 1.例子

```js
//创建路由模块
const express=require('express')

const router=express.Router()

//挂载路由
router.get('/get',(req,res)=>{
    const query=req.query//默认为空
    res.send({
        status:0,
        msg:'Get请求成功',
        data:query
    })
})

module.exports=router

//入口文件
const express=require('express')

const app=express()
//解析body数据
app.use(express.urlencodded({xxx:false}))
//引入路由
const apiRouter=require('./xxx.js')
//路由模块注册到app服务器中
app.use('/api',apiRouter)
app.listen(80,()=>{
    console.log('启动服务')
})
```

### 2.解决跨域问题

跨域问题一般由服务器端解决

```js
//安装cors中间件
const cors=require('cors')
app.use(cors（）)
//cors响应头
res.setHeader('Access-Control-Allow-Origin','*')//*表示通配符，允许来自任何域的请求
```

### 3.预检请求

（1）定义

只要符合以下任何一个条件的请求都需要进行预检请求

- 请求方式为GET、POST、HEAD之外的请求类型
- 请求头中包含自定义头部字段
- 向服务器发送application/json格式的请求

在客户端和服务器正式通信之前，浏览器会先发送OPTION请求进行预检，以获知服务器是否允许该实际请求，所以这次的OPTION请求称为“预检请求”。成功响应预检请求后才会发送真正的请求，并携带真实的数据

（2）特点

简单请求：客户端与服务器之间只会发生一次请求

预检请求：客户端与服务器之间会发生两次请求，OPTION预检请求成功后，才会发起真正的请求

### 4.JSONP接口

仅支持get请求，且不安全

```js
app.get('/api/jsonp',(req,res)=>{
    //获取回调函数的名字
    const funcName=req.query.callback
    //得到要通过JSONP发送给客户端的数据
    const data={name:'a',age:12}
    //根据数据和函数名拼接成一个函数
    const scripStr=`${funcName}(${JOSN.stringify(data)})`
    //将上一步的字符串响应给客户端的script标签进行解析执行
    res.send(scripStr)
})
```

## 三、MySQL数据库

安装mysql对应的npm包

```js
//安装mysql包：npm i mysql
//导入mysql模块
const mysql=requuire('mysql')
//建立与MySQL数据库的连接
const db=mysql.createPool({
    host:'127.0.0.1',//数据库的IP地址
    user:'root',//登录数据库的账号
    password:'xxxxxx',//登录数据库的密码
    database:'xxx'//要操作的数据库
})

//测试mysql模块是否正常工作
db.query('select 1',(err,res)=>{
    if(err)return //如果报错，则终止
    console.log('执行')
})

//查询数据库中users表所有的数据
const sqlStr='select * from users'
db.query(sqlStr,(err,res)=>{
    if(err)return //如果报错，则终止
    console.log(res)
})

//插入新增数据
const obj={userName:'121',password:123}
//如果新增数据的属性和字段都能一一对应，那么可以使用该语句：'INSERT INTO users SET ?'
//并且[obj.userName,obj.password]可替代为obj对象
//待执行的sql语句，英文?表示占位符
const sqlStr='insert into users (userName,password) values (?,?)'
//执行语句
db.query(sqlStr,[obj.userName,obj.password],(err,res)=>{
    if(err)return //如果报错，则终止
    if(results.affectedRows===1){//可以通过affectedRows属性来判断是否插入数据成功
        console.log('插入成功')
    }
})
```

![image-20230129173456347](D:\VS-Code\node.assets\image-20230129173456347.png)

<h4 style="color:red">执行update操作时，返回的res是一个对象</h4>

![image-20230129174253334](D:\VS-Code\node.assets\image-20230129174253334.png)

![image-20230129174704644](D:\VS-Code\node.assets\image-20230129174704644.png)

![image-20230129174956208](D:\VS-Code\node.assets\image-20230129174956208.png)

## 四、前后端身份认证

### 1. Web开发模式

目前主流的开发模式有两种：

（1）基于服务端渲染的传统Web开发模式

（2）基于前后端分离的新型Web开发模式

![image-20230129180048203](D:\VS-Code\node.assets\image-20230129180048203.png)

![image-20230129183458703](D:\VS-Code\node.assets\image-20230129183458703.png)

![image-20230129183711522](D:\VS-Code\node.assets\image-20230129183711522.png)

![image-20230129184012063](D:\VS-Code\node.assets\image-20230129184012063.png)

![image-20230129184338299](D:\VS-Code\node.assets\image-20230129184338299.png)

### 2.身份认证

![image-20230129184756329](D:\VS-Code\node.assets\image-20230129184756329.png)

![image-20230129185132527](D:\VS-Code\node.assets\image-20230129185132527.png)



例子：a会员购买商品后，下一个b会员购买商品结算时，不会显示a会员的信息

![image-20230129185753480](D:\VS-Code\node.assets\image-20230129185753480.png)

![image-20230129190557592](D:\VS-Code\node.assets\image-20230129190557592.png)

![image-20230129191036088](D:\VS-Code\node.assets\image-20230129191036088.png)

![image-20230129191350865](D:\VS-Code\node.assets\image-20230129191350865.png)

#### （1）session认证

![image-20230129191633996](D:\VS-Code\node.assets\image-20230129191633996.png)

![image-20230129192152672](D:\VS-Code\node.assets\image-20230129192152672.png)





### **node中使用session认证**

![image-20230129192516925](D:\VS-Code\node.assets\image-20230129192516925.png)

![image-20230129193318467](D:\VS-Code\node.assets\image-20230129193318467.png)

![image-20230129193616761](D:\VS-Code\node.assets\image-20230129193616761.png)

```js
req.sesseion.destroy()//只会清空当前登录状态下的session信息
```



![image-20230129194822652](D:\VS-Code\node.assets\image-20230129194822652.png)

#### （2）JWT 认证

JWT（英文全称：JSON Web Token）是目前最流行的跨域认证解决方案

![image-20230130150954858](D:\VS-Code\node.assets\image-20230130150954858.png)

![image-20230130151416810](D:\VS-Code\node.assets\image-20230130151416810.png)

![image-20230130152502312](D:\VS-Code\node.assets\image-20230130152502312.png)

![image-20230130152758736](D:\VS-Code\node.assets\image-20230130152758736.png)

![image-20230130153031351](D:\VS-Code\node.assets\image-20230130153031351.png)

<h4 style="color:red">Authorization： Bearer < token >固定写法</h4>

#### JWT在项目中的运用

![image-20230130153431780](D:\VS-Code\node.assets\image-20230130153431780.png)

![image-20230130153809814](D:\VS-Code\node.assets\image-20230130153809814.png)

secret密钥是自定义的字符串

![image-20230130154321379](D:\VS-Code\node.assets\image-20230130154321379.png)

配置对象可以配置当前token的有效期

由于要给客户端，客户端并不安全，所以生成的token字符串中要剔除密码和头像

![image-20230130154908311](D:\VS-Code\node.assets\image-20230130154908311.png)

![image-20230130161022885](D:\VS-Code\node.assets\image-20230130161022885.png)