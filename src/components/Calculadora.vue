<script setup>
import { reactive } from 'vue';
    const estado = reactive({
        primeiro_numero: '',
        segundo_numero: '',

        operacoes: {
            soma: (a,b) => a + b,
            subtracao: (a,b) => a - b,
            multiplicacao: (a,b) => a * b,
            divisao: (a,b) => (b !== 0 ? a/b : 'Divisão por Zero')
        },
        resultado : 0,
    });

    const calcular_resultado = () => {
        const {primeiro_numero, segundo_numero, operacao_matematica} = estado;
        estado.resultado = estado.operacoes[operacao_matematica](parseFloat(primeiro_numero), parseFloat(segundo_numero));
    };

</script>

<template>
    <div class="container">
        <h1>Calculadora Vue.js</h1>

        <input type="text" v-model="estado.primeiro_numero" @input="calcular_resultado">
        <input type="text" v-model="estado.segundo_numero" @input="calcular_resultado">

        <select v-model="estado.operacao_matematica" @change="calcular_resultado">
            <option value="soma">Soma</option>
            <option value="subtracao">Subtração</option>
            <option value="multiplicacao">Multiplicação</option>
            <option value="divisao">Divisão</option>
        </select>

        <p>Resultado: {{ estado.resultado }}</p>
    </div>    
</template>