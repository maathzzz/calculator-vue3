<script setup>
  import {ref} from 'vue';
  import Display from '../src/components/Resultado.vue'

  const result = ref('');

  function handleClick(value){
    result.value += value;
  }

  function handleCalculate() {
    try {
      result.value = eval(result.value);
    } catch (e) {
      result.value = 'Erro';
    }
  }

  function handleDel() {

    if(result.value.length > 0){
      result.value = result.value.slice(0, -1);
    } else if (result.value === 'Erro'){
      result.value = ''
    } else {
      result.value = ''
    }

  }

  function handleClear(){
    result.value = ''
  }

</script>


<template>
<div class="container">
  <div class="calculator">
    <!-- <div class="display">{{ result }}</div> -->
    <Display v-model:resultado="result"/>
    <div class="buttons">
      <button @click="handleClick('7')">7</button>
      <button @click="handleClick('8')">8</button>
      <button @click="handleClick('9')">9</button>
      <button @click="handleDel">Del</button>
      <button @click="handleClick('4')">4</button>
      <button @click="handleClick('5')">5</button>
      <button @click="handleClick('6')">6</button>
      <button @click="handleClick('+')">+</button>
      <button @click="handleClick('1')">1</button>
      <button @click="handleClick('2')">2</button>
      <button @click="handleClick('3')">3</button>
      <button @click="handleClick('-')">-</button>
      <button @click="handleClick('0')">0</button>
      <button @click="handleClick('.')">.</button>
      <button @click="handleClick('/100')">%</button>
      <button @click="handleClick('*')">*</button>
      <button @click="handleClick('(')">(</button>
      <button @click="handleClick(')')">)</button>
      <button @click="handleClear">Clear</button>
      <button @click="handleClick('/')">/</button>
      <button @click="handleCalculate">=</button>
    </div>
  </div>
</div>
</template>

<style>
  body{
    background: linear-gradient(90deg, #3e6a85, #000); 
  }

  .container{
    width: 100%;
    height: 100%;
    margin-top: 150px;
    display: flex;
    align-items: center;
    justify-content: center;
  }

  .calculator {
    border: 1px solid #ccc;
    padding: 10px;
    margin: 10px;

    width: 30%;
    height: 10%;
    
    background: #3c4043;
    border-radius: 10px;
  }

  .buttons {
    display: grid;
    grid-template-columns: repeat(4, 1fr);
    grid-gap: 20px;
  }

  button {
    height: 50px;
    font-size: 20px;
    padding: 5px;
    border-radius: 23px;
    background: aliceblue;
    cursor: pointer;
  }
</style>