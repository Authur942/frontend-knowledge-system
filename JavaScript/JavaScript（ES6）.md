# JavaScript（ES6）

## 变量的解构赋值

```js
let [a, b, c] = ['a','b',2]
console.log(a, b, c) // a b 2

let [a, b, c] = [1,2]
console.log(a, b, c) // 1 2 undefined

let [a, b, c] = [1,[2,3],4]
console.log(a, b, c) // 1 [2, 3] 4

let [a, [b], c] = [1,[2,3],4]
console.log(a, b, c) // 1 2 4

let [a, b, c] = [true, false, 2]
console.log(a, b, c) // true false 2

let [x, y, z] = []
console.log(x, y, z) // undefined undefined undefined

// 对于Set() 结构来说 赋予变量的值不宜重复
let [x, y, z] = new Set([1,1,1])
console.log(x, y, z) // 1 undefined undefined

let [x, y, z] = new Set([1,1,3])
console.log(x, y, z) // 1 3 undefined

let [x, y, z] = [1,1,3]
console.log(x, y, z) // 1 1 3
```

