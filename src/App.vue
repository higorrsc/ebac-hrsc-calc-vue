<script setup>
import { reactive } from 'vue';

const estado = reactive({
  primeiroNumero: 0,
  operacao: "soma",
  segundoNumero: 0,
  resultado: 0,
  calculoPossivel: true
});

const alteraOperacao = (e) => {
  estado.operacao = e.target.value.toString();
  calculaResultado();
}

const calculaResultado = () => {
  const { primeiroNumero, operacao, segundoNumero } = estado;
  estado.calculoPossivel = true;
  if (operacao === "soma") {
    estado.resultado = Number(primeiroNumero) + Number(segundoNumero);
  } else if (operacao === "subtracao") {
    estado.resultado = Number(primeiroNumero) - Number(segundoNumero);
  } else if (operacao === "multiplicacao") {
    estado.resultado = Number(primeiroNumero) * Number(segundoNumero);
  } else {
    if (segundoNumero != 0) {
      estado.resultado = Number(primeiroNumero) / Number(segundoNumero);
    } else {
      estado.calculoPossivel = false;
    }
  }
  console.log(estado.calculoPossivel);
}

</script>

<template>
  <div class="container">
    <h1>Calculadora em Vue.js</h1>
    <form @submit.prevent="">
      <div class="row mb-3">
        <label for="firstNumber" class="col-sm-2 col-form-label">1º núm</label>
        <div class="col-sm-10">
          <input @keyup="evento => estado.primeiroNumero = evento.target.value" @change="calculaResultado"
            :value="estado.primeiroNumero" type="number" name="firstNumber" id="firstNumber" placeholder="1º núm"
            class="form-control" value="0">
        </div>
      </div>
      <div class="row mb-3">
        <label for="operation" class="col-sm-2 col-form-label">Operação</label>
        <div class="col-sm-10">
          <select name="operation" id="operation" class="form-select" :value="estado.operacao" @change="alteraOperacao">
            <option value="soma">+</option>
            <option value="subtracao">-</option>
            <option value="multiplicacao">*</option>
            <option value="divisao">/</option>
          </select>
        </div>
      </div>
      <div class="row mb-3">
        <label for="secondNumber" class="col-sm-2 col-form-label">2º núm</label>
        <div class="col-sm-10">
          <input @keyup="evento => estado.segundoNumero = evento.target.value" @change="calculaResultado"
            :value="estado.segundoNumero" type="number" name="secondNumber" id="secondNumber" placeholder="1º núm"
            class="form-control" value="0">
        </div>
      </div>
      <hr>
      <div class="row mb-3">
        <label for="resultNumber" class="col-sm-2 col-form-label">Resultado</label>
        <div class="col-sm-10">
          <input v-if="estado.calculoPossivel === true" type="number" :value="estado.resultado" name="resultNumber"
            id="resultNumber" placeholder="Resultado" class="form-control" value="0" readonly>
          <span v-else>Não é possível dividir por 0 (Zero)</span>
        </div>
      </div>
    </form>
  </div>
</template>

<style scoped></style>
