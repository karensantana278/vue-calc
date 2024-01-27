<script setup>
 import {reactive, watch} from 'vue';

 const operacoes = ['+', '-', '*', '/']

 const estado = reactive({
  number1: 0,
  number2: 0,
  operacao: '+',
  result: 0,
})

function adicionaNumero1(evento){
  estado.number1 = evento.target.value;
}

function adicionaNumero2(evento){
  estado.number2 = evento.target.value;
}

function selecionaOperacao(evento){
  estado.operacao = evento.target.value;
}

function calcResult() {
  const num1 = parseFloat(estado.number1);
  const num2 = parseFloat(estado.number2);

  if (!isNaN(num1) && !isNaN(num2)) {
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
}

watch(() => estado.number1, () => calcResult());
watch(() => estado.number2, () => calcResult());
watch(() => estado.operacao, () => calcResult());


</script>

<template>
  <header>
    <div class="container">
      <div class="row">
        <div class="col-12 text-center p-5">
          <h1>Calculadora Aritmérica</h1>
        </div>
      </div>
    </div>
  </header>

  <section class="calc">
    <div class="container">
      <div class="row">
    <div class="col-md-5 col-12">
      <input @input="adicionaNumero1" type="number" class="form-control" placeholder="Insira o primeiro Número">
    </div>
    <div class="col-md-2 col-12 ">
      <select @change="selecionaOperacao" class="form-select text-center">
        <option v-for="op in operacoes" :value="op">{{ op }}</option>
      </select>
    </div>
    <div class="col-md-5 col-12">
      <input @input="adicionaNumero2" type="number" class="form-control" placeholder="Insira o segundo Número">
    </div>
  </div>
    </div>
  </section>

  <section class="result mt-5">
    <h2 class="result-number text-center text-success">
      {{ estado.result.toFixed(2) }}
    </h2>
  </section>
</template>

<style scoped>
  .result-number{
    font-size: 5rem;
  }
</style>
