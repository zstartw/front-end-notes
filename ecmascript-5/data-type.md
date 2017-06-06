在 JavaScript 代码中，能够表示并操作值的类型称之为**数据类型**。



![](03.png)

## 原始类型


> 
> - 由于 JavaScript 是区分大小写的，布尔类型的 true 和 false 全部是小写。
> - JavaScript 也可以将其他类型的数据，自动转换为布尔类型。
| --- | --- | --- |
| boolean类型 | true | false |
| string类型 | 任何非空字符串 | “”（空字符串）|
| number类型 | 任何非零数字值（包括无穷大）| 0和NaN |
| object类型 | 任何对象 | null |
| undefined | | undefined |

## number 类型
- 浮点类型: 表示小数，JavaScript 中的所有数字均用浮点类型表示。

> **值得注意的是:** 八进制或十六进制的数值最终会被转换成十进制数值。
var floatNum1 = 0.1;
```

> **值得注意的是:**
> 
> - JavaScript允许小数点前可以没有整数，但不推荐这种写法。
> - 保存浮点类型需要的空间是保存整数类型的两倍。
> - 如果小数点后面没有任何数字，那这个数值作为整数类型保存。
var floatNum3 = 1.;// 小数点后面没有数字 —— 解析为 1
```

### 四舍五入误差

```javascript
var x = .3 - .2;
```

> **值得注意的是:** 建议使用大整数表示金额。例如使用分作为单位，而不是使用元作为单位。

### NaN

- 任何涉及NaN的操作都会返回NaN。
console.log(isNaN(10));// 输出false（10是一个数值）
```

## string 类型
var firstString = "Nicholas";
```

string类型包含一些特殊的转义字符，用于表示非打印字符。
| --- | --- |
| \n | 换行符 |
| \t | 制表符 |
| \b | 退格符 |
| \r | 回车符 |
| \f | 换页符 |
| \\ | 斜杠 |
| \' | 单引号（'），在用单引号表示的字符串中使用。|
| \" | 双引号（"），在用双引号表示的字符串中使用。|

## typeof 运算符

```javascript
var message = "this is message";
```

> **值得注意的是:** typeof 运算符加上圆括号，会像是函数，而不是运算符，并不建议这种写法。

| 值 | 类型 |
| --- | --- |
| true或false | boolean |
| 任意数字或NaN | number |
| 任意字符串 | string |
| null | object |

## 包装类型

### 包装类型概述

在 JavaScript 中，对应原始类型提供了包装类型。通过包装类型可以创建原始类型的对象（后面的课程学习）。




### Boolean 类型
var bool = new Boolean(true);
```

boolean 类型与 Bollean 类型的区别:

- typeof 运算符对原始类型返回 "boolean"，而对包装类型为 "object"。
- instanceof 运算符测试 Boolean 类型返回 true，而测试 boolean 类型返回 false。

> **值得注意的是:** 不建议使用 Boolean 类型。

Number 类型是原始类型 number 类型对应的包装类型。
var num = new Number(10);
```

number 类型与 Number 类型的区别:

- typeof 运算符对原始类型返回 "number"，而对包装类型为 "object"。
- instanceof 运算符测试 Number 类型返回 true，而测试 number 类型返回 false。

> **值得注意的是:** 不建议使用 Number 类型。

### String 类型
var str = new String("hello world");
```

string 类型与 String 类型的区别:

- typeof 运算符对原始类型返回 "string"，而对包装类型为 "object"。
- instanceof 运算符测试 String 类型返回 true，而测试 string 类型返回 false。

> **值得注意的是:** 不建议使用 String 类型。

### instanceof 运算符

instanceof 运算符的左操作数是一个包装类型的变量，右操作数是对应的数据类型。如果左侧的变量是右侧的数据类型，则表达式返回 true；否则返回 false。例如下述代码:

```javascript
var str = "this is message";
```

> **值得注意的是:** 所有对象都是 Object 类型的实例对象，通过 instanceof 运算符判断一个对象是否为具体数据类型，也包含"父类"。（后面课程会学习）

## 特殊类型

### undefined

JavaScript 中有两个表示空的数据类型，undefined 和 null，其中比较有用的是 undefined。undefined 类型只有一个值，就是 undefined。

下列情况会返回undefined:

- 访问未修改的变量 undefined
- 没有定义 return 表达式的函数隐式返回 undefined
- return 表达式没有显式的返回任何内容
- 访问不存在的属性
- 任何被设置为 undefined 值的变量

### null

null 类型是 JavaScript 中的一个特殊类型，用于表示一个不再指向任何内存空间地址的变量。
var atguigu = null;
```

### undefined 与 null
- 不同点
	- undefined: 表示变量声明但未被赋值，是所有未赋值变量的默认值。一般很少主动使用。
	- null: 表示一个没有指向任何内存地址的变量，将来可能指向某个具体内存地址。一般用于主动释放资源。

## 类型转换

### 隐式类型转换

由于 JavaScript 是弱类型/松散类型的，在任何情况下都可以强制转换。

- 转换为字符串: 将一个值加上空字符串可以轻松转换为字符串类型。

```javascript
'' + 10 === '10'; // true
```

- 转换为数字: 使用一元的加号操作符，可以把字符串转换为数字。

```javascript
+'10' === 10; // true
```

- 转换为布尔值: 使用否操作符两次，可以把一个值转换为布尔型。

```javascript
!!'foo'; // true
```

### 显式类型转换

- 使用 JavaScript 的包装类型的构造函数进行类型转换。

| 构造函数 | 描述 |
| --- | --- |
| Number() | 将字符串或布尔值转换为数字，如果包含非法字符，则返回NaN。|
| String() | 将数字或布尔值转换为字符串。|
| Boolean() | 将字符串或数字转换为布尔值。|

- 使用数据类型的转换函数进行类型转换。

| 构造函数 | 描述 |
| --- | --- |
| toString() | 将数字或布尔值转换为字符串。|
| parseInt() | 将字符串或布尔值转换为整数类型。|
| parseFloat() | 将字符串或布尔值转换为浮点类型。|