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

## 三、类型

### 1.number

如果值为es6 中的二进制和八进制表示法，那么它们会被编译为十进制数字。

### 2.空值

JavaScript 没有空值（Void）的概念，在 TypeScript 中，可以用 `void` 表示没有任何返回值的函数：

~~~typescript
function alertName(): void {
    alert('My name is Tom');
}
~~~

用void表示的变量，只能被赋值为 `undefined` 和 `null`（只在tsconfig.json中的 --strictNullChecks 未指定时）

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

注意：此处如果要将undefined赋值为number类型的变量，需要在tsconfig.json文件中设置strict为false

### 4.数组

有两种方式可以定义数组。 第一种，可以在元素类型后面接上 `[]`，表示由此类型元素组成的一个数组：

~~~ts
let list: number[] = [1, 2, 3];
~~~

第二种方式是使用数组泛型，`Array<元素类型>`：

```ts
let list: Array<number> = [1, 2, 3];
```

### 5.元组Tuple

元组类型允许表示一个已知元素数量和类型的数组，各元素的类型不必相同。 比如，你可以定义一对值分别为 `string`和`number`类型的元组。

~~~ts
let x: [string, number];
// Initialize it
x = ['hello', 10]; // OK
// Initialize it incorrectly
x = [10, 'hello']; // Error
~~~

当访问超出元组长度的元素时，它的类型会被限制为元组中每个类型的联合类型

### 6.枚举类型

使用枚举类型可以为一组数值赋予友好的名字。

默认情况下，从`0`开始为元素编号。 你也可以手动的指定成员的数值。 例如：

~~~ts
enum Color {Red = 1, Green, Blue}
let c: Color = Color.Green;
console.log(c);//2
~~~

或者，全部都采用手动赋值：

~~~ts
enum Color {Red = 1, Green = 2, Blue = 4}
let c: Color = Color.Green;//2
~~~

枚举类型提供的一个便利是你可以由枚举的值得到它的名字。 例如，我们知道数值为2，但是不确定它映射到Color里的哪个名字，我们可以查找相应的名字：

~~~ts
enum Color {Red = 1, Green, Blue}
let colorName: string = Color[2];

console.log(colorName);  // 显示'Green'因为上面代码里它的值是2
~~~

### 7.任意类型

在赋值过程中改变类型是不被允许的

但是如果是any类型，则允许被赋值为任意类型

~~~ts
let myFavoriteNumber: any = 'seven';
myFavoriteNumber = 7;
console.log(myFavoriteNumber);//7

myFavoriteNumber='hhh'
console.log(myFavoriteNumber);//'hhh'

myFavoriteNumber=false
console.log(myFavoriteNumber);//false

myFavoriteNumber=[1,2,5]
console.log(myFavoriteNumber);//[1,2,5]
~~~

在任意值上访问任何属性和方法都是允许的：

~~~ts
let anyThing: any = 'hello';
console.log(anyThing.myName);
console.log(anyThing.myName.firstName);


let anyThing: any = 'hello';
console.log(anyThing.myName);
console.log(anyThing.myName.firstName);
~~~

注意：ts是强类型的，在编译时需要类型检查，any的作用是在有些对象还不明确推测出类型时，编译时跳过类型检查

### 8.未声明类型的变量

变量如果在声明的时候，未指定其类型，那么它会被识别为任意值类型

与js定义变量基本一致

### 9.联合类型

联合类型（Union Types）表示取值可以为多种类型中的一种。

联合类型使用 `|` 分隔每个类型。

例子：

~~~ts
let myFavoriteNumber: string | number;
myFavoriteNumber = 'seven';
myFavoriteNumber = 7;
~~~

~~~ts
let myFavoriteNumber: string | number;
myFavoriteNumber = true;

// index.ts(2,1): error TS2322: Type 'boolean' is not assignable to type 'string | number'.
//   Type 'boolean' is not assignable to type 'number'.
~~~

#### （1）访问联合类型的属性或方法

当 TypeScript 不确定一个联合类型的变量到底是哪个类型的时候，我们**只能访问此联合类型的所有类型里共有的属性或方法**：

~~~ts
function getLength(something: string | number): number {
    return something.length;
}

// index.ts(2,22): error TS2339: Property 'length' does not exist on type 'string | number'.
//   Property 'length' does not exist on type 'number'.
~~~

上例中，`length` 不是 `string` 和 `number` 的共有属性，所以会报错。

但是访问 `string` 和 `number` 的共有属性是没问题的：

~~~ts
function getString(something: string | number): string {
    return something.toString();
}
~~~

### 10.接口类型

在 TypeScript 中，我们使用接口（Interfaces）来定义对象的类型。

