<script>
  export let todos;
  export let removeTodo;
</script>

<ul>
  {#each todos as todo (todo.id)}
  <li class:completed='{todo.completed}'>
    <label><input type="checkbox" bind:checked='{todo.completed}' />{todo.text}</label>
    <button on:click|preventDefault={removeTodo(todo.id)}>&times;</button>
  </li>
  {/each}
</ul>

<style>
  .completed {
    text-decoration: line-through;
  }
</style>
