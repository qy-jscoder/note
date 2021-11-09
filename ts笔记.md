## 一、ts的概念

ts是js的超集

它强调了 TypeScript 的两个最重要的特性——类型系统、适用于任何规模。

「类型」是其最核心的特性。

ts是静态类型（在编译时才会类型检查），而js是动态类型（在运行时才会类型检查）

ts和js一样都是弱语言，即允许隐式类型转换

TypeScript 可以和 JavaScript 共存，这意味着 JavaScript 项目能够渐进式的迁移到 TypeScript。

TypeScript 可以编译为 JavaScript，然后运行在浏览器、Node.js 等任何能运行 JavaScript 的环境中。

 TypeScript 编译的时候即使报错了，还是会生成编译结果，我们仍然可以使用这个编译之后的文件。

如果要在报错的时候终止 js 文件的生成，可以在 `tsconfig.json` 中配置 `noEmitOnError` 即可。关于 `tsconfig.json`，请参阅[官方手册](http://www.typescriptlang.org/docs/handbook/tsconfig-json.html)（[中文版](https://zhongsp.gitbooks.io/typescript-handbook/content/doc/handbook/tsconfig.json.html)）。

## 二、简单使用

在 TypeScript 中，我们使用 `:` 指定变量的类型，`:` 的前后有没有空格都可以。

~~~typescript
function sayHello(person: string) {
    return 'Hello, ' + person;
}
let user = 'Tom';
console.log(sayHello(user));
~~~

执行以下命令

~~~node
tsc xxx.ts
~~~

生成一个编译好的js文件

 也可以全局安装

~~~
npm install -g typescript
~~~

执行以下命令，不会生成js文件，直接在控制台输出结果

~~~
ts-node xxx.ts
~~~

## 三、原始数据类型

以下为使用时的注意点

### 1.number

如果值为es6 中的二进制和八进制表示法，那么它们会被编译为十进制数字。

### 2.空值

JavaScript 没有空值（Void）的概念，在 TypeScript 中，可以用 `void` 表示没有任何返回值的函数：

~~~typescript
function alertName(): void {
    alert('My name is Tom');
}
~~~

用void表示的变量，只能被赋值为 `undefined` 和 `null`（只在 --strictNullChecks 未指定时）

### 3.Null 和 Undefined

在 TypeScript 中，可以使用 `null` 和 `undefined` 来定义这两个原始数据类型

~~~typescript
let u: undefined = undefined;
let n: null = null;
~~~

与 `void` 的区别是，`undefined` 和 `null` 是所有类型的子类型。也就是说 `undefined` 类型的变量，可以赋值给 `number` 类型的变量：

~~~ts
let num: number = undefined;
// 这样也不会报错
let u: undefined;
let num: number = u;
~~~

注意：此处如何要将undefined赋值为number类型的变量，需要再

















