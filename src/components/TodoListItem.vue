<template>
  <div class="todo-item">
    <input class="list-item_toggle" type="checkbox" v-model="todo.completed" />
    <span class="list-item_text">{{todo.text}}</span>
    <button class="list-item_remove" @click="$emit('delete-todo')">remove</button>
  </div>
</template>

<script>
export default {
  name: "todo-list-item",
  props: ["todo"]
};
</script>

<style scoped>
.todo-item {
  margin-top: 1rem;
  display: flex;
  align-items: baseline;
}

.list-item_text {
  margin-right: auto;
  font-size: 2em;
}

.list-item_toggle {
  margin-right: 1rem;
  transform: scale(1.5);
}

.list-item_remove {
  border: none;
  outline: none;
  background-color: red;
  color: white;
  padding: 1rem;
  font-size: 2rem;
  border-radius: 5px;
}
</style>
