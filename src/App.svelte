<script>
	import TodoListItems from './TodoListItems.svelte'
	import AddTodoForm from './AddTodoForm.svelte';
	export let name;
  let todos = [
    { id: 1, text: 'Walk the dog', completed: false },
    { id: 2, text: 'Mop the floor', completed: true },
  ]

	function addTodo(text) {
		const id = Math.max(...todos.map(({ id }) => id)) + 1;
		todos = [...todos, { id, text, completed: false }]
	}

	function removeTodo(id) {
		const index = todos.findIndex(todo => todo.id === id)
		todos.splice(index, 1);
		todos = todos;
	}

</script>

<main>
	<h1>{name}'s Todo List!</h1>
	<TodoListItems {todos} {removeTodo} />
	<AddTodoForm {addTodo} />
</main>

<style>
	main {
		padding: 1em;
		max-width: 40em;
		margin: 0 auto;
	}

	h1 {
		color: #ff3e00;
		text-transform: uppercase;
		font-size: 4em;
		font-weight: 100;
	}

	/* @media (min-width: 640px) {
		main {
			max-width: none;
		}
	} */
</style>
