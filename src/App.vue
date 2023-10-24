<script setup>
  import { ref } from "vue";
  import Calculator from './components/Calculator.vue';
  import Todo from './components/Todo.vue';

  const active = ref("calculator");

  function switchMode() {
    if (active.value === "calculator") active.value = "todo";
    else active.value = "calculator";
  }
</script>

<template>
  <main>
    <button @click="switchMode">Switch Mode</button>
    <Calculator v-if="active === 'calculator'"></Calculator>
    <Todo v-else></Todo>
  </main>
</template>

<style scoped>
  main {
    height: 100vh;
  }
</style>
