<template>
	<div id="app">
		<todo-list v-bind:todos="todos"></todo-list>
		<create-todo v-on:add-todo="addTodo"></create-todo>
	</div>
</template>

<script>
import TodoList from "./components/TodoList";
import CreateTodo from "./components/CreateTodo";

export default {
	name: "App",
	components: {
		TodoList,
		CreateTodo
	},
	data() {
		return {
			todos: [
				{
					title: "Todo A",
					project: "Project A",
					done: false
				},
				{
					title: "Todo B",
					project: "Project B",
					done: true
				},
				{
					title: "Todo C",
					project: "Project C",
					done: false
				},
				{
					title: "Todo D",
					project: "Project D",
					done: false
				}
			]
		};
	},
	methods: {
		/**
		 * Adds a new todo by pushing it to the array todos. By default, the new todo is set as not-completed.
		 * @param {string} title The title of the todo
		 * @param {string} project The project it is associated to
		 */
		addTodo(title, project) {
			this.todos.push({
				title,
				project,
				done: false
			});
		}
	}
};
</script>

<style>
#app {
	font-family: "Avenir", Helvetica, Arial, sans-serif;
	-webkit-font-smoothing: antialiased;
	-moz-osx-font-smoothing: grayscale;
}
</style>
