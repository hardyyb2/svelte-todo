<script lang="typescript">
  import Todo from "./Todo.svelte";

  export let todos = [];
</script>

<main>
  {#each todos as todo (todo.name)}
    <Todo name={todo.name} done={todo.done} on:deleteTodo on:doneTodo />
  {/each}
</main>
