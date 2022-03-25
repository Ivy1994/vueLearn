<template>
	<div id="count">
		Counter: {{ count }}
	</div>
	<div>
		<span v-bind:title="messge">
			鼠标悬停几秒钟查看此处动态绑定的提示信息！
		</span>
	</div>
	<div>
		<p>{{ messge }}</p>
		<button v-on:click="reverseMessage">反转 message</button>
		<p>
			<input v-model= "messge" />
		</p>
	</div>
</template>

<script >
	export default {
		data() {
			return {
				count: 0,
				messge: 'You loaded this page on ' + new Date().toLocaleString()
			}
		},
		mounted() {},
		methods: {
			reverseMessage() {
				this.messge = this.messge.split('').reverse().join('')
			}
		}
	}
	
</script>

<style>
</style>
