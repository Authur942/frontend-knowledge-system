# `Vue`项目总结

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
            // 在需要刷新页面的代码块中使用：
            finishu() {
                this.reload();
            }
        }，
    }
</script>
```



