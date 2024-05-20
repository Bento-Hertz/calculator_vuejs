<script setup>
  import { reactive } from 'vue';

 
  const state = reactive({
    firstField: 0,
    secondField: 0,
    operation: '+',
    result: 0
  })

  function calcular() {
    const { firstField, secondField, operation } = state
    
    if(operation == '+')
      state.result = parseFloat(firstField) + parseFloat(secondField)
    else if(operation == '-')
      state.result = parseFloat(firstField) - parseFloat(secondField) 
    else if(operation == '/')
      state.result = parseFloat(firstField) / parseFloat(secondField) 
    else if(operation == '*')
      state.result = parseFloat(firstField) * parseFloat(secondField)
    else
      alert('Escolha uma operação válida!')
  }

  function onChangingFirstField(value) {
    if(value)
      state.firstField = value;
    calcular();
  }
  function onChangingSecondField(value) {
    if(value)
      state.secondField = value;
    calcular();
  }
  function onChangingOperation(value) {
    if(value)
      state.operation = value;
    calcular();
  }

</script>

<template>
  <input type="number" @keyup="e => onChangingFirstField(e.target.value)"> <br />
  <select @change="e => onChangingOperation(e.target.value)">
    <option value="+">+</option>
    <option>-</option>
    <option>/</option>
    <option value="*">x</option>
  </select> <br />
  <input type="number" @keyup="e => onChangingSecondField(e.target.value)"> <br />
  resultado: {{ state.result }}
</template>

<style scoped>

</style>
