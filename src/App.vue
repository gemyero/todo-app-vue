<template>
  <todo-app></todo-app>
</template>

<script>
import TodoApp from "./components/TodoApp.vue";

export default {
  name: "App",
  components: {
    TodoApp
  }
};
</script>

<style>
  * {
    margin: 0;
    padding: 0;
    box-sizing: border-box;
  }

  body {
    background-color: #D3D3D3;
    font-family: Helvetica, Arial, sans-serif;
  }

  html {
    font-size: 10px;
  }
</style>
