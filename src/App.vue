<script setup>
</script>

<template>
  <div class="container">
    <h1>Calculadora em VueJS</h1>
    <form @submit.prevent="">
      <div class="row">
        <div class="col-md-3">
          <input type="number" name="" id="" placeholder="1º núm" class="form-control" value="0">
        </div>
        <div class="col-md-1">
          <select name="" id="" class="form-select">
            <option value="soma">+</option>
            <option value="subtracao">-</option>
            <option value="multiplicacao">*</option>
            <option value="divisao">/</option>
          </select>
        </div>
      </div>
      <div class="row">
        <div class="col-md-3">
          <input type="number" name="" id="" placeholder="2º núm" class="form-control" value="0">
        </div>
      </div>
    </form>
  </div>
</template>

<style scoped></style>
