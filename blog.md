深入理解JavaScript原型和闭包

# 一切皆是对象

在JavaScript中一切皆是对象，但是要注意的是值类型不是对象。

首先我们先看看在JavaScript中的一个运算符`typeof`，这个可以说是我们的老朋友了，它用于检测变量的类型。

```js
function show(x) {

  console.log(typeof x);    // undefined
  console.log(typeof 10);   // number
  console.log(typeof 'abc'); // string
  console.log(typeof true);  // boolean

  console.log(typeof function () {});  //function

  console.log(typeof [1, 'a', true]);  //object
  console.log(typeof { a: 10, b: 20 });  //object
  console.log(typeof null);  //object
  console.log(typeof new Number(10));  //object
}
show();
```

上面有五种（`undefined`，`number`，`string`，`boolean`）属于简单的值类型（**基本类型**），不是对象。剩下的集中情况——函数、数组、对象、new Number(10)是对象，都是**引用类型**。

> 这里需要特别注意的是：虽然`typeof Null`的返回的值是Object，但是Null不属于对象，而是一种基本数据类型。

值类型的类型判断用`typeof`，而引用类型的类型判断用`instanceof`

```js
var fn = function () { };
console.log(fn instanceof Object);  // true
```

