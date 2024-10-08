<script setup>
import { ref, computed } from "vue";

let email = defineModel('email');

let password = defineModel('password');

let role = defineModel('role', { type: String, default: 'developer' });

let terms = defineModel('terms', { type: Boolean, default: true });

let names = defineModel('names', { type: Array, default: [] });

</script>

<template>
    <h1>Form</h1>
    <form>
        <label>Email: </label>
        <input type="email" required v-model="email" />
        <br />
        <label>Password: </label>
        <input type="password" required v-model="password" />
        <br />
        <label>Role: </label>
        <select v-model="role">
            <option value="developer">Web Dev</option>
            <option value="designer">Designer</option>
        </select>
        <br />
        <div class="term">
            <input type="checkbox" v-model="terms" />
            <label>Accept Terms and Conditions</label>
        </div>
        <br />
        <div class="names">
            <input type="checkbox" value="peter" v-model="names" />
            <label>Peter</label>
        </div>
        <div class="names">
            <input type="checkbox" value="mari" v-model="names" />
            <label>Mari</label>
        </div>
        <div class="names">
            <input type="checkbox" value="ace" v-model="names" />
            <label>Ace</label>
        </div>
    </form>

    <p>Email: {{ email }}</p>
    <p>Password: {{ password }}</p>
    <p>Role: {{ role }}</p>
    <p>Name: {{ names }}</p>
</template>

<style scoped>
form {
    text-align: left;
}

.label {
    display: block;
    font-size: 16px;
    padding-right: 20px;
    margin-bottom: 20px;
}

input {
    display: block;

    min-height: 40px;
    min-width: 300px;
    border: 1px solid #ddd;
}
</style>