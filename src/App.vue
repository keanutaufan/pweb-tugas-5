<script setup>
  import { onMounted, ref } from "vue";
  const input1 = ref(null);
  const input2 = ref(null);
  const result = ref(0);

  function add() {
    result.value = input1.value + input2.value;
  }

  function sub() {
    result.value = input1.value - input2.value;
  }
  function mul() {
    result.value = input1.value * input2.value;
  }
  function div() {
    result.value = input1.value / input2.value;
  }
</script>

<template>
  <main>
    <div class="simple-calculator">
      <h1>Simple Calculator</h1>
      <div class="input-fields">
        <div class="input-group">
          <label for="num1">Number 1:</label>
          <input type="number" id="num1" v-model="input1">
        </div>
        <div class="input-group">
          <label for="num2">Number 2:</label>
          <input type="number" id="num2" v-model="input2">
        </div>
      </div>
      <div class="buttons">
        <button @click="add">&plus;</button>
        <button @click="sub">&minus;</button>
        <button @click="mul">&times;</button>
        <button @click="div">&div;</button>
      </div>
      <div class="result">
        <p>Result: </p>
        <h2>{{ result }}</h2>
      </div>
    </div>
  </main>
</template>

<style scoped>
  main {
    height: 100vh;
    display: flex;
    flex-direction: column;
    align-items: center;
    justify-content: center;
  }

  .simple-calculator {
    display: flex;
    flex-direction: column;
    align-items: center;
    justify-content: center;
    gap: 2rem;
  }

  .input-fields {
    display: flex;
    gap: 2rem;
  }

  .input-group {
    display: flex;
    flex-direction: column;
  }

  input {
    height: 2rem;
    font-size: 1rem;

  }

  .buttons {
    display: flex;
    align-items: center;
    justify-content: center;
    gap: 16px;
  }

  .result {
    text-align: center;
  }
</style>
