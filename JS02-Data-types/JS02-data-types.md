[数据类型](#数据类型)

* [简单数据类型](#简单数据类型)

  - [Undefined](#Undefined)
  - [Null](#Null)
  - [Boolean](#Boolean)
  - [Number](#Number)
  - [Null](#Null)
  - [String](#String)
  - [Symbol](#Symbol)
  - [BigInt](#BigInt)

* [复杂数据类型](#复杂数据类型)

  - [Object](#Object)

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

```javascript
let msg;
console.log(msg == undefined); // true
```

也可以显式的将`undefined`赋值给变量，但是不建议这样做，因为默认情况下，任何未经初始化的变量都会取得`undefined`值，ECMA中增加这个特殊值的目的就是区别`null`和未初始化变量。

```javascript
let msg = undefined;
console.log(msg == undefined); // true
```
需注意，包含`undefined`值的变量和未定义变量是有区别的，请看下面例子
```javascript
let msg; // 这个变量被声明了，值为undefined
// 没有声明过 name 变量
// let name;
console.log(msg); // "undefined"
console.log(name); // 报错
```
#### Null
`Null`类型同样只有一个值，即特殊值`null`。逻辑上讲，null值表示一个空对象指针，这也是使用`typeof`方法鉴别`null`的类型时返回一个"object"的原因：

```javascript
let car = null;
console.log(typeof car); // "object"
```

把`null`作为尚未创建的对象，也许更好理解，所以在定义将来要保存对象值的变量时，建议使用`null`来初始化，不要使用其他值。这样只要检查这个变量的值是不是`null`就可以知道这个变量是否在后来被重新赋予一个对象的引用，比如：

```javascript
if(car != null){
  // car是一个对象的引用
}
```

如前所述，永远不必显式的将变量值设置为`undefined`，但是`null`不是这样的。任何时候，只要变量要保存对象，而当时有没有一个对象可保存，就要用`null`来填充该变量，这样就可以保持`null`是空对象指针的语义，并进一步将其与`undefined`区分开来。

`null`是一个假值。因此，如果需要，可以用更简洁的方式检测它。不过要记住，也有很多其他可能的值同样是假值，所以一定要明确自己想检测的就是`null`这个字面值，而不仅仅是假值。

```javascript
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

`Boolean`（布尔值）类型是JS中使用最频繁的类型之一，有两个字面值：`true`和`false`。`Boolean`类型通常用于存储表示`yes`或`no`的值：`true`意味着“yes，真，正确”，`false`意味着“no，假，不正确”。这两个布尔值不同于数值，因此`true`不等于1，`false`不等于0。下面是给变量赋布尔值的例子：

```javascript
let found = true;
let lost = false;
```

注意，布尔值字面量`true`和`false`是区分大小写的，因此`True`和`False`（及其他形式的大小混写）是有效的标识符，但不是布尔值。

虽然布尔值只有两个字面值，但是所有其他类型的值都有相应布尔值的等价形式。要将一个其他类型的值转换成布尔值，可以调用特定的`Boolean()`转型函数：

```javascript
let msg = "hello world";
let msgAsBoolean = Boolean(msg);
```

这个例子中，字符串`msg`被转换为布尔值并保存在变量`msgAsBoolean`中，`Boolean()`转型函数可以在任意类型的数据上调用，而且始终返回一个布尔值。具体转化为`true`还是`false`取决于数据类型和实际的值。下表总结了不同类型与布尔值之间的转换规则。

| 数据类型 | 转换为true的值 | 转换为false的值 |
| --- | --- | --- |
| Boolean | true | false |
| String | 非空字符串 | ""(空字符串) |
| Number | 非零数值 | 0、NaN |
| Object | 任意对象 | null |
| Undefined | N/A(不存在) | undefined |

以上转换非常重要，在`if`等控制语句中会自动执行其他类型到布尔值的转换，例如：

```javascript
let msg = "Hello World";
if ( msg ) {
  console.log("Value is true"); // Value is true
}
```

这个例子中，`console.log`会打印出”`Value is true`“，因为字符串`msg`会自动转换为等价的布尔值`true`。由于这种自动转换的存在，理解控制语句中使用的是什么变量就非常重要。错误地使用对象而不是布尔值会明显改变应用程序的执行流。

#### Number

`Number`是ECMAScript中最有意思的数据类型。`Number`类型使用IEEE754格式表示整数和浮点数。不同的数值类型相应的也有不同的数值字面量格式。

最基本的数值字面量格式是十进制整数，可以直接写出来：

```javascript
let intNum = 12; // 整数
```

整数也可以用八进制和十六进制字面量表示。八进制字面量，第一个数字必须是0，然后是相应的八进制数字（0-7），注意严格模式下八进制字面量是无效的，JS引擎会抛出语法错误；十六进制字面量，开头是数值前缀0x（区分大小写），然后是十六进制数字（0-9及A-F），十六进制数字中的字母大小写均可。使用八进制和十六进制格式创建的数值在所有数学操作中都被视为十进制数值。

```javascript
let octalNum1 = 070; // 八进制的56
let octalNum2 = 079; // 无效的八进制值，当成79处理
let octalNum3 = 08; // 无效的八进制值，当成8处理

let hexNum1 = 0xA; // 十六进制的10
let hexNum2 = 0x1f; // 十六进制的31
```

* __浮点数__

定义浮点数，必须包含小数点，而且小数点后面至少有一个数字。

```javascript
let floatNum1 = 1.1;
let floatNum2 = 0.1;
let floatNum3 = .1; // 有效，但不推荐
```

浮点数可以用科学计数法来表示非常大或非常小的数值。

```javascript
let floatNum1 = 3.123e7; // 等于31230000
let floatNum2 = 3e-7; // 等于0.0000003
```

浮点数最高可精确到17为小数，但是在算数计算中远不如整数精确，例如，0.1加0.2得到的不是0.3，而是0.30000000000000004。由于这种微小的舍入错误，导致很难测试特定的浮点值。

```javascript
if( a+b == 0.3 ) { // 别这么干 0.1+0.2=0.30000000000000004
  console.log("It is 0.3");
}
```

这里检测两个数值之和是否等于0.3。如果两个数值分别是0.05和0.25，或者0.15和0.15，那没问题。但如果是0.1和0.2，如前所述，测试将失败。因此永远不要测试某个特定的浮点值。

* __NaN__

`NaN`是一个特殊的数值，意思是”不是数值“（Not a Number），用来表示本来要返回数值的操作失败了（不是抛出错误）。比如，用0除任意数值在其他语言中通常会报错，但是JS中，0、+0或-0相除会返回NaN：

```javascript
console.log(0/0); // NaN
console.log(-0/0); // NaN
```

如果分子是非0值，分母是有符号0或者无符号0.则会返回`Infinity`或`-Infinity`：

```javascript
console.log(4/0); // Infinity
console.log(3/-0); // -Infinity
```

`NaN`有几个特殊属性。首先，任何设计`NaN`的操作始终返回`NaN`；其次，`NaN`不等于包含`NaN`在内的任何值。

```javascript
console.log(NaN == NaN); // false
```

为此JS提供了`isNaN()`函数。该函数接收一个参数，可以是任意类型的数据，然后判断这个参数是否”不是数值“。参数传给`isNaN()`后，该函数会尝试把它转换为数值，如果不能转换为数值函数返回`true`：

```javascript
console.log(isNaN(NaN)); // true
console.log(isNaN(10)); // false，10是数值
console.log(isNaN("10")); // false，字符串被转换为数值10
console.log(isNaN("black")); // true，不可以转换为数值
console.log(isNaN(true)); // false，true可以转换为数值1
```

* __数值转换__

要把非数值转换为数值，可以使用三个转型函数：`Number()`、`parseInt()`和`parseFloat()`，这三个转型函数可用于任何数据类型，后两个函数主要用于将字符串转换为数值。对于同样的参数，这三个函数执行的操作是不同的。

`Number()`函数基于以下规则执行转换：

1. 布尔值：`true`转换为1，`false`转换为0
2. 数值：直接返回
3. `null`：返回0
4. `undefined`：返回`NaN`
5. 字符串：

    如果字符串包含数值字符，包括数值字符前面带加、减号的情况，则转化为一个十进制数值。因此，`Number("1")`返回1，`Number("123")`返回123 ，`Number("012")`返回12（忽略前面的0）。

    如果字符串包含有效的浮点值格式如”1.1“，则会转换为相应的浮点值（同样忽略前面的0）。

    如果字符串包含有效的十六进制格式如”0xf“，则会转换为与该十六进制对应的十进制整数值。

    如果是空字符串，返回0.

    如果字符串包含上述情况之外的其他字符，则返回NaN。

6. 对象：调用`valueOf()`方法，并暗战上述规则转换返回值。如果转换结果是`NaN`，则调用`toString()`方法，在按照转换字符串的规则转换。

```javascript
let num1 = Number("Hello world"); // NaN
let num2 = Number(""); // 0
let num3 = Number("0012"); // 12
let num4 = Number(true); // 1
```

由于`Number()`函数转换字符串时相对复杂且有点反常规，通常在需要得到整数时可以使用`parseInt()`函数。`parseInt()`函数更专注与字符串是否包含数值模式。字符串最前面的空格会被忽略，从第一个非空字符串开始转换，如果第一个字符串不是数值字符、加号或减号，`parseInt()`立即返回`NaN`，所以空字符串也会返回`NaN`。如果第一个字符串是数值字符、加号或减号，则继续一次检测每个字符，直到字符串末尾，或碰到非数值字符。

```javascript
let num1 = parseInt("234adb"); // 234
let num2 = parseInt(""); // NaN
let num3 = parseInt("0xA"); // 10，解释为十六进制整数
let num4 = parseInt(22.5); // 22
let num5 = parseInt("70"); // 70
```

`parseInt()`函数还接收第二个参数，用于指定进制数。如果知道要解析的值是十六进制，可以传入16作为第二个参数：

```javascript
let num = parseInt("0xAF", 16); // 175
// 如果提供了十六进制参数，前面的“0x”可以省掉
let num1 = parseInt("AF", 16); // 175
let num2 = parseInt("AF"); // NaN
let num3 = parseInt("10", 2); // 2，按二进制解析
let num4 = parseInt("10", 8); // 8，按八进制解析
```

`parseFloat()`函数跟`parseInt()`函数类似，也是从位置0开始检测每个字符，解析到字符串末尾或者解析到一个无效的浮点数值字符为止。这意味着第一次出现的小数点是有效的，但是第二个出现的小数点就无效了。

`parseFloat()`函数的不同之处在于，他始终忽略字符串开头的0，这个函数能识别前面讨论的所有浮点格式，以及十进制格式。十六进制数值始终会返回0.因为`parseFloat()`只解析十进制值，它不能指定进制数。

```javascript
let num1 = parseFloat("122kad"); // 122
let num2 = parseFloat("0xA"); // 0
let num3 = parseFloat("22.3"); // 22.3
let num4 = parseFloat("23.34.5"); // 23.34
let num5 = parseFloat("09.3"); // 9.3
let num6 = parseFloat("3.12e5"); // 312000
```

#### String
#### Symbol
#### BigInt
### 复杂数据类型
#### Object