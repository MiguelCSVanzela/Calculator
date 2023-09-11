<script setup>
import { reactive } from 'vue';
import Cabecalho from './components/Cabecalho.vue';
import Historico from './components/Historico.vue';
import Formulario from './components/Formulario.vue';

const state = reactive({
  filtro: "",
  numberOne: "",
  numberTwo: "",
  dataAtual: "", 
  operations: [
    {
      firstNumber: 10,
      secondNumber: 10,
      operation: "x",
      result: 100, 
      feitoEm: "8/9/2023 - 20:44"
    }
  ]
})

const operation = () => {
  const { filtro, numberOne, numberTwo } = state;

  switch (filtro) {
    case "somar":
      return numberOne + numberTwo;
    case "subtrair":
      return numberOne - numberTwo;
    case "multiplicar":
      return numberOne * numberTwo;
    case "dividir":
      return numberOne / numberTwo;
    case "resto":
      return numberOne % numberTwo;
    case "potencia":
      return numberOne ** numberTwo;
    case "raiz":
      return numberOne ** (1 / numberTwo);
  }
}

const getSinal = () => {
  const { filtro } = state;

  switch (filtro) {
    case "somar":
      return "+";
    case "subtrair":
      return "-";
    case "multiplicar":
      return "x";
    case "dividir":
      return "/";
    case "resto":
      return "modulo de";
    case "potencia":
      return "elevado a";
    case "raiz":
      return "raiz de";
  }
}

const getDataAtual= () => {
const d = new Date()
  return `${d.getDate()}/${d.getMonth() + 1}/${d.getFullYear()} - ${d.getHours()}:${d.getMinutes()}`
}


const useResult = () => {
        let inputOne = document.querySelector(".inputOne"); 
        let inputTwo = document.querySelector(".inputSecond"); 
        inputOne.value =  operation()
        inputTwo.value = 0
    }

const registrarOperacao = () => {
  const novaOperacao = {
    firstNumber: state.numberOne,
    secondNumber: state.numberTwo,
    operation: getSinal(),
    result: operation(),
    feitoEm: getDataAtual()
  }
  state.operations.unshift(novaOperacao);
  console.log(getDataAtual())
}

</script>

<template>
  <div class="container">
    <Cabecalho />


    <Formulario :trocarFiltro="event => state.filtro = event.target.value"
      :addNumberOne="event => state.numberOne = Number.parseFloat(event.target.value)"
      :addNumberTwo="event => state.numberTwo = Number.parseFloat(event.target.value)"
      :addYear="event => state.dataAtual = event.target.value"
      :zeroStyle="state.numberTwo == 0 && state.filtro == 'dividir'" :registrarOperation="registrarOperacao"
      :operation="operation()" :conditionResult="operation() || operation() == 0"
      :conditionDefault="(state.numberOne == 0 || state.numberTwo == 0) && (state.filtro !== 'resto') && (operation() !== 'Infinity')" 
      :useResultado="useResult" 
      />
      

    <Historico :operations="state.operations" />

  </div>
</template>

<style>
:root{
  --forest: #97D8C4;
  --dark: #2A2D34;
  --rose: #D81159;
  --sky: #118AB2;
  --platium: #E6E8E6;
  --white: #fcfcfc;
  --jasmine: #FFD972; 
}
</style>
