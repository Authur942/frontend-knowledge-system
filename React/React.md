# React（用于构建用户界面的JavaScript库）

> `React`是一个将数据渲染为HTML视图的开源JavaScript库

## React 的特点：

1. 采用组件化开发模式，使用**声明式**编程，而不是**命令式**编程，提高了开发效率以及组件的复用率。
2. 在`React Native`中可以使用`React`进行移动端 `Android` 和 `ios` 应用的开发。
3. 使用虚拟DOM+`diffing`算法，尽量减少与真实DOM的交互。

```html
<!-- 引入react核心库 -->
<script src="https://unpkg.com/react@16/umd/react.development.js" crossorigin></script>
<!-- 引入react-dom用于支持react操作dom -->
<script src="https://unpkg.com/react-dom@16/umd/react-dom.development.js" crossorigin></script>
<!-- 引入Babel，用于jsx转换成js -->
<script src="https://unpkg.com/babel-standalone@6/babel.min.js"></script>

<!-- 在使用JSX方式创建虚拟DOM时，必须加上type="text/babel" -->
<script type="text/babel"></script> 
```

## 虚拟DOM

虚拟DOM的本质就是 `Object `类型的一般对象。

虚拟DOM比较`轻`，真实DOM比较`重`，虚拟DOM是React内部使用的DOM。

## JSX（JavaScript + XML）

> **XML**是早期时一种用于存储和传输数据的文件格式 如今被**JSON**代替

```xml
<student>
    <name>Tom</name>
    <age>19</age>
</student>
```

```json
"{
	"name": "tom",
	"age": "18"
}"
```

### 创建虚拟DOM的两种方式

1. JSX

   ```jsx
   // const VDOM = <h1>hello react</h1>
   // 在h1标签里面嵌套span标签
   
   const VDOM = (
     <h1 id="title">
     <span class="dom">hello react</span>
     </h1>
   )
   ReactDOM.render(VDOM, document.getElementById('app'))
   
   // -----------分割线----------------
   
   // babel将JSX语法转换成浏览器可识别的JS
   const VDOM = (
     <h1 id="title">
     <span class="dom">hello react</span>
     </h1>
   )
   // 等价于
   const VDOM = React.createElement('h1', { id: 'title' }, React.createElement('span', { className : 'dom' }, 'hello world'))
   ```

2. JavaScript

   > 采用JavaScript方式创建虚拟DOM时不需要用到Babel转换，因为未使用到JSX语法。

   ```js
   // JavaScript的方式
   
   // const VDOM = React.createElement('h1', {id : 'title'}, 'hello world')
   // 在h1标签里面嵌套span标签
   const VDOM = React.createElement('h1', { id: 'title' }, React.createElement('span', { className : 'dom' }, 'hello world'))
   
   ReactDOM.render(VDOM, document.getElementById('app'))
   ```

### JSX语法规则

1. 定义虚拟DOM时*不加双引号*。
2. 样式的类名指定不要用`class`，而是用`className`。
3. 内联样式，需要用花括号**键值**表达的形式去写，在遇到双单词的属性需要使用**驼峰命名法。**
4. 标签中混入`JS表达式`时，需要使用**花括号**。
5. 只有一个根标签。
6. 标签必须闭合
7. 标签首字母
   1. 若是小写字母开头，则将标签转为HTML的同名元素，若HTML中无同名元素，则报错。
   2. 若是大写字母开头，则将标签转化为虚拟DOM组件，React就去渲染对应的组件，若组件未定义，则报错。

```css
.wrap {
  background-color: orange;
}
#title {
  color: #fff;
}
```

```jsx
const myId = 'title'
const myClass = 'wrap'
const VDOM = ( // 定义虚拟DOM时不加双引号。
  // 样式的类名指定不要用class，而是用className
  <div className={myClass}> // 标签中混入JS表达式时，需要使用花括号。
    <h1 id={myId}>
      // 内联样式，需要用花括号键值表达的形式去写，在遇到双单词的属性需要使用驼峰命名法。
      <span style={{ color: 'red', fontSize: '39px'}}>hello react</span>
    </h1>
    <h1 id={myId}>
      <span>hello react</span>
    </h1>
  </div>
  // 只有一个根标签。
)
ReactDOM.render(VDOM, document.getElementById('app'))
```

