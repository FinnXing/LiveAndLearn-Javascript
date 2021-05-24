## 数据类型
在上一篇文章中，我们简单介绍了一下JS中的数据类型，数据类型可分为：简单数据类型（原始类型）和复杂数据类型（引用类型），JS中一共有8种数据类型，今天我们将对它们进行大体的介绍，之后会有专门章节对每种类型进行详细介绍。

JS是一种弱类型语言，这意味着你不用提前声明变量的类型，在程序运行过程中，类型会被自动确定，这也意味着你可以使用同一个变量保存不同类型的数据。

最新的ECMAScript标准定义了8中数据类型，其中包含7种简单数据类型和1种复杂数据类型。

### 简单数据类型

除Object以外的所有类型都是不可变的（值本身无法被改变），例如JS中对字符串的操作一定返回了一个新的字符串，原始字符串并没有被改变。我们称这些类型为“原始值”。

简单数据类型包含以下7种：
* Undefined
* Null
* Boolean
* Number
* String
* Symbol
* BigInt

#### Undefined

Undefined类型只有一个值，就是特殊值undefined。当使用var或let声明了变量，但是没有初始化时，就相当于给变量赋予了undefined值：
```
let msg;
console.log(msg == undefined); // true
```
也可以显式的将 undefined 赋值给变量，但是不建议这样做，因为默认情况下，任何未经初始化的变量都会取得 undefined 值，ECMA中增加这个特殊值的目的就是区别 null 和未初始化变量。
```
let msg = undefined;
console.log(msg == undefined); // true
```
需注意，包含undefined值的变量和未定义变量是有区别的，请看下面例子
```
let msg; // 这个变量被声明了，值为undefined
// 没有声明过 name 变量
// let name;
console.log(msg); // "undefined"
console.log(name); // 报错
```

#### Null
#### Boolean
#### Number
#### String
#### Symbol
#### BigInt
### 复杂数据类型
* Object