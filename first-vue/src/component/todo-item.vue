<template>
  <div id = 'todo-list-example'>
    <form>
      <label for="new-todo">Add a todo</label>
      <input
        v-model="newTodoText"
        id="new-todo"
        placeholder="E.g. Feed the cat"/>
      <button>Add</button>
    </form>
    <ul>
      <li></li>
    </ul>
  </div>
</template>

<script>
  export default {
    name: "todo-list-example",
    data(): {
      return {}
    }
  }
</script>

<style>
</style>
