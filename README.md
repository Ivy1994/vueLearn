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
.stop
.prevent
.capture
.self
.once
.passive
<a v-on:click.stop.prevent="doThat"></a>
按键修饰符
鼠标按钮修饰符
2.2.0 新增

.left
.right
.middle

v-model 修饰符
.lazy
.number
如果想自动将用户的输入值转为数值类型
.trim
如果要自动过滤用户输入的首尾空白字符，可以给 v-model 添加 trim 修饰符：

************************
# VUE3

### Vue.js 添加到项目的方式
1. CDN 包的形式导入 
	```js
	<script src="https://unpkg.com/vue@next"></script>
	```
2. 下载并自托管
3. npm
	```
	# 最新稳定版本
	npm install vue@next
	# 单文件组件的配套工具
	npm install -D @vue/compiler-sfc
	```
3. 命令行工具（CLI） (* 推荐)
为单页面应用（SPA）快速搭建繁杂的脚手架
	```
	# 安装最新版本的 cli
	npm install -g @vue/cli
	# 在 VUE 项目中运行
	vue upgrade --next
	```
5.  Vite
	web 开发构建工具，通过在终端运行以下命令，可以快速构建 vue 项目
	```
	npm init vite@latest \<project-name\> --template vue
	cd \<project-name\>
	npm install
	npm run dev

### 介绍
1. 声明式渲染
	* v-bind: 绑定属性
	```
	<span v-bind:title="message">
	    鼠标悬停几秒钟查看此处动态绑定的提示信息！
	</span>
	```
	
2. 处理用户输入
	* v-on: 添加事件监听
	* v-model 表单输入和应用状态之间的双向绑定
3. 条件与循环
	* v-if
	* v-for

### 应用和组件实例
1. 组件实例 property
	* data
	* methods
	* props
	* computed
	* inject
	* setup
2. 生命周期钩子
	* beforeCreate
	* created
	* beforeMount
	* mounted
	* beforeUpdate
	* updated
	* beforeUnmont
	* unmonted

### 模板语法
1. 插值
	* 文本： Mustache（双大括号）
	```
	span>Message: {{ msg }}</span>
	```
	* Attribute : 使用 v-bind 指令绑定
	* 原生 HTML： v-html	
	* 使用 JavaScript 表达式
2. 指令 （Directives）
	Directives 是带有 v- 前缀的特殊 attribute, 指令 attribute 的值预期是单个 JavaScript 表达式.
	* 指令的职责是当表达式的值改变时，将其产生的连带响应，响应式的左右于 DOM
	* 一些指令可以接收一个参数，在指令名称之后以冒号表示
	* 动态参数
		```
		<a v-bind:[attributeName]="url"> ... </a>
		```
	* 修饰符（modifier）: 用半角句号.指明特殊的后缀
		```
		<form v-on:submit.prevent="onSubmit">...</form>
		```
	* 缩写：v-bind 缩写(:) v-on 缩写（@）
	
### Data Property 方法和方法
1. data 选项是一个函数，返回一个对象，并以 $data 的形式存储在组件实例中
	* Vue 使用 $ 前缀通过组件实例暴露自己的内置 API。它还为内部 property 保留 _ 前缀。你应该避免使用这两个字符开头的顶级 data property 名称。

2. 方法：我们用 methods 选项向组件实例添加方法，他是一个对象
***************************
### 单文件组件
Vue 单文件组件：也叫 .vue 文件，缩写 SFC, 他允许将 VUE 组件的模板逻辑与样式封装在单个文件中

* SFC 示例
```
<script>
export default {
	data() {
		return {
			greeting: 'Hello World'
		}
	}
}
</script>
<template>
	<p class="greeting">{{greeting}}</p>
</template>
<style>
	.greeting {
		color: red;
		font-weight: bold
	}
<style>
```
