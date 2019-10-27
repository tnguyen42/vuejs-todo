<template>
	<div>
		<!-- JavaScript expressions in Vue are enclosed in double curly brackets. -->
		<p>Completed Tasks: {{todos.filter(todo => {return todo.done === true}).length}}</p>
		<p>Pending Tasks: {{todos.filter(todo => {return todo.done === false}).length}}</p>
		<todo
			v-on:complete-todo="completeTodo"
			v-on:delete-todo="deleteTodo"
			v-for="todo in todos"
			v-bind:todo="todo"
		></todo>
	</div>
</template>

<script type = "text/javascript" >
import Todo from './Todo'
export default {
	props: ["todos"],
	components: {
		Todo
	},
	methods: {
		/**
		 * Delete the designated todo
		 * @param {object} todo The todo to be deleted
		 */
		deleteTodo (todo) {
			const todoIndex = this.todos.indexOf(todo)
			this.todos.splice(todoIndex, 1)
		},
		/**
		 * Mark the designated todo as Completed
		 * @param {object} todo The todo to be marked as completed
		 */
		completeTodo (todo) {
			const todoIndex = this.todos.indexOf(todo)
			this.todos[todoIndex].done = true
		}
	}
}
</script>

<style>
</style>
