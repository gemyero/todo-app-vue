<template>
  <div class="todo-app">
    <h1 class="todo-app_title">Todo App</h1>
    <add-todo @add-todo="addTodo"></add-todo>
    <todo-list v-if="inCompletedTodos.length" :todos="inCompletedTodos" :deleteTodo="deleteTodo"></todo-list>
    <todo-list v-if="completedTodos.length" :todos="completedTodos" :deleteTodo="deleteTodo"></todo-list>
  </div>
</template>

<script>
import uniqid from "uniqid";

import AddTodo from "./AddTodo.vue";
import TodoList from "./TodoList.vue";

export default {
  name: "todo-app",
  components: {
    AddTodo,
    TodoList
  },
  data() {
    return {
      todos: JSON.parse(localStorage.getItem("todos")) || []
    };
  },
  computed: {
    inCompletedTodos() {
      return this.todos.filter(todo => !todo.completed);
    },
    completedTodos() {
      return this.todos.filter(todo => todo.completed);
    }
  },
  methods: {
    addTodo(todoText) {
      const todo = {
        id: uniqid(),
        text: todoText,
        completed: false
      };

      this.todos.push(todo);
    },
    deleteTodo(todoId) {
      this.todos = this.todos.filter(todo => todo.id !== todoId);
    }
  },
  watch: {
    todos: {
      handler(newTodos) {
        console.log(newTodos);
        localStorage.setItem("todos", JSON.stringify(newTodos));
      },
      deep: true
    }
  }
};
</script>

<style scoped>
.todo-app {
  background-color: white;
  border-radius: 10px;
  box-shadow: 5px 5px 20px #999;
  padding: 3rem;
  margin: 4rem auto;
  width: 70rem;
}

.todo-app_title {
  font-size: 5rem;
  margin: 1rem 0 5rem;
  text-align: center;
}
</style>