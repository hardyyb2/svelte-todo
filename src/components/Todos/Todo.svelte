<script lang="ts">
  import { createEventDispatcher } from "svelte";
  const dispatch = createEventDispatcher();

  export let name: string;
</script>

<div class="todo">
  <span>{name}</span>
  <span on:click={() => dispatch("deleteTodo", { name })}>&Cross;</span>
</div>

<style>
  .todo {
    display: flex;
    justify-content: space-between;
    padding: 10px 20px;
    border: 1px solid #efefef;
  }

  .todo > span:last-child {
    cursor: pointer;
  }
</style>