在面向对象语言中，接口（Interfaces）是一个很重要的概念，它是对行为的抽象，而具体如何行动需要由类（classes）去实现（implement）。

TypeScript 中的接口是一个非常灵活的概念，除了可用于[对类的一部分行为进行抽象](https://ts.xcatliu.com/advanced/class-and-interfaces.html#类实现接口)以外，也常用于对「对象的形状（Shape）」进行描述。

#### （1）简单例子

定义了一个接口 `Person`，接着定义了一个变量 `tom`，它的类型是 `Person`。这样，我们就约束了 `tom` 的形状必须和接口 `Person` 一致。

~~~ts
interface Person {
    name: string;
    age: number;
}

let tom: Person = {
    name: 'Tom',
    age: 25
};
~~~

接口一般首字母大写。有的编程语言中会建议接口的名称加上 `I` 前缀

定义的变量比接口少了一些属性，或者多一些属性都是不允许的

#### （2）可选属性

有时我们希望不要完全匹配一个形状，那么可以用可选属性：

~~~ts
interface Person {
    name: string;
    age?: number;
}

let tom: Person = {
    name: 'Tom'
};
~~~

这时仍然不允许在变量中添加未定义的属性

#### （3）任意属性

有时候我们希望一个接口允许有任意的属性，可以使用如下方式：

使用 `[propName: string]` 定义了任意属性取 `string` 类型的值。

需要注意的是，**一旦定义了任意属性，那么确定属性和可选属性的类型都必须是它的类型的子集**：

~~~ts
interface Person {
    name: string;
    age?: number;
    [propName: string]: any;
}

let tom: Person = {
    name: 'Tom',
    gender: 'male'
};
~~~

一个接口中只能定义一个任意属性。如果接口中有多个类型的属性，则可以在任意属性中使用联合类型：

~~~ts
interface Person {
    name: string;
    age?: number;
    [propName: string]: string | number;
}

let tom: Person = {
    name: 'Tom',
    age: 25,
    gender: 'male'
};
~~~

#### （4）只读属性

有时候我们希望对象中的一些字段只能在创建的时候被赋值，那么可以用 `readonly` 定义只读属性：

~~~ts
interface Person {
    readonly id: number;
    name: string;
    age?: number;
    [propName: string]: any;
}

let tom: Person = {
    id: 89757,
    name: 'Tom',
    gender: 'male'
};

tom.id = 9527;

// index.ts(14,5): error TS2540: Cannot assign to 'id' because it is a constant or a read-only property.
~~~

**注意，只读的约束存在于第一次给对象赋值的时候，而不是第一次给只读属性赋值的时候**：

```ts
interface Person {
    readonly id: number;
    name: string;
    age?: number;
    [propName: string]: any;
}

let tom: Person = {
    name: 'Tom',
    gender: 'male'
};

tom.id = 89757;

// index.ts(8,5): error TS2322: Type '{ name: string; gender: string; }' is not assignable to type 'Person'.
//   Property 'id' is missing in type '{ name: string; gender: string; }'.
// index.ts(13,5): error TS2540: Cannot assign to 'id' because it is a constant or a read-only property.
```

上例中，报错信息有两处，第一处是在对 `tom` 进行赋值的时候，没有给 `id` 赋值。

第二处是在给 `tom.id` 赋值的时候，由于它是只读属性，所以报错了。

### 11.数组类型

#### （1）常见定义

在 TypeScript 中，数组类型有多种定义方式，比较灵活。

最简单的方法是使用「类型 + 方括号」来表示数组：

~~~~ts
let arr: number[] = [1, 1, 2, 3, 5];
~~~~

#### （2）数组泛型

我们也可以使用数组泛型（Array Generic） `Array<elemType>` 来表示数组：

~~~ts
let arr: Array<number> = [1, 1, 2, 3, 5];
~~~

#### （3）接口定义

~~~ts
interface NumberArray {
    [index: number]: number;
}
let fibonacci: NumberArray = [1, 1, 2, 3, 5];
~~~

`NumberArray` 表示：只要索引的类型是数字时，那么值的类型必须是数字。

虽然接口也可以用来描述数组，但是我们一般不会这么做，因为这种方式比前两种方式复杂多了。

#### （4）类数组

类数组（Array-like Object）不是数组类型，比如 `arguments`：

不能用普通的数组的方式来描述，而应该用接口：

~~~ts
function sum() {
    let args: {
        [index: number]: number;
        length: number;
        callee: Function;
    } = arguments;
}
~~~

在这个例子中，我们除了约束当索引的类型是数字时，值的类型必须是数字之外，也约束了它还有 `length` 和 `callee` 两个属性。

事实上常用的类数组都有自己的接口定义，如 `IArguments`, `NodeList`, `HTMLCollection` 等：

~~~ts
function sum() {
    let args: IArguments = arguments;
}
~~~

其中 `IArguments` 是 TypeScript 中定义好了的类型，它实际上就是：

~~~ts
interface IArguments {
    [index: number]: any;
    length: number;
    callee: Function;
}
~~~

### 12.函数类型

#### （1）函数声明

一个函数有输入和输出，要在 TypeScript 中对其进行约束，需要把输入和输出都考虑到，其中函数声明的类型定义较简单：

~~~ts
function sum(x: number, y: number): number {
    return x + y;
}
~~~

注意，**输入多余的（或者少于要求的）参数，是不被允许的**

#### （2）函数表达式

~~~ts
let mySum = function (x: number, y: number): number {
    return x + y;
};
~~~

这是可以通过编译的，不过事实上，上面的代码只对等号右侧的匿名函数进行了类型定义，而等号左边的 `mySum`，是通过赋值操作进行类型推论而推断出来的。如果需要我们手动给 `mySum` 添加类型，则应该是这样：

~~~ts
let mySum: (x: number, y: number) => number = function (x: number, y: number): number {
    return x + y;
};
~~~

注意不要混淆了 TypeScript 中的 `=>` 和 ES6 中的 `=>`。

在 TypeScript 的类型定义中，`=>` 用来表示函数的定义，左边是输入类型，需要用括号括起来，右边是输出类型。

在 ES6 中，`=>` 叫做箭头函数，应用十分广泛

#### （3）用接口定义函数的形状

~~~ts
interface SearchFunc {
    (source: string, subString: string): boolean;
}
let mySearch: SearchFunc;
mySearch = function(source: string, subString: string) {
    return source.search(subString) !== -1;
}
~~~

#### （4）可选参数

~~~ts
function buildName(firstName: string, lastName?: string) {
    if (lastName) {
        return firstName + ' ' + lastName;
    } else {
        return firstName;
    }
}
let tomcat = buildName('Tom', 'Cat');
let tom = buildName('Tom');
~~~

可选参数必须接在必需参数后面。换句话说，**可选参数后面不允许再出现必需参数了**

#### （5）参数默认值

**TypeScript 会将添加了默认值的参数识别为可选参数**

此时就不受「可选参数必须接在必需参数后面」的限制了：

~~~ts
function buildName(firstName: string = 'Tom', lastName: string) {
    return firstName + ' ' + lastName;
}
let tomcat = buildName('Tom', 'Cat');
let cat = buildName(undefined, 'Cat');
~~~

但是此时就必须实参写全

#### （6）剩余参数

ES6 中，可以使用 `...rest` 的方式获取函数中的剩余参数（rest 参数）：

我们可以用数组的类型来定义剩余参数：

~~~ts
function push(array: any[], ...items: any[]) {
    items.forEach(function(item) {
        array.push(item);
    });
}

let a = [];
push(a, 1, 2, 3);
~~~

注意，rest 参数只能是最后一个参数

#### （7）重载

重载允许一个函数接受不同数量或类型的参数时，作出不同的处理。

通常和联合类型一起使用

~~~ts
function reverse(x: number): number;
function reverse(x: string): string;
function reverse(x: number | string): number | string | void {
    if (typeof x === 'number') {
        return Number(x.toString().split('').reverse().join(''));
    } else if (typeof x === 'string') {
        return x.split('').reverse().join('');
    }
}
~~~

注意，TypeScript 会优先从最前面的函数定义开始匹配，所以多个函数定义如果有包含关系，需要优先把精确的定义写在前面。

该特性不常使用

## 四、类型推断和类型断言

### 1.类型推断

如果没有明确的指定类型，那么 TypeScript 会依照类型推论（Type Inference）的规则推断出一个类型。

**如果定义的时候没有赋值，不管之后有没有赋值，都会被推断成 `any` 类型而完全不被类型检查**：

~~~~ts
let myFavoriteNumber;
myFavoriteNumber = 'seven';
myFavoriteNumber = 7;
~~~~

### 2.类型断言

用来手动指定一个值的类型。

#### （1）语法

~~~ts
值 as 类型
~~~

或

~~~ts
<类型>值
~~~

在 tsx 语法（React 的 jsx 语法的 ts 版）中必须使用前者，即 `值 as 类型`。

第二种语法在ts中不仅表示类型断言外，还可能表示一个泛型

故建议大家在使用类型断言时，统一使用 `值 as 类型` 这样的语法

#### （2）将一个联合类型断言为其中一个类型

~~~ts
interface Cat {
    name: string;
    run(): void;
}
interface Fish {
    name: string;
    swim(): void;
}

function isFish(animal: Cat | Fish) {
    if (typeof (animal as Fish).swim === 'function') {
        return true;
    }
    return false;
}
~~~

使用该方法会避免编译报错，但是运行时如果没有对应的属性依然会报错

使用类型断言时一定要格外小心，尽量避免断言后调用方法或引用深层属性，以减少不必要的运行时错误。

#### （3）父类可以被断言为子类

~~~ts
class ApiError extends Error {
    code: number = 0;
}
class HttpError extends Error {
    statusCode: number = 200;
}

function isApiError(error: Error) {
    if (typeof (error as ApiError).code === 'number') {
        return true;
    }
    return false;
}
~~~

#### （4）将任何一个类型断言为 any

在 `any` 类型的变量上，访问任何属性都是允许的。

~~~
(window as any).foo = 1;
~~~

否则会报错

~~~ts
window.foo = 1;

// index.ts:1:8 - error TS2339: Property 'foo' does not exist on type 'Window & typeof globalThis'.
~~~

需要注意的是，将一个变量断言为 `any` 可以说是解决 TypeScript 中类型问题的最后一个手段。

**它极有可能掩盖了真正的类型错误，所以如果不是非常确定，就不要使用 `as any`。**

#### （5）将 `any` 断言为一个具体的类型

通过类型断言及时的把 `any` 断言为精确的类型

~~~ts
function getCacheData(key: string): any {
    return (window as any).cache[key];
}

interface Cat {
    name: string;
    run(): void;
}

const tom = getCacheData('tom') as Cat;
tom.run();
~~~

#### （6）类型断言的限制

TypeScript 是结构类型系统，类型之间的对比只会比较它们最终的结构，而会忽略它们定义时的关系。

不管定义时的关系，只看它们的结构关系

~~~ts
interface Animal {
    name: string;
}
interface Cat {
    name: string;
    run(): void;
}
~~~

相当于

~~~ts
interface Animal {
    name: string;
}
interface Cat extends Animal {
    run(): void;
}
~~~

所以，以下可以实现，不会报错

~~~ts
interface Animal {
    name: string;
}
interface Cat {
    name: string;
    run(): void;
}

let tom: Cat = {
    name: 'Tom',
    run: () => { console.log('run') }
};
let animal: Animal = tom;
~~~

就像面向对象编程中我们可以将子类的实例赋值给类型为父类的变量

但是，不能将父类的实例赋值给类型为子类的变量。

综上所述：

- 联合类型可以被断言为其中一个类型
- 父类可以被断言为子类（子类可以被断言为父类）
- 任何类型都可以被断言为 any
- any 可以被断言为任何类型
- 要使得 `A` 能够被断言为 `B`，只需要 `A` 兼容 `B` 或 `B` 兼容 `A` 即可

#### （7）双重断言

根据

- 任何类型都可以被断言为 any
- any 可以被断言为任何类型

可以使用 as any as xxx来断言

~~~ts
interface Cat {
    run(): void;
}
interface Fish {
    swim(): void;
}

function testCat(cat: Cat) {
    return (cat as any as Fish);
}
~~~

如果使用了这种双重断言，它很可能会导致运行时错误。

**除非迫不得已，千万别用双重断言。**

#### （8）类型断言和类型转换

类型断言只会影响 TypeScript 编译时的类型，类型断言语句在编译结果中会被删除

~~~ts
function toBoolean(something: any): boolean {
    return something as boolean;
}
toBoolean(1);
// 返回值为 1
~~~

相当于

~~~ts
function toBoolean(something) {
    return something;
}
toBoolean(1);
// 返回值为 1
~~~

若要进行类型转换，需要直接调用类型转换的方法

#### （9）类型断言和类型声明

~~~ts
function getCacheData(key: string): any {
    return (window as any).cache[key];
}

interface Cat {
    name: string;
    run(): void;
}

const tom: Cat = getCacheData('tom');
tom.run();
~~~

其中的

~~~ts
const tom = getCacheData('tom') as Cat;
~~~

等价于

~~~ts
const tom: Cat = getCacheData('tom');
~~~

深入的讲，它们的核心区别就在于：

- `animal` 断言为 `Cat`，只需要满足 `Animal` 兼容 `Cat` 或 `Cat` 兼容 `Animal` 即可
- `animal` 赋值给 `tom`，需要满足 `Cat` 兼容 `Animal` 才行

优先使用类型声明，这也比类型断言的 `as` 语法更加优雅



## 五、泛型

泛型（Generics）是指在定义函数、接口或类的时候，不预先指定具体的类型，而在使用的时候再指定类型的一种特性。

### 1.简单例子































