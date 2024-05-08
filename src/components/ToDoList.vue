<script setup>
import { ref, computed } from "vue";

// give each todo a uniqure id
let id = 0;

const hideCompleted = ref(false);

const newTodo = ref("");
const todos = ref([
  { id: id++, text: "ABC", done: false },
  { id: id++, text: "DEF", done: true },
  { id: id++, text: "GHI", done: false },
  { id: id++, text: "JKL", done: false },
]);

const filteredTodos = computed(() => {
  return hideCompleted.value ? todos.value.filter((t) => !t.done) : todos.value;
});

function addTodo() {
  todos.value.push({ id: id++, text: newTodo.value, done: false });
  newTodo.value = "";
}

function removeTodo(todo) {
  todos.value = todos.value.filter((t) => t !== todo);
}
</script>
https://vuejs.org/tutorial/#step-9
<template>
  <h1>To Do List</h1>
  <form @submit.prevent="addTodo">
    <input v-model="newTodo" required placeholder="New Todo" />
    <button class="add">Add Todo</button>
  </form>
  <ul>
    <li v-for="todo in filteredTodos" :key="todo.id">
      <input type="checkbox" v-model="todo.done" />
      <span :class="{ done: todo.done }">{{ todo.text }}</span>
      <button @click="removeTodo(todo)" class="remove">X</button>
    </li>
  </ul>
  <section>
    <button @click="hideCompleted = !hideCompleted">
      {{ hideCompleted ? "Show all" : "Hide completed" }}
    </button>
  </section>
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
.done {
  text-decoration: line-through;
}
</style>