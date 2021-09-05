## 一、ref和reactive

### 1.基本使用

ref函数将基本类型数据转为一个refimpl对象，改变值时要通过xxx.value来改变

reactive将引用类型数据转为一个proxy对象，获取对象时不需要value，改变值时直接用属性获取值，不需要value

数组同理，使用reactive处理，改变值获取值时都可以直接使用索引修改

reactive定义的响应式数据是深层次的，内部是基于proxy实现的，通过代理对象操作源对象内部数据

reactive定义的对象或数组，可以直接修改属性或者通过索引来修改值

### 2.对比

#### （1）定义

ref定义基本类型数据，reactive定义对象（数组）类型数据（ref也可以定义对象类型数据，内部会将其转为代理对象）

#### （2）原理

ref基于vue2的响应式原理来实现响应式（即：Object.defineProperty（）的get与set）

reactive通过proxy来实现响应式，并通过Reflect操作源对象内部的数据

#### （3）使用

ref定义的数据，要通过.value;在模板中使用不需要.value

reactive定义的数据，读取与修改时都不需要.value

#### 3.vue3响应式原理

#### （1）Proxy

window中内置了proxy函数，可以通过该函数来构造代理对象，通过代理对象来映射要操作的对象，读写数据时仍然是通过get，set来实现的，此外添加了deleteProperty来删除属性。

~~~js
//第二个参数可以为空，若为空也可以操作对象，但不是响应式的
const p=new Proxy(obj,{
	get(target,propName){
		return target[propName]
	},
	set(target,propName,value){
		target[propName]=value
	},
    deleteProperty(target,propName){
        return delete target[propName]
    }
})
~~~

#### （2）Reflect

通过Reflect可以操作对象属性

~~~js
Reflect.get(obj,'propName')
Reflect.set(obj,'propName')
Reflect.deleteProperty(obj,'propName')

//所以应用到vue3响应式原理中
const p=new Proxy(obj,{
	get(target,propName){
		return Reflect.get(target,propName)
	},
	set(target,propName,value){
		return Reflect.set(target,propName)
	},
    deleteProperty(target,propName){
        return Reflect.deleteProperty(target,propName)
    }
})
~~~

### 二、setup

#### 1.setup执行的时机

在beforeCreate之前执行一次，this是undefined

#### 2.参数

props：值为对象，父组件传值进来，子组件声明接收的属性

context：

- attrs：值为对象，父组件传来，但是没有在props中配置的属性。相当于this.$attrs
- slots：收到的插槽内容，相当于this.$slots
- emit：发送事件，相当于this.$emit

### 三、计算属性computed

手动引入

~~~js
import {computed} from 'vue'
~~~

使用

~~~js
setup(){
	const xx=computed(()=>{
		return xxx
	})
}
~~~

计算属性是可以修改的，若要修改，应当通过get，set来修改

### 四、监听器watch

手动引入

~~~js
import {watch} from 'vue'
~~~

使用:

~~~js
setup(){
    //通用情况
    watch(数据,(newvalue,oldvalue)=>{
        
    },{immediate:true})
 	//情况1：监视的ref定义的一个数据
    watch(一个数据,(newcalue,oldvalue)=>{
        
    })
    //情况2：监视传入的ref定义的多个数据，返回的是一个数组
    watch([数据1,数据2],(newvalue,oldvalue)=>{
        
    })
    //情况3：监视传入的reactive定义的数据
    //注意：1.强制开启深度监听，即deep:true，无法更改
    //2.无法获取oldvalue
    watch(数据,(newvalue,oldvalue)=>{
        
    })
    //情况4：监视reactive定义的一个响应式对象的一个属性
    watch(()=>对象.属性,(newvalue,oldvalue)=>{
        
    })
    //情况5：监视reactive定义的一个响应式数据深层次的属性的属性
    /*例如：const obj={
    			action:{
    				eat:{
    					food:{
    					
    					}
    				}
    			}
			}*/
    /*若要监视obj.action中的eat，必须要手动开启deep:true，与直接监视整个对象不同，需要		加以区分*/
	}
	//情况6：监视ref定义的对象，则必须手动开启deep为true
}
~~~

