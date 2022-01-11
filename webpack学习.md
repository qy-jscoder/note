## 一、概念

*webpack* 是一个现代 JavaScript 应用程序的*静态模块打包器(module bundler)*。当 webpack 处理应用程序时，它会递归地构建一个*依赖关系图(dependency graph)*，其中包含应用程序需要的每个模块，然后将所有这些模块打包成一个或多个 *bundle*。

webpack有四个**核心概念**：

- 入口(entry)
- 输出(output)
- loader
- 插件(plugins)

### 二、webpack学习前提知识

### 1.path.join()

path.join([...paths])

`path.join()` 方法使用特定于平台的分隔符作为定界符将所有给定的 `path` 片段连接在一起，然后规范化生成的路径。

零长度的 `path` 片段被忽略。 如果连接的路径字符串是零长度字符串，则将返回 `'.'`，表示当前工作目录。

~~~js
path.join('/foo', 'bar', 'baz/asdf', 'quux', '..');
// 返回: '/foo/bar/baz/asdf'

path.join('foo', {}, 'bar');
// 抛出 'TypeError: Path must be a string. Received {}'
~~~

### 2.path.resolve()

path.resolve([...paths])

`...paths` 路径或路径片段的序列

`path.resolve()` 方法将路径或路径片段的序列解析为绝对路径。

给定的路径序列从右到左处理，每个后续的 `path` 会被追加到前面，直到构建绝对路径。 例如，给定路径片段的序列：`/foo`、`/bar`、`baz`，调用 `path.resolve('/foo', '/bar', 'baz')` 将返回 `/bar/baz`，因为 `'baz'` 不是绝对路径，而 `'/bar' + '/' + 'baz'` 是。

如果在处理完所有给定的 `path` 片段之后，还没有生成绝对路径，则使用当前工作目录。

生成的路径被规范化，并删除尾部斜杠（除非路径解析为根目录）。

零长度的 `path` 片段被忽略。

如果没有传入 `path` 片段，则 `path.resolve()` 将返回当前工作目录的绝对路径。

~~~js
path.resolve('/foo/bar', './baz');
// 返回: '/foo/bar/baz'

path.resolve('/foo/bar', '/tmp/file/');
// 返回: '/tmp/file'

path.resolve('wwwroot', 'static_files/png/', '../gif/image.gif');
// 如果当前工作目录是 /home/myself/node，
// 则返回 '/home/myself/node/wwwroot/static_files/gif/image.gif'
path.resolve(__dirname, 'sdad')
// 返回: '当前文件所在目录/sdad'
~~~

## 3.style-loader和css-loader

webpack是用JS写的，运行在node环境，所以默认webpack打包的时候只会处理JS之间的依赖关系！！！

因为像 .css 这样的文件不是一个 JavaScript 模块，你需要配置 webpack 使用 css-loader 或者 style-loader 去合理地处理它们。

如果在JS中导入了css，那么就需要使用 css-loader 来识别这个模块，通过特定的语法规则进行转换内容最后导出

css-loader会处理 `import` / `require`（） `@import` / `url` 引入的内容。

例如：

~~~css
.bg {
  background: #000;
}
~~~

~~~js
const style = require('./base.css')
console.log(style, 'css')
~~~

css-loader处理之后导出的是

![img](C:\Users\xiaoxi\AppData\Local\Temp\企业微信截图_16415340014648.png)

但是这并不是我们想要的，因为是个数组，页面是无法直接使用，这时我们需要用到另外一个style-loader来处理。

style-loader 是通过一个JS脚本创建一个style标签，里面包含一些样式。style-loader是不能单独使用的，应为它并不负责解析 css 之前的依赖关系，每个loader的功能都是单一的，各自拆分独立。

## 4.url-loader和url-loader

