<script setup>
import { ref } from "vue";
import TheHeader from './components/header.vue'
import BaseInput from './components/BaseInput.vue';

const firstName = ref("");
const lastName = ref("");
const email = ref("");

function checkInput(email) {
  
  if (/^\w+([\.-]?\w+)*@\w+([\.-]?\w+)*(\.\w{2,3})+$/.test(email)) {
    return true;
  } else {
    console.log('wrong email')
  }
}


</script>

<template>
  <div class="container">
    <header>
      <TheHeader title="Vue Form Practice" 
                message="I was able to understand the concept of props, v-model, and emitting events, and created a reusable input components"
      />
    </header>

    <main >
      <BaseInput v-model:first-name="firstName"
                 v-model:last-name="lastName" 
                 v-model:email-address="email"
                 @submit:submit-event="checkInput(email)"/>
     
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

  main {
    display: flex;
    flex-direction: column;
    justify-content: flex-start;
    align-items: center;
    padding: 2em;
    box-shadow: rgba(149, 157, 165, 0.2) 0px 8px 24px;
    border-radius: 8px;
  }

  
</style>
