<script lang="ts">
  import SearchBar from "./components/SearchBar.svelte";
  import Todos from "./components/Todos/Todos.svelte";

  type TodoItem = { name: string; done: boolean };
  let todos: TodoItem[] = [];

  function handleSubmit(e) {
    let val = e.target?.todo?.value ?? "";
    let alreadyExists = todos.find((todo) => todo.name === val);

    if (alreadyExists) return;

    todos = [...todos, { name: val, done: false }];
    e.target.reset();
  }

  function handleDeleteTodo(e: CustomEvent<{ name: string }>) {
    const todoName = e.detail?.name;
    let newTodos = todos.filter((todo) => todo.name !== todoName);
    todos = newTodos;
  }

  function handleDoneTodo(e: CustomEvent<{ name: string }>) {
    const todoName = e.detail?.name;
    let newTodos = todos.map((todo) => {
      if (todo.name === todoName) {
        todo.done = !todo.done;
      }
      return todo;
    });
    todos = newTodos;
  }
</script>

<main>
  <SearchBar on:submit={handleSubmit} />
  <Todos
    {todos}
    on:deleteTodo={handleDeleteTodo}
    on:doneTodo={handleDoneTodo}
  />
</main>

<style>
  main {
    text-align: center;
    padding: 1em;
    max-width: 240px;
    margin: 0 auto;
  }

  h1 {
    color: #ff3e00;
    text-transform: uppercase;
    font-size: 4em;
    font-weight: 100;
  }

  @media (min-width: 640px) {
    main {
      max-width: none;
    }
  }
</style>
