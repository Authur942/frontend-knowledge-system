# Vue 2.0

## 条件渲染

`v-for` 指令可以循环遍历渲染数组和对象，都可传三个参数，数组`（value/index/key）` ，对象 `(value/name/index)`

```html
<ul id="example-1">
  <li v-for="item in items" :key="item.message">
    {{ item.message }}
  </li>
</ul>
```

```js
var example1 = new Vue({
  el: '#example-1',
  data: {
    items: [
      { message: 'Foo' },
      { message: 'Bar' }
    ]
  }
})
```

可以用 `of` 替代 `in` 作为分隔符

```html
<div v-for="item of items"></div>
```

遍历一个对象

```html
<ul id="v-for-object" class="demo">
  <li v-for="value in object">
    {{ value }}
  </li>
</ul>
```

```js
new Vue({
  el: '#v-for-object',
  data: {
    object: {
      title: 'How to do lists in Vue',
      author: 'Jane Doe',
      publishedAt: '2016-04-10'
    }
  }
})
```

结果：

- How to do lists in Vue
- Jane Doe
- 2016-04-10

### 假想

> ant design vue UI框架中的表格，表格头用遍历对象的形式进行渲染，表格体亦是如此

```vue
// code模板
<a-table
	bordered
	:scroll="{ y: 400, x: 300 }"
	:loading="loading"
	:row-selection="{
		selectedRowKeys: selectedRowKeys,
		onChange: onSelectChange,
	}"
	:columns="columns"
	:data-source="currentData"
	:pagination="paginationProps"
	:row-key="
		(record, index) => {
     return index;
	}"
>
</a-table>
```

```js
columns = [
  {
    title: '题名',
    dataIndex: 'title',
    key: 'title',
    width: '30%',
    ellipsis: true
  },
  {
    title: '条码号',
    dataIndex: 'barcode',
    key: 'barcode',
    width: '20%',
    ellipsis: true
  },
]
```

```vue

```

