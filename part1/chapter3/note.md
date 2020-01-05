##  数据类型

-  五种简单数据类型
	- `Undefined`
	- `Null`
	- `Boolean`
	- `Number`
	- `String`

- 复杂数据类型（`Object`）
  - Object 本质上是由一组无序的键值对组成的

### `typeof` 操作符
ECMAScript是松散类型，typeof可以用来判断给定变量的数据类型。
  
typeof的返回值可能是以下几种：
- `undefined` ----表示值未定义
- `boolean`   ----表示值为布尔值
- `string`			----表示值是字符串
- `number`			----表示值是数字
- `object`			----表示这个值是对象或者null
- `function`		----表示这个值是函数
> code：Example01.js
### Undefined 类型
`Undefined`类型只有一个值，就是特殊的`Undefined`。在使用`var`、`let`、声明变量但未对其初始化时，默认的值就是`Undefined`。 

>在使用`const`时一定要注意赋初始值。否则会出现
> Uncaught SyntaxError: Missing initializer in const declaration  
>code: Example02.js

``` js
var message;
console.log(message == undefined); // true
```
等价于
``` js
var message = undefined;
```
只声明但不初始化，得到的默认值就是undefined，如字面意义`未定义`。
> 引入这个值是为了正式区分空对象指针与未经初始化的变量

包含undefined值的变量和尚未定义的变量还是不一样的
>code Example03.js

未声明的变量直接使用会报错，但是可以使用`typeof`来判断类型
``` js
let a;
typeof a; //undefined
typeof b; //undefined
```
> 逻辑上的合理性；但还是推荐显示初始化变量，这样在typeof出现undefined时可以明确知道是未定义而不是未赋值；

### NULL 类型
Null也只有一个值，表示一个空对象指针。
``` js 
var car = null;
typeof car; // object
```
如果定义的变量在将来会储存对象，那么初始化的时候应该初始化为null，这样检查类型的时候如果为null就可以知道是否已经保存一个对象的引用。
``` js
if (car != null){
	// do something...
}
```
实际上undefined是派生自null的，因此ECMA-262规定它们相等测试为true;
``` js
console.log(null == undefined);
```
> 关于 '==' 和 '==='后面会整理

### Boolean 类型
Boolean 类型有两个字面值：`true`和`false`，它是使用最频繁的一种数据类型。
> 和数字类型还是有区别的， 1不一定等同与true, 0不一定等同false
``` js
var found = true;
var lost = false;
```
> True 和 False 都不是Boolean类型，是标识符. Boolean类型区分大小写。
虽然Boolean字面值只有两个，但是ECMAScript中所有数据类型的值都有与这两个Boolean值等价的值。转型函数Boolean()可以做到这点。
``` js
var message = "hello";
var messageAsBoolean = Boolean(message); // true
```
可以对任何数据类型的值调用Boolean()函数，而且总会返回一个Boolean值。
下面给出对应的转换规则，具体的返回值由要转换值的数据类型和实际值决定。

|数据类型|转换为true的值|转换为false的值|
|--|--|--|
|Boolean|true|false|
|String|非空字符串|空字符串""|
|Number|任何非零数字(包括无穷大)|0和NaN|
|Object|任何对象| null|
|Undefined|n/a|undefined|
> n/a： no applicable的缩写,"不适用“

### Number类型
Number类型用来表示整数和浮点数

