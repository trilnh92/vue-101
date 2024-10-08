<script setup>
import { ref, onMounted, onUpdated } from 'vue';

const props = defineProps(['delay']);

let showBlockRef = ref(false);
let timer = ref(null);
let reactionTime = ref(0);

// const emit = defineEmits(['end']);

function startTimer() {

    timer = setInterval(() => {
        reactionTime += 10;
    }, 10);

}

function stopTimer() {

    clearInterval(timer);
    // emit('end', reactionTime);

}

onMounted(() => {
    console.log(`the component is now mounted.`, props.delay);
 
})

onUpdated(() => {
    console.log(`the component is now updated.`, props.delay);

    setTimeout(() => {
        showBlockRef = true;
        startTimer();
        console.log(props.delay);
    }, props.delay);

})
</script>

<template>
    <div class="block" v-if="showBlockRef" @click="stopTimer()">Click Me</div>
</template>

<style scoped>

.block {
    width: 400px;
    border-radius: 20px;
    background: #0faf87;
    text-align: center;
    padding: 100px 0;
    margin: 40px auto;

    &:hover {
        cursor: pointer;
    }
}
</style>