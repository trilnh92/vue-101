<script setup>
import { ref } from "vue";

defineProps({
  msg: String,
  name: String,
});

const className = ref(false);
const input = ref(null);

function handleClick() {
  className.value = !className.value;
  input.value.focus();
}
</script>

<template>
  <h1>{{ msg }}</h1>
  <input type="text" ref="input" :class="className ? 'active' : ''" />
  <button @click="handleClick">Click Me</button>
</template>

<style scoped>
input.active {
  border: 3px solid red;
}
</style>