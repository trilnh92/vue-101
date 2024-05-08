<script setup>
import { ref } from "vue";

// give each todo a uniqure id
let id = 0;

const newTodo = ref("");
const todos = ref([
  { id: id++, text: "ABC" },
  { id: id++, text: "DEF" },
  { id: id++, text: "GHI" },
  { id: id++, text: "JKL" },
]);

function addTodo() {
  todos.value.push({ id: id++, text: newTodo.value });
  newTodo.value = "";
}

function removeTodo(todo) {
  todos.value = todos.value.filter((t) => t !== todo);
}
</script>

<template>
  <h1>To Do List</h1>
  <form @submit.prevent="addTodo">
    <input v-model="newTodo" required placeholder="New Todo" />
    <button class="add">Add Todo</button>
  </form>
  <ul>
    <li v-for="todo in todos" :key="todo.id">
      <span>{{ todo.text }}</span>
      <button @click="removeTodo(todo)" class="remove">X</button>
    </li>
  </ul>
</template>

<style scoped>
input {
  min-height: 45px;
  padding-inline: 10px;
  margin-inline: 10px;
}
ul {
  margin: 0;
  padding: 0;
  list-style-type: none;
}

ul:empty {
  display: none;
}

li {
  padding-top: 30px;
  display: flex;
  justify-content: center;
  align-items: center;
  gap: 30px;
}
button {
  line-height: 40px;
  padding-inline: 20px;
}

button.add {
  background: blue;
}
button.remove {
  background-color: red;
  border-radius: 30px;
}
</style>