<script setup>
import { ref, computed } from "vue";
import Block from "./ReactionTimer/Block.vue";
// import Results from "./ReactionTimer/Results.vue";

let isPlaying = ref(false);
let delay = ref(null);
let score = ref(null);
let showResults = ref(false);

function start() {
    delay = 2000 + Math.random() * 5000;
    isPlaying = true;
    console.log(delay, isPlaying);
}

// function endGame(reactionTime) {
//     score = reactionTime;
//     isPlaying = false;
// }

</script>

<template>
    <h1>Ninja Reaction Timer</h1>

    <button class="btn" @click="start()" :disabled="isPlaying">Play</button>

    <Block v-if="isPlaying" :delay="delay" />

    <p v-if="showResults">Reaction Time: {{ score }} ms</p>

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