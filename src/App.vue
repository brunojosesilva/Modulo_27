<script setup>

import { reactive, computed } from 'vue';


const estado = reactive({
  numero1: 0,  // Estado inicial para o primeiro número
  numero2: 0,  // Estado inicial para o segundo número
  operacao: '+' // Estado inicial para a operação (soma)
});


const resultado = computed(() => {
  switch (estado.operacao) {
    case '+':
      return estado.numero1 + estado.numero2;
    case '-':
      return estado.numero1 - estado.numero2;
    case '*':
      return estado.numero1 * estado.numero2;
    case '/':
      
      return estado.numero2 !== 0 ? estado.numero1 / estado.numero2 : "Divisão por zero não é permitida";
    default:
      return '';
  }
});
</script>

<template>

<div class="container mt-5">

  <div class="row justify-content-center">
 
    <div class="col-sm-12 col-md-6">
  
      <div class="form-group">
        <label for="numero1">Número 1:</label>
        <input id="numero1" type="number" v-model.number="estado.numero1" class="form-control">
      </div>

 
      <div class="form-group">
        <label for="numero2">Número 2:</label>
        <input id="numero2" type="number" v-model.number="estado.numero2" class="form-control">
      </div>

      <div class="form-group">
        <label for="operacao">Operação:</label>
        <select id="operacao" v-model="estado.operacao" class="form-control">
          <option value="+">Adição (+)</option>
          <option value="-">Subtração (-)</option>
          <option value="*">Multiplicação (*)</option>
          <option value="/">Divisão (/)</option>
        </select>
      </div>

     
      <h2>Resultado: {{ resultado }}</h2>
    </div>
  </div>
</div>
</template>

<style scoped>

</style>
