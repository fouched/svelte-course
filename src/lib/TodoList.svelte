<script>
	import MyButton from './MyButton.svelte'
	import { createEventDispatcher } from 'svelte'

	export let todos = []
	let txtTodo = ''
	const dispatch = createEventDispatcher()

	function handleAddTodo() {
		if (!txtTodo) return

		dispatch('addtodo', {
			title: txtTodo
		})
		txtTodo = ''
	}

	function handleRemoveTodo(id) {
		dispatch('removetodo', {
			id 
		})
	}
</script>
<div class="todo-list-wrapper">
	<ul>
	{#each todos as {id, title, completed} (id)}
		<li>
			<label for="todo">
				<input type="checkbox" name="todo" id="todo" checked={completed}>
			</label>
			{title}
			<button on:click={() => handleRemoveTodo(id)}>Remove</button>
		</li>
	{/each}
	</ul>
	<form class="add-todo-form" on:submit|preventDefault={handleAddTodo}>
		<input type="text" bind:value={txtTodo}>
		<MyButton>Add</MyButton>
	</form>
</div>
