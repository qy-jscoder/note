[TOC]- HTML5补充
- [一、音频和视频](#一音频和视频)
  - [1.容器](#1容器)
  - [2.编解码器](#2编解码器)
  - [3.常用attribute属性](#3常用attribute属性)
  - [4.常用property属性](#4常用property属性)
  - [5.常用的js相关函数](#5常用的js相关函数)
- [二、新增常用标签](#二新增常用标签)
  - [1. meter](#1-meter)
  - [2. progress](#2-progress)
  - [3. datalist](#3-datalist)
  - [4. details](#4-details)
  - [5. ruby](#5-ruby)
- [三、新增表单类型](#三新增表单类型)
  - [1. type='tel'](#1-typetel)
  - [2. type='url'](#2-typeurl)
  - [3. type='search'](#3-typesearch)
  - [4. type='range'](#4-typerange)
  - [5. type='number'](#5-typenumber)
  - [6. type='color'](#6-typecolor)
  - [7. type='datetime'](#7-typedatetime)
  - [8. type='datetime-local'](#8-typedatetime-local)
  - [9. type='date'](#9-typedate)
- [四、新增表单属性](#四新增表单属性)
  - [1. autofocus](#1-autofocus)
  - [2. required](#2-required)
  - [3. pattern](#3-pattern)
  - [4. formaction](#4-formaction)
- [五、表单其他新增内容](#五表单其他新增内容)
  - [1. validity对象](#1-validity对象)
  - [2. setCustomValidity方法](#2-setcustomvalidity方法)



## 一、音频和视频

在HTML5之前，对视频和音频都没有一个标准。因此在网页中看到的视频都是通过第三方插件嵌入的，可能是Flash、RealPlayer等等。HTML5很好的整合了这些插件。

### 1.容器

大部分人认为视频文件就是.avi，.mp4，但事实上，这仅仅是容器的格式，只决定怎么将视频存储起来，而不决定存储的内容

### 2.编解码器

音频和视频编码/解码是一组算法。用来对特定音频或视频进行解码和编码，以便于音频和视频能够播放。原始的媒体文件体积巨大，不对其进行编码，那么数据是非常惊人的，在互联网上传播则需要耗费无法忍受的体积，如果不对进行解码，那么将对编码后的数据重组为原始的媒体数据

### 3.常用attribute属性

属性值为布尔值的属性，不加属性值也可以生效

videoHeight和videoWidth表示音视频的实际尺寸

（1）control属性

controls 属性是一个 boolean(布尔) 属性。

controls 属性规定浏览器应该为视频提供播放控件。

如果设置了该属性，则规定不存在作者设置的脚本控件。

（2）poster属性

为视频设置封面海报

（3）autoplay属性

设置是否自动播放，属性值为布尔值

（4）loop属性

设置是否循环播放，属性值为布尔值

（5）muted属性

设置静音，属性值为布尔值

（6）preload属性

1）属性值none

不加载视频

2）属性值metadata

只显示视频海报、控件、长度等，只有在播放视频时才会加载视频（默认值，且一般使用该属性值）

3）属性值auto

在用户不知道时，就为用户预先加载好视频

如果属性值为空字符串，也表示auto

### 4.常用property属性

（1）duration属性

媒体总时间（只读）

（2）currentTime属性

开始播放到现在所用的时间（可读写），可理解为进度条所在时间点

（3）muted属性

是否静音（可读写），返回值为布尔值

（4）volume属性

0到1的音量相对值

（5）paused属性

媒体是否暂停（只读），返回值为布尔值

（6）ended属性

媒体是否播放完毕（只读），返回值为布尔值

（7）error属性

媒体发生错误时，返回错误代码（只读）

（8）currentSrc属性

以字符串的形式返回媒体资源地址（只读）



注：muted和volume不同步，要在操作前为这两个属性赋值

### 5.常用的js相关函数

（1）pause：暂停

（2）play：播放

（3）load：重新加载。在通过source标签更改资源地址后要重新加载，才能生效

## 二、新增常用标签

### 1. meter

<meter> 标签定义度量衡。仅用于已知最大和最小值的度量。

比如：磁盘使用情况、电池电量、查询结果的相关性等。

**注意：** <meter> 不能作为一个进度条来使用， 要表示进度条应当使用<progress>标签。

~~~html
<meter value="90" min="0" max="100" low="20" high="80" optimum="50"></meter>
~~~

low和high表示最低值和最高值，一旦小于low或者大于high，度量条就会显示为黄色

### 2. progress

~~~html
<progress min="0" max="100"></progress>
~~~

注：如果没有设置value，进度条会有一个动画效果，其他属性与meter几乎一致

### 3. datalist

datalist标签规定了 <input> 元素可能的选项列表。

datalist标签被用来在为 <input> 元素提供"自动完成"的特性。用户能看到一个下拉列表，里边的选项是预先定义好的，将作为用户的输入数据。

请使用 <input> 元素的 list 属性来绑定 <datalist> 元素。

~~~html
<form action="#" method="get">
    <input list="browsers" name="browser">
    <datalist id="browsers">
        <option value="Internet Explorer">
        <option value="Firefox">
        <option value="Chrome">
        <option value="Opera">
        <option value="Safari">
    </datalist>
    <input type="submit">
</form>
~~~

### 4. details

details标签规定了用户可见的或者隐藏的需求的补充细节。

details标签用来供用户开启关闭的交互式控件。任何形式的内容都能被放在 <details> 标签里边。

details元素的内容对用户是不可见的，除非设置了 open 属性。

~~~html
<details>
    <summary>Copyright 1999-2011.</summary>
    <p> - by Refsnes Data. All Rights Reserved.</p>
    <p>All content and graphics on this web site are the property of the company 		Refsnes Data.</p>
</details>
~~~

### 5. ruby

<ruby> 标签定义 ruby 注释（中文注音或字符）。

在东亚使用，显示的是东亚字符的发音。

将 <ruby> 标签与 rt 和 rp 标签一起使用：
<ruby> 元素由一个或多个需要解释/发音的字符和一个提供该信息的 <rt> 元素组成，还包括可选的 <rp> 元素，定义当浏览器不支持 "ruby" 元素时显示的内容。

~~~html
<ruby>
    汉 <rt>Han</rt>
    字 <rt>zi</rt>
</ruby>
~~~

## 三、新增表单类型

### 1. type='tel'

在pc端和正常文本框没有太大区别，但在手机端会弹出手机键盘

### 2. type='url'

指定输入框内格式为一个url

### 3. type='search'

指定输入框内格式为一个搜索框，自带删除输入框文本内容功能

### 4. type='range'

指定输入框格式为类似进度条，有min、max、step（移一次走多少步）等属性

### 5. type='number'

指定输入框内只能输入数字

### 6. type='color'

指定输入框为一个拾色器

### 7. type='datetime'

显示完整日期（移动端支持）

### 8. type='datetime-local'

是用来专门输入本地日期和时间的文本框，并且在提交时会进行检测。

### 9. type='date'

专门用来输入日期的文本框，提交时会进行检查



等等

## 四、新增表单属性

### 1. autofocus

自动获取焦点

### 2. required

此项必须填写内容

### 3. pattern

正则验证

### 4. formaction

在表单内的元素向一个指定url提交表单，若想其中指定元素提交到不同的url，可通过该属性来设置

## 五、表单其他新增内容

### 1. validity对象

查看验证是否通过

通常在给表单元素加上invalid监听事件，并且验证不通过时 打印

### 2. setCustomValidity方法

setCustomValidity用于判断表单的正误，有错误时可以手动设置提示信息
当没有错误时要将setCustomValidity内参数设置为空，否则表单无法提交

























































