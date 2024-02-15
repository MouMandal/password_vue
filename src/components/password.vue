<script setup>
import { ref } from 'vue';
const length = (ref(8));
const upperCase = ref("ABCDEFGHIJKLMNOPQRSTUVWXYZ");
const lowerCase = ref("abcdefghijklmnopqrstuvwxyz");
const number = ref("0,1,2,3,4,5,6,7,8,9");
const symbol = ref("!@#$%^&*(){}[]<>/-=+_");
const passwordBox = ref("");

const allChars = () => {
    return upperCase.value + lowerCase.value + number.value + symbol.value;
}

const calculate = () => {
    let password = "";
    password += upperCase.value[Math.floor(Math.random() * upperCase.value.length)];
    password += lowerCase.value[Math.floor(Math.random() * lowerCase.value.length)];
    password += number.value[Math.floor(Math.random() * number.value.length)];
    password += symbol.value[Math.floor(Math.random() * symbol.value.length)];
    while (length.value > password.length) {
        password += allChars();
    }
    passwordBox.value = password;
}
</script>
<template>
    <div class="container">
        <h1>Generate a <br><span>Random Password</span></h1>
        <div class="display">
            <input type="text" v-model="passwordBox" placeholder="password">
        </div>
        <button @click="calculate">Generate Password</button>
    </div>
</template>
<style></style>

