<script lang="typescript">
  import Todo from "./Todo.svelte";

  type TodoItem = { name: string };
  export let todos: TodoItem[] = [];
</script>

<main>
  {#each todos as todo (todo.name)}
    <Todo name={todo.name} on:deleteTodo />
  {/each}
</main>
