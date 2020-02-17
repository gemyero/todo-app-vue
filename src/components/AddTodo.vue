<template>
  <form @submit.prevent="handleSubmit" class="add-todo">
    <input type="text" placeholder="Enter Todo Text..." v-model="todoText" class="add-todo_input" />
    <input type="submit" value="Add Todo" class="add-todo_button"/>
  </form>
</template>

<script>
export default {
  name: "add-todo",
  data() {
    return {
      todoText: ""
    };
  },
  methods: {
    handleSubmit() {
      this.$emit("add-todo", this.todoText);
      this.todoText = "";
    }
  }
};
</script>

<style scoped>
.add-todo {
  display: flex;
  justify-content: center;
}

.add-todo_input {
  padding: 1rem;
  margin-right: 1rem;
  flex-grow: 1;
  font-size: 2em;
}

.add-todo_button {
  background-color: blue;
  outline: none;
  border: none;
  color: white;
  font-size: 2em;
  padding: 0.5em;
  border-radius: 5px;
}
</style>