# vue基础
1. vue 有三个常用标签:
- ```<template></template>```
- ```<script></script>```
- ```<style></style>```
2. 获得一个数组的拷贝----两种方法
- slice方法
- es6展开运算符（...）
3. 传递属性
- 需要在父组件中定义属性
- 在子组件中定义 props:['属性名']
4. 简写形式
- 'v-bind' 等价于 ':'
- 'v-on' 等价于 '@'
***
# vue-router
1. 先在main.js文件中导入router-------import router from "./router";
2. 然后在main.js文件下的new Vue中添加router
```js
new Vue({
  el: '#app',
  router,
  template: '<App/>',
  components: { App }
})
```
3.在src文件夹下新建router.js文件
```js
import Vue from 'vue'
import Router from 'vue-router'
import Home from '@/components/Home'
import Post from '@/components/Post'

Vue.use(Router)

export default new Router({
  routes: [
    {
      path: '/',
      component: Home
    },
    {
      path: '/post',
      component: Post
    }
  ]
})

```
4. 在components文件夹下创建 Home.vue 和 Post.vue
5. 在app.vue 文件根标签下添加 标签
- ```<router-view></router-view>```