处理css中的图片资源时，我们常用的两种loader是[file-loader](https://link.jianshu.com/?t=https%3A%2F%2Fdoc.webpack-china.org%2Floaders%2Ffile-loader%2F)或者[url-loader](https://link.jianshu.com/?t=https%3A%2F%2Fdoc.webpack-china.org%2Floaders%2Furl-loader%2F)，两者的主要差异在于。url-loader可以设置图片大小限制，当图片超过限制时，其表现行为等同于file-loader，而当图片不超过限制时，则会将图片以[base64](https://so.csdn.net/so/search?q=base64)的形式打包进css文件，以减少请求次数。

url-loader封装了file-loader，但是url-loader不依赖于file-loader，即 使用url-loader时，只需要安装url-loader即可，不需要安装file-loader

参数：

（1）limit：文件大小小于limit参数，url-loader将会把文件转为DataURL；文件大小大于limit，url-loader会调用file-loader进行处理，参数也会直接传给file-loader。

（2）name：输出的文件名规则，如果不添加这个参数，输出的就是默认值：文件哈希；加上[path]表示输出文件的相对路径与当前文件相对路径相同，加上[name].[ext]则表示输出文件的名字和扩展名与当前相同。加上[path]这个参数后，打包后文件中引用文件的路径也会加上这个相对路径。

（3）outputPath：表示输出文件路径前缀。图片经过url-loader打包都会打包到指定的输出文件夹下。但是我们可以指定图片在输出文件夹下的路径。比如outputPath=img/，图片被打包时，就会在输出文件夹下新建（如果没有）一个名为img的文件夹，把图片放到里面。

（4）publicPath：表示打包文件中引用文件的路径前缀，如果你的图片存放在CDN上，那么你上线时可以加上这个参数，值为CDN地址，这样就可以让项目上线后的资源引用路径指向CDN了


file-loader打包的图片会给每张图片都生成一个随机的hash值作为图片的名字

### 三、入口

**入口起点(entry point)**指示 webpack 应该使用哪个模块，来作为构建其内部*依赖图*的开始。进入入口起点后，webpack 会找出有哪些模块和库是入口起点（直接和间接）依赖的。

每个依赖项随即被处理，最后输出到称之为 *bundles* 的文件中

通过在 [webpack 配置](https://www.webpackjs.com/configuration)中配置 `entry` 属性，来指定一个入口起点（或多个入口起点）。默认值为 `./src`。

例子：

~~~js
module.exports = {
  entry: './path/to/my/entry/file.js'
};
~~~

## 四、输出

配置 `output` 选项可以控制 webpack 如何向硬盘写入编译文件。注意，即使可以存在多个`入口`起点，但只指定一个`输出`配置。

### 1.用法

在 webpack 中配置 `output` 属性的最低要求是，将它的值设置为一个对象，包括以下两点：

- `filename` 用于输出文件的文件名。
- 目标输出目录 `path` 的绝对路径。

webpack.config.js：

~~~js
const config = {
  output: {
    filename: 'bundle.js',
    path: '/home/proj/public/assets'
  }
};

module.exports = config;
~~~

## 五、模式

提供 `mode` 配置选项，告知 webpack 使用相应模式的内置优化。

在配置中提供 `mode` 选项：

~~~js
module.exports = {
  mode: 'production'
};
~~~

通常分为开发环境和生产环境，需要不同的配置

## 六、loader

loader 用于对模块的源代码进行转换。loader 可以使你在 `import` 或"加载"模块时预处理文件。因此，loader 类似于其他构建工具中“任务(task)”，并提供了处理前端构建步骤的强大方法。loader 可以将文件从不同的语言（如 TypeScript）转换为 JavaScript，或将内联图像转换为 data URL。loader 甚至允许你直接在 JavaScript 模块中 `import` CSS文件！

例子：

你可以使用 loader 告诉 webpack 加载 CSS 文件，或者将 TypeScript 转为 JavaScript。为此，首先安装相对应的 loader：

~~~js
npm install --save-dev css-loader
npm install --save-dev ts-loader
~~~

然后指示 webpack 对每个 `.css` 使用 [`css-loader`](https://www.webpackjs.com/loaders/css-loader)，以及对所有 `.ts` 文件使用 [`ts-loader`](https://github.com/TypeStrong/ts-loader)：

**webpack.config.js**

~~~js
module.exports = {
  module: {
    rules: [
      { test: /\.css$/, use: 'css-loader' },
      { test: /\.ts$/, use: 'ts-loader' }
    ]
  }
};
~~~

## 七、插件

















































































































































