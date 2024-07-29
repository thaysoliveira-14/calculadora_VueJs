<script setup>
import { reactive } from 'vue';

const estado = reactive({
    num1: '',
    num2: '',
    operacoes: {
        soma: (a, b) => a + b,
        subtracao: (a, b) => a - b,
        multiplicacao: (a, b) => a * b,
        divisao: (a, b) => (b !== 0 ? a / b : 'Divisão por zero'),
    },
    resultado: 0,
});

const calcularResultado = () => {
    const { num1, num2, operacaoMatematica } = estado;
    estado.resultado = estado.operacoes[operacaoMatematica](parseFloat(num1), parseFloat(num2));
};
</script>

<template>
    <div class="container ">
        <h1 class="fnt">Calculadora Aritmética VueJs</h1>

        <input type="number" v-model="estado.num1" @input="calcularResultado" />
        <input type="number" v-model="estado.num2" @input="calcularResultado" />

        <select v-model="estado.operacaoMatematica" @change="calcularResultado">
            <option value="soma">Soma</option>
            <option value="subtracao">Subtração</option>
            <option value="multiplicacao">Multiplicação</option>
            <option value="divisao">Divisão</option>
        </select>

        <p class="result">Resultado: <strong>{{ estado.resultado }}</strong></p>
    </div>
</template>

<style scoped>
.container {
max-width: 320px;
margin: 25vh auto;
padding: 20px;
background-color: #1a5964;
border-radius: 5px;
color: white;
box-shadow: 0px 0px 5px rgba(0, 0, 0, 0.5);
text-align: center;
font-family: sans-serif
}

.fnt {
font-size: 1.2em;
}

input {
margin: 10px 0;
padding: 8px;
width: 300px;
border: 1px solid #000000;
border-radius: 3px;
display: flex;
align-items: center;
text-align: center;

}

select {
margin: 10px 0;
padding: 8px;
width: 320px;
border: 1px solid #000000;
border-radius: 3px;
display: flex;
align-items: center;
text-align: center;

}

.result {
font-size: 1.2em;
text-align: center;
}
</style>