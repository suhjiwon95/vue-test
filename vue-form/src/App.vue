<script setup>
import { ref } from "vue";
import TheHeader from './components/header.vue'
import BaseInput from './components/BaseInput.vue';

const firstName = ref("");
const checkJiwon = () => {
  return firstName.value === "Jiwon" ? console.log("good") : console.log("bad");
}


</script>

<template>
  <div class="container">
    <header>
      <TheHeader title="Vue Form Practice" 
                message="In this practice, I learned basics of vue components such as props"
      />
    </header>

    <main >
      <BaseInput v-model="firstName" 
                  @submit-text="checkJiwon" />
    </main>
  </div>
  
</template>

<style>
  .container {
    display: flex;
    flex-direction: column;
    justify-content: flex-start;
    align-items: center;
    font-size: 1.125rem;
    gap: 1.2em;
  }

  header {
    text-align: center;
  }

</style>
