## 数据类型
在上一篇文章中，我们简单介绍了一下JS中的数据类型，数据类型可分为：简单数据类型（原始类型）和复杂数据类型（引用类型），JS中一共有8种数据类型，今天我们将对它们进行大体的介绍，之后会有专门章节对每种类型进行详细介绍。

JS是一种弱类型语言，这意味着你不用提前声明变量的类型，在程序运行过程中，类型会被自动确定，这也意味着你可以使用同一个变量保存不同类型的数据。

最新的ECMAScript标准定义了8中数据类型，其中包含7种简单数据类型和1种复杂数据类型。

### 简单数据类型

除`Object`以外的所有类型都是不可变的（值本身无法被改变），例如JS中对字符串的操作一定返回了一个新的字符串，原始字符串并没有被改变。我们称这些类型为“原始值”。

简单数据类型包含以下7种：
* Undefined
* Null
* Boolean
* Number
* String
* Symbol
* BigInt

#### Undefined

`Undefined`类型只有一个值，就是特殊值`undefined`。当使用var或let声明了变量，但是没有初始化时，就相当于给变量赋予了`undefined`值：
```
let msg;
console.log(msg == undefined); // true
```
也可以显式的将`undefined`赋值给变量，但是不建议这样做，因为默认情况下，任何未经初始化的变量都会取得`undefined`值，ECMA中增加这个特殊值的目的就是区别`null`和未初始化变量。
```
let msg = undefined;
console.log(msg == undefined); // true
```
需注意，包含`undefined`值的变量和未定义变量是有区别的，请看下面例子
```
let msg; // 这个变量被声明了，值为undefined
// 没有声明过 name 变量
// let name;
console.log(msg); // "undefined"
console.log(name); // 报错
```
#### Null
`Null`类型同样只有一个值，即特殊值`null`。逻辑上讲，null值表示一个空对象指针，这也是使用`typeof`方法鉴别`null`的类型时返回一个"object"的原因：
```
let car = null;
console.log(typeof car); // "object"
```
把`null`作为尚未创建的对象，也许更好理解，所以在定义将来要保存对象值的变量时，建议使用`null`来初始化，不要使用其他值。这样只要检查这个变量的值是不是`null`就可以知道这个变量是否在后来被重新赋予一个对象的引用，比如：
```
if(car != null){
  // car是一个对象的引用
}
```
如前所述，永远不必显式的将变量值设置为`undefined`，但是`null`不是这样的。任何时候，只要变量要保存对象，而当时有没有一个对象可保存，就要用`null`来填充该变量，这样就可以保持`null`是空对象指针的语义，并进一步将其与`undefined`区分开来。

`null`是一个假值。因此，如果需要，可以用更简洁的方式检测它。不过要记住，也有很多其他可能的值同样是假值，所以一定要明确自己想检测的就是`null`这个字面值，而不仅仅是假值。
```
let msg = null;
let car;
if(msg) {
  // 这个块不会执行
}
if(!msg) {
  // 这个块会执行
}
if(car) {
  // 这个块不会执行
}
if(!car) {
  // 这个块会执行
}
```
#### Boolean
Boolean（布尔值）类型是JS中使用最频繁的类型之一，有两个字面值：true和false。Boolean类型通常用于存储表示yes或no的值：true意味着“yes，真，正确”，false意味着“no，假，不正确”。这两个布尔值不同于数值，因此true不等于1，false不等于0。下面是给变量赋布尔值的例子：

```
let found = true;
let lost = false;
```

注意，布尔值字面量true和false是区分大小写的，因此True和False（及其他形式的大小混写）是有效的标识符，但不是布尔值。

虽然布尔值只有两个字面值，但是所有其他类型的值都有相应布尔值的等价形式。要将一个其他类型的值转换成布尔值，可以调用特定的Boolean()转型函数：
```
let msg = "hello world";
let msgAsBoolean = Boolean(msg);
```
这个例子中，字符串msg被转换为布尔值并保存在变量msgAsBoolean中，Boolean()转型函数可以在任意类型的数据上调用，而且始终返回一个布尔值。具体转化为true还是false取决于数据类型和实际的值。下表总结了不同类型与布尔值之间的转换规则。

| 数据类型 | 转换为true的值 | 转换为false的值 |
| --- | --- | --- |
| Boolean | true | false |
| String | 非空字符串 | ""(空字符串) |
| Number | 非零数值 | 0、NaN |
| Object | 任意对象 | null |
| Undefined | N/A(不存在) | undefined |

以上转换非常重要，在if等控制语句中会自动执行其他类型到布尔值的转换，例如：
```
let msg = "Hello World";
if ( msg ) {
  console.log("Value is true"); // Value is true
}
```
这个例子中，console.log会打印出”Value is true“，因为字符串msg会自动转换为等价的布尔值true。由于这种自动转换的存在，理解控制语句中使用的是什么变量就非常重要。错误地使用对象而不是布尔值会明显改变应用程序的执行流。

#### Number
#### String
#### Symbol
#### BigInt
### 复杂数据类型
* Object