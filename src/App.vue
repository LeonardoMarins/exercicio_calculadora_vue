<script setup>
import { reactive } from 'vue';
import Input from './components/inputs.vue';

const estado = reactive({
  valor1:0,
  valor2:0,
  operador: '',
})

const calcular = () => {
  const {valor1, valor2, operador} = estado;

    switch(operador) {
      case '+':
        return valor1 + valor2;
      case '-':
        return valor1 - valor2;
      case '/':
        return valor1 / valor2;
      case '*':
        return valor1 * valor2;
    }
  
}




</script>

<template>
  <div class="container p-3">
    <form @submit.prevent="calcular()">
    <div class="row">
      <h1>Calculadora VueJS</h1>
      <div class="col-12 inputs">
        <Input :entrada="event => estado.valor1 = parseFloat(event.target.value)" :entrada2="event => estado.valor2 = parseFloat(event.target.value)" />
          
      </div>
      <div class="row">
        <div class="col-12">
          <select v-model="estado.operador" class="mt-4">
            <option value="+">+</option>
            <option value="-">-</option>
            <option value="/">/</option>
            <option value="*">*</option>
          </select>
        </div>
      </div>
    </div>
    </form>
  </div>
  <p v-if="calcular()">{{ `o resultado e: ${calcular()}`}}</p>
  <p v-else-if="calcular() === 0">{{'o resultado e: 0'}}</p>
  <p v-else>Esperando numero para calcular</p>
</template>

<style scoped>
* {
  padding: 0px;
  margin: 0;
  box-sizing: border-box;
}

.container {
  border: solid;
  max-width: 50vw;
  text-align: center;
  height: 50vh;
  margin-left: 25vw;
}

.inputs {
  display: flex;
  flex-direction: column;
  align-items: center;
  justify-content: center;
}

p {
  text-align: center;
}

select {
  margin-right: 20px;
}
</style>
