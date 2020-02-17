<template>
  <div class="todo-list">
    <h3 class="todo-list-completed_title" v-if="isCompletedList">Completed Todos</h3>
    <todo-list-item v-for="todo in todos" :key="todo.id" :todo="todo" @delete-todo="deleteTodo(todo.id)"></todo-list-item>
  </div>
</template>

<script>
import TodoListItem from "./TodoListItem.vue";

export default {
  name: "todo-list",
  components: {
    TodoListItem
  },
  computed: {
    isCompletedList() {
      return this.todos.every(todo => todo.completed);
    }
  },
  props: ['todos', 'deleteTodo']
};
</script>

<style scoped>
  .todo-list {
    margin-top: 2rem;
    padding: 2rem;
  }

  .todo-list-completed_title {
    font-size: 2rem;
  }
</style>