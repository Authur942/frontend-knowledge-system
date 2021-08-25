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

