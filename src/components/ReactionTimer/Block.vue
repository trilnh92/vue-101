<script setup>
import { ref, onMounted, onUpdated } from 'vue';

const props = defineProps(['delay']);

let showBlockRef = ref(false);
console.log(showBlockRef);

onMounted(() => {
    console.log(`the component is now mounted.`);

    setTimeout(() => {
        showBlockRef.value= true;
        console.log(showBlockRef);
    }, props.delay);
})

onUpdated(() => {
    console.log(`the component is now updated.`)
})

</script>

<template>
    <div class="block" v-if="showBlockRef.value">Click Me</div>
</template>

<style scoped>
.block {
    width: 400px;
    border-radius: 20px;
    background: #0faf87;
    text-align: center;
    padding: 100px 0;
    margin: 40px auto;
}
</style>