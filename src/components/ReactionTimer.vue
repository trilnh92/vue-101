<script setup>
import { ref, computed } from "vue";
import Block from "./ReactionTimer/Block.vue";

let isPlaying = defineModel('isPlaying');
let delay = defineModel('delay');

function start() {
    this.delay = 2000 + Math.random() * 5000;
    this.isPlaying = true;
    // console.log(this.delay, this.isPlaying);
}

</script>

<template>
    <h1>Ninja Reaction Timer</h1>

    <button class="btn" @click="start()" :disabled="isPlaying">Play</button>

    <Block :if="isPlaying" :delay="delay" />
</template>


<style scoped>

h1 {
    margin: 0;
    padding: 0;
    color: #EF6024;
    margin-bottom: 30px;
}

button[disabled] {
    opacity: .3;
}

.btn {
    min-width: 180px;
    background: #731702;
    color: #fff;

    font-size: 16px;
    font-weight: 700;
    letter-spacing: .01em;

}
</style>