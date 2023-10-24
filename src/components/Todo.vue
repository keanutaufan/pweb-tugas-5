<script setup>
	import { ref } from "vue";
	const newTodo = ref("");
	let id = 0;

	const todos = ref([
		{ id: id++, text: 'Lorem', done: true },
		{ id: id++, text: 'Ipsum', done: true },
		{ id: id++, text: 'Dolor sit amet', done: false }
	]);

	function addTodo() {
		if (!newTodo.value) return;
		todos.value.push({ text: newTodo.value, done: false })
		newTodo.value = ''
	}

	function deleteTodo(todo) {
		todos.value = todos.value.filter(t => t !== todo);
	}
</script>

<template>
	<main>
		<form @submit.prevent="addTodo">
			<input v-model="newTodo">
			<button>Add Todo</button>
		</form>
		<ul>
			<li v-for="todo in todos" :key="todo.id">
				<span :class="{ done: todo.done }" @click="todo.done = !todo.done">{{ todo.text }}</span>
				<span class="delete" @click="deleteTodo(todo)"> x</span>
			</li>
		</ul>
	</main>
</template>

<style scoped>
	main {
		padding: 1rem;
		display: flex;
		flex-direction: column;
		gap: 1rem;
	}

	form {
		display: flex;
		gap: 1rem;
	}

	.done {
		text-decoration: line-through;
	}

	.delete {
		color: rgb(247, 42, 42);
		cursor: pointer;
	}

	input {
    height: 2.4rem;
    font-size: 1rem;
    border-radius: 8px;
    outline: none;
    border: 2px solid gray;
    color: white;
    background: rgba(0, 0, 0, 0.1);
    padding: 4px 10px;
  }

	input:focus {
		border: 2px solid #327959;
    transition: all 500ms ease;
	}

	button {
		height: 2.4rem;
		font-size: 1rem;
		border-radius: 8px;
		outline: none;
		border: 2px solid #327959;
		background: transparent;
		color: gray;
	}

	button:active {
		border-width: 3px;
	}

</style>