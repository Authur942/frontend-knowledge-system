# JavaScript（`ES5`）

## JavaScript的基本语法

- JavaScript严格区分大小写
- JavaScript会忽略大量空格和换行
- 在语句后面需要加上英文 `;` ，否则的话就会消耗系统的资源，在不加的情况下会系统会自动帮你语句后面加上`;`。

## 字面量和变量

- 字面量是字面上意思的量也是不可改变的值。
- 变量的话就是可以改变的量，声明变量的话要用var，在ES6中不使用var来声明变量，let来声明变量，const来声明常量。
- 声明变量之后要给变量赋值。

## 标识符

- 标识符就是我们可以用来命名 **变量名** 、**函数名** 、**属性名** 都是属于标识符

- 命名标识符要遵守如下规则：

  1.标识符中可以含有数字、字母、'' _ "、$。
  2.标识符不可以数字作为开头。
  3.标识符不能是ES中的关键字和保留字。
  4.标识符的命名一般都采用驼峰命名法，首字母小写，第二个单词中的首字母大写。
  5.`JS`底层保存标识符时实际上时采用Unicode编码，所以理论上讲，所有的`utf-8`中含有的内容都可以作为标识符。

## 数据类型

> 就是当我们给变量赋值的时候，字面量拥有多个数据类型。

用 `typeof` 来检验一个变量的数据类型。
1.`String` 字符串
2.`number` 数值
3.`Boolean` 布尔值
4.`null` 空值
5.`undefined` 未定义
6.`object` 对象

**==1-5都是基本数据类型，object是引用数据类型==**



### `string`

- 在`JS`中字符串需要使用引号引起来。
- 一定要注意加上双引号才是字符串类型，不加的话就是变量。
- 使用双引号或单引号都可以，**但是不要混着用** 。

```js
var str = "我说："今天的天气很好"";
在这个时候，需要用到`\`转义字符
```

- 当使用一些特殊符号的时候需要用到 \进行转义。

  - \ " 表示 "
  - \ ' 表示 '
  - \ n 表示 换行符
  - \ t 表示 制表符
  - \ \ 表示 \

  > **注意** 上面“ \”后面是不带空格的。

### `number`

- number就是包括所有的整数和浮点数。
- `number.MAX_VALUE` 就是控制台返回的值正无穷的数，`number.MIN_VALUE` 表示的是大于零的最小数。
- `MAX_VALUE`、`MIN_VALUE`返回的数据类型是`number`。
- 如果使用JS进行浮点型计算的话，可能会得到一个不精确的结果。
- NAN表示`Not A Number`。

```js
var a = MAX_VALUE
console.log(a)
//返回Infinity 表示正无穷数
var a = "abc" * "def";
console.log(a);
//控制台返回NAN
```

### `Boolean`

- 只有两个值，主要用来做逻辑判断。
- true 表示真。
- false 表示假。
- 用`typeof`检查会返回boolean。

### `Null`和`Undefined`

- null专门用来表示空值的，值是null。
- null用`typeof`检验返回的是object类型。
- undefined是声明了一个变量，但是没有赋值则会返回undefined。
- 如果变量赋值为undefined，本身就没有意义，无须如此赋值。

### `object`

## 强制类型转换

### String

- 指将一个数据类型强制转换为其他的数据类型。

- 类型转换主要指，将其他的数据类型，转换为string number boolean。

- 将其他的数据类型转换为string

  - 方式一：

    1.调用被转换数据类型的 `toString()` 方法
    2.该方法不会影响到原变量，它会将转换的结果返回
    3.但是注意！null和undefined这两个值是没有`toString()` 方法，如果调用会报错

  - 方式二:

    1.调用`String()`函数，并将被转换的数据作为参数传递给函数
    2.使用`String()`函数做强制类型转换时

    - 对于number和`Boolean`实际上就是调用的`toString()` 方法
    - 但是对于null和`undefined`，就不会调用`toString()`方法
    - 它会将null（这是字面量null） 直接转换为 "null"（这是字符串null）
    - 将undefined 直接转换为 "`undefined`"

```js
var a = 123;
a.toString()
console.log(typeOf a)
console.log(a)
// string
// "123"
var a = 123;
a = String(a)

console.log(typeOf a)
console.log(a)

// string
// "123"
var a = null
a = String(a)

console.log(typeOf a)
console.log(a)

// string
// "null" 注意这里是字符串"null"
```

### number

将其他的数据类型转换为Number

- 方式一：使用Number()函数

1. 字符串--》数字
   - 如果是纯数字的字符串，则直接将其转换为数字
   - 如果字符串中（只要）有非数字的内容，则转换为`NaN`
   - 如果字符串是一个空串或者是一个全是空格的字符，则转换为0
2. 布尔--》数字
   - true 转换成 1
   - false 转换成 0
3. null--》数字
   - 值转换成0
4. undefined--》数字
   - 值转换成`NaN`

- 方式二：调用`parseInt()`函数
  - 这种方式专门用来对付字符串
  - `parseInt()` 把一个字符串转换为一个整数
  - `parseInt()`

## 防抖和节流

**防抖**

```js
/**
 * 防抖函数
 * @fn 需要执行的函数
 * @delay 毫秒，防抖期限值
 */
// 旧代码
function debounce (fn, delay) {
  let timer = null //借助闭包
  return function () {
    if (timer) {
      clearTimeout(timer)
      timer = setsetTimeout(fn, delay)
    } else {
			timer = setTimeout(fn, delay)
    }
  }
}

// 简化后的代码
function debounce (fn, delay) {
  let timer = null
  return function () {
    if (timer) {
      clearTimeout(timer)
    }
    timer = setTimeout(fn, delay)
  }
}

function showTop () {
  var scrollTop = document.body.scrollTop || document.documentElement.scrollTop
  console.log('滚动条位置：' + scrollTop)
}

export { debounce, showTop }

// 在Vue项目中引入
import { debounce, showTop } from '@/...'

window.onscroll = debounce(showTop, 1000)
```

**节流**

```js
```

