<script setup>
import { reactive } from 'vue';


const valores = reactive({
  operador: '',
  numero1: 0,
  numero2: 0,
  resultado: 0,
})

function operadorUsado(){
  let operação = valores.operador;

  if (operação == "+") {
    valores.resultado = valores.numero1 + valores.numero2;
  } if (operação == "-") {
    valores.resultado = valores.numero1 - valores.numero2;
  } if (operação == "*") {
    valores.resultado = valores.numero1 * valores.numero2;
  }if (operação == "/") {
    valores.resultado = valores.numero1 / valores.numero2;
  }
}

function recuperaCampo1(evento) {
  valores.numero1 = parseInt(evento.target.value);
  operadorUsado();
}

function recuperaCampo2(evento) {
  valores.numero2 = parseInt(evento.target.value);
  operadorUsado();
}

function recuperaOperador(evento) {
  valores.operador = evento.target.value;
  operadorUsado()
}

</script>

<template>
  <body>
    <h1>Calculadora</h1>
    <p>Digite os valores e selecione a sua operação:</p>
    <input type="number" @keyup="recuperaCampo1" required />
    <select @change="recuperaOperador">
      <option value="" selected disabled > Selecione: </option>
      <option value="+"> Soma + </option>
      <option value="-"> Subtração - </option>
      <option value="/"> Divisão ÷ </option>  
      <option value="*"> Multiplicacão * </option>
    </select>
    <input type="number" @keyup="recuperaCampo2" required  />
    <h3>Resultado</h3>
    <span>{{ valores.resultado }}</span>
  </body>
</template>

<style scoped>

body{
  text-align: center;
}

span {
  font-size: 40px;
}

</style>
