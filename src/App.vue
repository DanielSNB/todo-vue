<script setup>
import { ref, computed } from 'vue';

const num1 = ref(0);
const num2 = ref(0);
const operation = ref('+');

const result = computed(() => {
    switch (operation.value) {
        case '+': return num1.value + num2.value;
        case '-': return num1.value - num2.value;
        case '*': return num1.value * num2.value;
        case '/': return num2.value !== 0 ? (num1.value / num2.value).toFixed(2) : 'Erro';
        default: return 0;
    }
});

const calculatorImage = "https://cdn-icons-png.flaticon.com/512/3502/3502488.png";
</script>

<template>
    <div class="container d-flex justify-content-center align-items-center vh-100">
        <div class="calculator card p-4 shadow-sm rounded">
            <img :src="calculatorImage" alt="Calculadora" class="calculator-img mb-3 mx-auto d-block">
            <h2 class="text-center text-secondary mb-4">Calculadora Aritmética</h2>
            <div class="inputs d-flex justify-content-center gap-3 mb-4">
                <input type="number" v-model.number="num1" placeholder="Número 1" class="form-control">
                <select v-model="operation" class="form-select w-auto">
                    <option value="+">+</option>
                    <option value="-">-</option>
                    <option value="*">×</option>
                    <option value="/">÷</option>
                </select>
                <input type="number" v-model.number="num2" placeholder="Número 2" class="form-control">
            </div>
            <div class="result text-center fs-4 fw-bold text-black">
                Resultado: <span class="text-danger">{{ result }}</span>
            </div>
        </div>
    </div>
</template>

<style scoped>
body {
    font-family: 'Poppins', sans-serif;
    background: linear-gradient(to right, #6a11cb, #2575fc);
    margin: 0;
}

.calculator-img {
    width: 80px;
    height: 80px;
}
</style>
