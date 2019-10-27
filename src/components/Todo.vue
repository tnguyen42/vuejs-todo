<template>
	<div class="ui centered card">
		<div class="content">
			<div class="header">{{ todo.title }}</div>
			<div class="meta">{{ todo.project }}</div>
			<div class="extra content">
				<span class="right floated edit icon" v-on:click="showForm">
					<i class="edit icon"></i>
				</span>
				<span class="right floated trash icon" v-on:click="deleteTodo(todo)">
					<i class="trash icon"></i>
				</span>
			</div>
		</div>
		<!-- form is visible when we are in editing mode -->
		<div class="content" v-show="isEditing">
			<div class="ui form">
				<div class="field">
					<label>Title</label>
					<input type="text" v-model="todo.title" />
				</div>
				<div class="field">
					<label>Project</label>
					<input type="text" v-model="todo.project" />
				</div>
				<div class="ui two button attached buttons">
					<button class="ui basic blue button" v-on:click="hideForm">Close X</button>
				</div>
			</div>
		</div>
		<div class="ui bottom attached green basic button" v-show="todo.done">Completed</div>
		<div
			class="ui bottom attached red basic button"
			v-show="!todo.done"
			v-on:click="completeTodo(todo)"
		>Complete</div>
	</div>
</template>

<script type = "text/javascript" >
export default {
	props: ['todo'],
	data () {
		return {
			isEditing: false
		}
	},
	methods: {
		/**
		 * Open the form in the UI
		 */
		showForm () {
			this.isEditing = true
		},
		/**
		 * Closes the form in the UI
		 */
		hideForm () {
			this.isEditing = false
		},
		/**
		 * Refers the todo reference to its parent component for deletion
		 * @param {object} todo The todo to be deleted
		 */
		deleteTodo (todo) {
			console.log(todo)
			this.$emit('delete-todo', todo)
		},
		/**
		 * Refers the todo reference to its parent component to mark the todo as completed
		 * @param {object} todo The todo to be marked as completed
		 */
		completeTodo (todo) {
			console.log(todo)
			this.$emit('complete-todo', todo)
		}
	}
}
</script>
