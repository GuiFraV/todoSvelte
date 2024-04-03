<script>
  let todos = [];
  let newTodo = '';

  function addTodo() {
    if (newTodo.trim().length > 0) {
      todos = [...todos, { text: newTodo.trim(), completed: false }];
      newTodo = '';
    }
  }

  function toggleTodo(index) {
    todos[index].completed = !todos[index].completed;
  }

  function removeTodo(index) {
    todos.splice(index, 1);
    todos = todos;
  }
</script>

<div class="todos">
  <h1>Svelte Todo List</h1>

  <form on:submit|preventDefault={addTodo}>
    <input type="text" bind:value={newTodo} placeholder="Enter a new todo">
    <button type="submit">Add</button>
  </form>

  <ul>
    {#each todos as todo, index}
      <li class:completed={todo.completed}>
        <span on:click={() => toggleTodo(index)}>{todo.text}</span>
        <button on:click={() => removeTodo(index)}>Remove</button>
      </li>
    {/each}
  </ul>
</div>