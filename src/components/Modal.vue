<script setup>
import { ref } from 'vue'

defineProps({
  msg: String,
  name: String
})

// const name = ref("active");

function handleClick() {
    console.log(this.$refs.name);
    this.$refs.name.classList.add('active');
}

</script>

<template>
<h1>{{ msg }}</h1>
<input type="text" ref="name" />
<button @click="handleClick">Click Me</button>
</template>

<style scoped>
</style>