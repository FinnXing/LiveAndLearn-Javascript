[JS01-Introduction](#JS01-Introduction)

- [JavaScript简介](#JavaScript简介)

- [学习JavaScript需要做哪些准备？](#学习JavaScript需要做哪些准备？)

- [在网页中使用JavaScript](#在网页中使用JavaScript)

  - [行内脚本](#行内脚本)
  - [内部脚本](#内部脚本)
  - [外部脚本](#外部脚本)

- [数据类型简介](#数据类型简介)

  - [String](#String)
  - [Number](#Number)
  - [Boolean](#Boolean)
  - [Undefined](#Undefined)
  - [Null](#Null)

- [注释](#注释)

- [变量](#变量)

  - [声明变量](#声明变量)

# JS01-Introduction

## JavaScript 简介

JavaScript是一种具有函数优先的轻量级，解释型或即时编译型的编程语言。虽然它是作为开发Web 页面的脚本语言而出名的，但是它也被用到了很多非浏览器环境中，例如 Node.js、 Apache CouchDB 和 Adobe Acrobat。JavaScript 是一种基于原型编程、多范式的动态脚本语言，并且支持面向对象、命令式和声明式（如函数式编程）风格。

JavaScript 的标准是 ECMAScript 。截至 2012 年，所有的现代浏览器都完整的支持 ECMAScript 5.1，旧版本的浏览器至少支持 ECMAScript 3 标准。2015年6月17日，ECMA国际组织发布了 ECMAScript 的第六版，该版本正式名称为 ECMAScript 2015，但通常被称为 ECMAScript 6 或者 ES6。自此，ECMAScript 每年发布一次新标准。本文档目前覆盖了最新 ECMAScript 的草案，也就是 ECMAScript2020。

这是人类历史上最流行的编程语言。 JavaScript用于添加网站的交互性，开发移动应用程序，桌面应用程序，游戏，如今，JavaScript可用于机器学习和AI。 近年来，JavaScript越来越流行，并且已经连续六年成为领先的编程语言，是Github上使用最多的编程语言。

## 学习JavaScript需要做哪些准备？

1. 积极主动
2. 一台能上网的电脑
3. 安装Node.js
4. 一个浏览器（Chrome）和一个编辑器（VSCode）

## 在网页中使用JavaScript

页面中使用JavaScript的方式有三种：

* 行内脚本
* 内部脚本
* 外部脚本

下面是页面添加JavaScript代码的不同方法

### 行内脚本

在本地新建一个文件夹，文件夹内新建一个`index.html`，将以下代码复制到`index.html`中，然后在浏览器中打开它。

```javascript
<!DOCTYPE html>
<html>
  <head>
    <title>100DaysOfScript:Inline Script</title>
  </head>
  <body>
    <button onclick="alert('欢迎一起学习js')">点我点我</button>
  </body>
</html>
```

恭喜，第一个内联脚本成功运行，我们使用了`alert()`内置函数创建了一个弹窗。

### 内部脚本

内部脚本可以写在页面的`<head>`或`<body>`中，但是最好将其放在HTML文档的`<body>`中。 首先，我们先在`<head>`中写脚本。

``` javascript
<!DOCTYPE html>
<html>
  <head>
    <title>100DaysOfScript:Internal Script</title>
		<script>
    	console.log("欢迎一起学习JS")  
    </script>
  </head>
  <body></body>
</html>
```

实际工作中我们经常把JS写在`<body>`的最后，打开浏览器控制台查看一下以下代码的输出。

```javascript
<!DOCTYPE html>
<html>
  <head>
    <title>100DaysOfScript:Internal Script</title>
  </head>
  <body>
    <button onclick="alert('欢迎一起学习JS');">点我点我</button>
    <script>
      console.log('欢迎一起学习JS')
    </script>
  </body>
</html>
```

### 外部脚本

和内部脚本类似，外部脚本也可以写在页面的`<head>`或`<body>`中，推荐写在`<body>`最后，首先在刚刚的文件夹中新建一个`introduction.js`，以.js为扩展名的文件都是JS文件，在`introduction.js`中写入一下JS代码，然后再将`introduction.js`链接到页面中。

```javascript
console.log('欢迎一起学习JS');
```

写在`<head>`中

```javascript
<!DOCTYPE html>
<html>
  <head>
    <title>100DaysOfScript:External script</title>
    <script src="introduction.js"></script>
  </head>
  <body></body>
</html>
```

写在`<body>`中

```javascript
<!DOCTYPE html>
<html>
  <head>
    <title>100DaysOfScript:External script</title>
  </head>
  <body>
    <script src="introduction.js"></script> 
		// 也可以引入多个外部脚本
		<script src="introduction1.js"></script>   
  </body>
</html>
```

打开浏览器控制台查看代码输出。

## 数据类型简介

JS和其他编程语言中都存在不同类型的数据类型，以下是JS的基础数据类型：`String`，`Number`，`Boolean`，`undefined`，`Null`，`Symbol`。

### String

`String`可以包含在单引号（`''`）、双引号（`""`）或反引号（` `` `）中，例如：

```javascript
'Hello Word'
"你好"
`欢迎一起学习JS`
```

### Number

`Number`类型代表整数和浮点数，例如：1、23、-23、0、3.23、-1.234。。。。。。

### Boolean

`Boolean`类型仅包含两个值：`true`和`false`。任何比较都会返回一个布尔值，要么为真，要么为假。

### Undefined

`Undefined`的含义是 `未被赋值`，在JS中，如果不给变量分配值，则该值是不确定的。 除此之外，如果一个函数不返回任何东西，它将返回未定义的。

```javascript
let firstName;
console.log(firstName) // 未定义，因为firstName没有赋值
```

### Null

`Null`在JS中指特殊值`空值`

```javascript
let emptyValue = null
```

## 注释

注释可以使代码更具可读性，JS中的注释与其他编程语言相似。有以下两种注释方式：

* 单行注释 `//`
* 多行注释 `/* */`

```javascript
// 这是单行注释
/*
  这里是
  多行注释
  */
```



## 变量

变量用于存储数据，是数据的‘命名存储’，我们可以用变量保存商品、用户等等信息。在JS中创建变量可以使用`var`，`let`，`const`关键字。

创建一个在之后有可能会修改的变量可以使用`var`或`let`，如果变量不会改变则可以使用`const`来创建。

变量名的定义需要遵循以下规则：

* 可以包含字母和数字，但是不能以数字开头
* 不可以使用除`$`和`_`以外的其他特殊字符
* 不能使用保留字作为变量名，例如：`let`，`var`，`return`等等
* 建议使用驼峰命名法（camelCase）命名变量

示例：

```javascript
firstName
city
first_name
num_1
$num1
year2021
```

无效变量命名

```javascript
first-name
1_num
num_#_1
```

### 声明变量

声明变量需要在变量名前使用`var`、`let`、`const`关键字，变量名后接一个等号和一个值。

```javascript
let firstName = 'ZhangSan'
const age = 100
let isMarried = true
// 也可以使用逗号分隔一行声明
let name = 'a',
    job = 'FE';
console.log(firstName, age, isMarried, name, job)
```



🎉 先来简单的了解一下JS，后面加油继续深入学习。🎉