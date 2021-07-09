## 20210708
1. 学习 VUE， 开发环境搭建 and 项目启动吧、
安装webpack
cnpm install webpack -g
安装vue脚手架
npm install vue-cli -g
根据模板创建项目
vue init webpack-simple 工程名字<工程名字不能用中文>
安装项目依赖
npm install
安装 vue 路由模块vue-router和网络请求模块vue-resource
cnpm install vue-router vue-resource --save
启动项目
npm run dev

localhost:8080

v-html
Mustache 语法不能作用在 HTML attribute 上，遇到这种情况应该使用 v-bind 指令
指令
<p v-if="seen">现在你看到我了</p>
<a v-bind:href="url">...</a>
<a v-on:click="doSomething">...</a>
修饰符
<form v-on:submit.prevent="onSubmit">...</form>

对于任何复杂逻辑，你都应当使用计算属性。
computed
computed: {
    // 计算属性的 getter
    reversedMessage: function () {
      // `this` 指向 vm 实例
      return this.message.split('').reverse().join('')
    }
	}
我们可以将同一函数定义为一个方法而不是一个计算属性。两种方式的最终结果确实是完全相同的。
然而，不同的是计算属性是基于它们的响应式依赖进行缓存的。
只在相关响应式依赖发生改变时它们才会重新求值。
这就意味着只要 message 还没有发生改变，多次访问 reversedMessage 计算属性会立即返回之前的计算结果，而不必再次执行函数。
计算属性的 setter

侦听器
Vue 通过 watch 选项提供了一个更通用的方法，来响应数据的变化。当需要在数据变化时执行异步或开销较大的操作时，这个方式是最有用的。

因此，如果需要非常频繁地切换，则使用 v-show 较好；如果在运行时条件很少改变，则使用 v-if 较好。
当 v-if 与 v-for 一起使用时，v-for 具有比 v-if 更高的优先级。

 <li v-for="(item, index) in items">
 你也可以用 of 替代 in 作为分隔符，因为它更接近 JavaScript 迭代器的语法：
 
v-for对象
<div v-for="(value, name, index) in object">
  {{ name }}: {{ value }}
</div>

v-for 也可以接受整数。在这种情况下，它会把模板重复对应次数。
监听事件
v-on:click
内联处理器中的方法

事件修饰符


