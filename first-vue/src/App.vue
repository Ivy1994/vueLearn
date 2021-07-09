<template>
  <div id="app">
    <img src="./assets/logo.png">
    <h1>{{ msg }}</h1>
    <input v-model="msg" />
    <br />
    <span v-bind:title="message">
      鼠标悬停几秒钟查看此处动态绑定的提示信息！
    </span>
    <p v-if="seen">现在你看到我了。。。</p>
    <ol v-for="todo in todos">
      <li>{{todo.text}}</li>
    </ol>
    <button v-on:click="reverseMessage">反转消息</button>
    <firstcomponent></firstcomponent>
  </div>
</template>

<script>
import firstcomponent from './component/firstcomponent.vue'
export default {
  name: 'app',
  data () {
    return {
      msg: 'Welcome to Your Vue.js App',
      message: '页面加载于 ' + new Date().toLocaleString(),
      seen: true,
      todos: [
        {text: '学习 JS'},
        {text: '学习 Vue' },
        {text: '整个牛项目'},
      ]
    }
  },
  methods: {
    reverseMessage: function (){
       this.message = this.msg.split('').reverse().join('')
    }
  },
  components: { firstcomponent }
}
</script>

<style>
#app {
  font-family: 'Avenir', Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}

h1, h2 {
  font-weight: normal;
}

ul {
  list-style-type: none;
  padding: 0;
}

li {
  display: inline-block;
  margin: 0 10px;
}

a {
  color: #42b983;
}
</style>
