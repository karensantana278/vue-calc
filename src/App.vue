<script setup>
import { reactive, watch } from 'vue';
import Header from './components/Header.vue'
import Form from './components/Form.vue'
import Result from './components/Result.vue'

const operacoes = ['+', '-', '*', '/']

const estado = reactive({
  number1: 0,
  number2: 0,
  operacao: '+',
  result: 0,
})

function calcResult() {
  const num1 = parseFloat(estado.number1) || 0;
  const num2 = parseFloat(estado.number2) || 0;

  switch (estado.operacao) {
    case '+':
      estado.result = num1 + num2;
      break;
    case '-':
      estado.result = num1 - num2;
      break;
    case '*':
      estado.result = num1 * num2;
      break;
    case '/':
      estado.result = num1 / num2;
      break;
    default:
      estado.result = 0;
  }
}


watch(() => estado.number1, () => calcResult());
watch(() => estado.number2, () => calcResult());
watch(() => estado.operacao, () => calcResult());


</script>

<template>

  <Header />

  <Form 
  :adicionaNumero1="evento => estado.number1 = evento.target.value" 
  :adicionaNumero2="evento => estado.number2 = evento.target.value" 
  :selecionaOperacao="evento => estado.operacao = evento.target.value"
  :operacoes="operacoes" />

  <Result :resultado="estado.result.toFixed(2)" />
</template>

<style scoped></style>
