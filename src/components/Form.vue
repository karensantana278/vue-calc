<script setup>
    const props = defineProps(['adicionaNumero1', 'adicionaNumero2', 'selecionaOperacao', 'operacoes'])
</script>

<template>
    <section class="calc">
    <div class="container">
      <div class="row">
        <div class="col-md-5 col-12">
          <input @input="props.adicionaNumero1" type="number" class="form-control" placeholder="Insira o primeiro Número">
        </div>
        <div class="col-md-2 col-12 ">
          <select @change="props.selecionaOperacao" class="form-select text-center">
            <option v-for="op in props.operacoes" :value="op">{{ op }}</option>
          </select>
        </div>
        <div class="col-md-5 col-12">
          <input @input="props.adicionaNumero2" type="number" class="form-control" placeholder="Insira o segundo Número">
        </div>
      </div>
    </div>
  </section>
</template>

<script scoped>
</script>