# `Vue`项目总结

## 页面刷新

用户执行完某个动作，改变了某些状态，需要重新刷新页面，以此来重新渲染页面。

1. 原始方法

   `location.reload()`

2. 路由跳转

   `this.$router.go(0)`

用过的人都知道，前两者都是强制刷新页面，会出现短暂的闪烁，用户体验效果不好。

```vue
<template>
    <div id="app">
    	<router-view v-if="isRouterAlive"></router-view>
	</div>
</template>
<script>
    export default {
        name: 'App',
        provide () {    //父组件中通过provide来提供变量，在子组件中通过inject来注入变量。                                       
            return {
                reload: this.reload                                              
            }
        },
        data() {
            return{
                isRouterAlive: true                    //控制视图是否显示的变量
            }
        },
        methods: {
            reload () {
                this.isRouterAlive = false;            //先关闭，
                this.$nextTick(function () {
                    this.isRouterAlive = true;         //再打开
                }) 
            },
            // 在需要刷新页面的代码块中调用：
            finishu() {
                this.reload();
            }
        }，
    }
</script>
```

## 过渡动画

`Vue` 在插入、更新或者移除 DOM 时，提供多种不同方式的应用过渡效果。

- 在` CSS `过渡和动画中自动应用 class

`Vue` 提供了 `transition` 的封装组件，在下列情形中，可以给任何元素和组件添加进入/离开过渡：

- 条件渲染 (使用 `v-if`)
- 条件展示 (使用 `v-show`)
- 动态组件
- 组件根节点

这里是一个典型的例子：

```vue
<div id="demo">
  <button v-on:click="show = !show">
    Toggle
  </button>
  <transition name="fade">
    <p v-if="show">hello</p>
  </transition>
</div>
```

```js
new Vue({
  el: '#demo',
  data: {
    show: true
  }
})
```

```css
.fade-enter-active, .fade-leave-active {
  transition: opacity .5s;
}
.fade-enter, .fade-leave-to /* .fade-leave-active below version 2.1.8 */ {
  opacity: 0;
}
```

`Vue`中有6个过渡名：

1. v-enter
2. v-enter-active
3. v-enter-to
4. v-leave
5. v-leave-active
6. v-leave-to

## 🌋问题场景

**滚动条一定高度时触发事件** (结合防抖)

```js
/**
 * 防抖函数
 * @fn 需要执行的函数
 * @delay 毫秒，防抖期限值
 */
function debounce (fn, delay) {
  let timer = null
  return function () {
    if (timer) {
      clearTimeout(timer)
    }
    timer = setTimeout(fn, delay)
  }
}

export { debounce }
```

```js
// 在data中定义初始化数据  
data() {
  return {
    scrollTopNum: "", // 页面滚动的高度
    tabshow: false, // 是否进行某种操作
  };
},
  
// 在生命周期中添加滚动事件  
mounted() {
  // 让滚动进行
  window.addEventListener("scroll", debounce(this.handleScroll, 100), true);
},
  
// 获取页面滚动的高度  
methods: {
  handleScroll() {
    let top =
        document.documentElement.scrollTop ||
        document.body.scrollTop ||
        window.pageYOffset;
    this.scrollTopNum = top;
  }
}

// 监听页面滚动的距离,当达到一定距离时,触发某个操作
watch: {
  scrollTopNum: function () {
    if (this.scrollTopNum > 45) {
      this.tabshow = true;
    } else {
      this.tabshow = false;
    }
  },
},
```

## prettier

```js
{
    // 使能每一种语言默认格式化规则
    "[html]": {
        "editor.defaultFormatter": "esbenp.prettier-vscode"
    },
    "[css]": {
        "editor.defaultFormatter": "esbenp.prettier-vscode"
    },
    "[less]": {
        "editor.defaultFormatter": "esbenp.prettier-vscode"
    },
    "[javascript]": {
        "editor.defaultFormatter": "esbenp.prettier-vscode"
    },

    /*  prettier的配置 */
    "prettier.printWidth": 100, // 超过最大值换行
    "prettier.tabWidth": 4, // 缩进字节数
    "prettier.useTabs": false, // 缩进不使用tab，使用空格
    "prettier.semi": true, // 句尾添加分号
    "prettier.singleQuote": true, // 使用单引号代替双引号
    "prettier.proseWrap": "preserve", // 默认值。因为使用了一些折行敏感型的渲染器（如GitHub comment）而按照markdown文本样式进行折行
    "prettier.arrowParens": "avoid", //  (x) => {} 箭头函数参数只有一个时是否要有小括号。avoid：省略括号
    "prettier.bracketSpacing": true, // 在对象，数组括号与文字之间加空格 "{ foo: bar }"
    "prettier.disableLanguages": ["vue"], // 不格式化vue文件，vue文件的格式化单独设置
    "prettier.endOfLine": "auto", // 结尾是 \n \r \n\r auto
    "prettier.eslintIntegration": false, //不让prettier使用eslint的代码格式进行校验
    "prettier.htmlWhitespaceSensitivity": "ignore",
    "prettier.ignorePath": ".prettierignore", // 不使用prettier格式化的文件填写在项目的.prettierignore文件中
    "prettier.jsxBracketSameLine": false, // 在jsx中把'>' 是否单独放一行
    "prettier.jsxSingleQuote": false, // 在jsx中使用单引号代替双引号
    "prettier.parser": "babylon", // 格式化的解析器，默认是babylon
    "prettier.requireConfig": false, // Require a 'prettierconfig' to format prettier
    "prettier.stylelintIntegration": false, //不让prettier使用stylelint的代码格式进行校验
    "prettier.trailingComma": "es5", // 在对象或数组最后一个元素后面是否加逗号（在ES5中加尾逗号）
    "prettier.tslintIntegration": false // 不让prettier使用tslint的代码格式进行校验
}
```









