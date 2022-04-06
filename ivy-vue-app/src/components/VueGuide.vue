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
			<input v-model="messge" />
		</p>
	</div>
	<div>
		<form @submit.prevent="addToDoItem">
			<lable>Add a todo</lable>
			<input v-model="todoText" />
			<button>Add</button>
		</form>
		<ul>
			<ToDoItem v-for="(todo, index) in todos" :title="todo.title" @remove="todos.splice(index, 1)"></ToDoItem>
		</ul>

	</div>
</template>

<script>
	
	import ToDoItem from './ToDoItem.vue'
	export default {
		components: {
		    ToDoItem
		  },
		data() {
			return {
				count: 0,
				messge: 'You loaded this page on ' + new Date().toLocaleString(),
				author: {
					name: "John Doe",
					books: [
						"VUE1 - Advanced GUide",
						"VUE3 - Basic GUide",
						"Vue 4 - The Mystery"
					]
				},
				todoText: "",
				todos: [{
						id: 1,
						title: 'Do the dishes'
					},
					{
						id: 2,
						title: 'Take out the trash'
					},
					{
						id: 3,
						title: 'Mow the lawn'
					}
				]
			}
		},
		computed: {
			publishedBooksMessage() {
				return this.author.books.length > 0 ? "Yes" : "No"
			},
			fullName: {
				//getter
				get() {
					return this.firstName + "-" + this.lastName;
				},
				//setter
				set(newValue) {
					const names = newValue.split(' ');
					this.firstName = names[0];
					this.lastName = names[names.length - 1]
				}
			}
		},
		created() {
			this.fullName = "Ivy Yu"
		},
		mounted() {},
		methods: {
			reverseMessage() {
				this.messge = this.messge.split('').reverse().join('')
			},
			addToDoItem() {
				let id = this.todos.length;
				this.todos.push({
					id,
					title: this.todoText
				});
				console.log(this.todos)
			}
		}
	}
</script>

<style>
</style>
