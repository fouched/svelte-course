<script>
import TodoList from './lib/TodoList.svelte'
import {v4 as uuid} from "uuid"

let todos = [
	{
		id: uuid(),
		title: 'Todo 1',
		completed: true
	},
	{
		id: uuid(),
		title: 'Todo 2',
		completed: false
	},
	{
		id: uuid(),
		title: 'Todo 3',
		completed: true
	},
]

function handleAddTodo(event) {
	todos = [...todos, {
		id: uuid(),
		title: event.detail.title,
		completed: false
	}]
}

function handleRemoveTodo(event) {
	todos = todos.filter(t => t.id !== event.detail.id)
}

function handleToggleTodo(event) {
	todos = todos.map((t) => {
		if (t.id === event.detail.id) {
			return {...t, completed: event.detail.value}
		}
		return { ...t }
	})	
}
</script>

<h2>{todos.length} Todos</h2>
<TodoList {todos} 
	on:addtodo={handleAddTodo}
	on:removetodo={handleRemoveTodo}	
	on:toggletodo={handleToggleTodo}
/>

<style>

</style>
