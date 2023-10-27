<script setup>
  import { ref } from "vue";
  const count = ref(0);

</script>

<template>
  <div>
    <h4>
      The current count is
    </h4>
    <h1>{{ count }}</h1>
    <div class="button-wrapper">
      <button @click="count--">-</button>
      <button @click="count++">+</button>
    </div>
  </div>
</template>

<style scoped>
  div {
    display: flex;
    flex-direction: column;
    justify-content:center;
    align-items: center;
    gap: 1.3em;
    text-align: center;
  }

   .button-wrapper {
    flex-direction: row;
    gap: 1em;
  }

  button {
    width: 40px;
    height: 30px;
    font-weight: bold;
  }
  
</style>