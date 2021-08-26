<script lang="ts">
  import { createEventDispatcher } from "svelte";
  import { fade } from "svelte/transition";

  const dispatch = createEventDispatcher();

  export let name: string;
  export let done: boolean;
</script>

<div class="todo" class:done transition:fade>
  <span>{name}</span>
  <div class="actions">
    <span on:click={() => dispatch("doneTodo", { name })}>&checkmark;</span>
    <span on:click={() => dispatch("deleteTodo", { name })}>&Cross;</span>
  </div>
</div>

<style>
  .todo {
    display: flex;
    justify-content: space-between;
    padding: 8px 16px;
    border: 1px solid #efefef;
  }

  .todo span {
    cursor: pointer;
  }

  .actions {
    display: flex;
    gap: 24px;
  }

  .done {
    background-color: aqua;
  }
</style>
