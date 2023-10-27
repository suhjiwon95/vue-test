<script setup>
  import quizesJson from "./assets/quizes.json";
  import { ref } from "vue";

  const quizes = ref(quizesJson);

</script>

<template>
  <div class="container">
    <!-- {{ quizesJson }} -->
    <header>
      <h1>Quizes</h1>
      <input type="text" placeholder="Search quizes here">
    </header>
    <div class="cards-container">
      <div 
        v-for="quiz in quizes"
        :key="quiz.id"
        class="card">
        <img :src="quiz.img" alt="">
        <div class="card-text">
          <h2>{{ quiz.name }}</h2>
          <p>{{ quiz.questions.length }} questions</p>
        </div>
      </div>
    </div>
  </div>
</template>

<style scoped>
  .container {
    width: 100vw;
    height: 100vh;
    max-width: 1000px;
    margin: 0 auto;
    padding: 2em;
    font-size: 1.125rem;
  }

  header {
    display: flex;
    align-items: center;
    justify-content: space-between;
    gap: 2em;
    margin-bottom: 2em;
  }

  header h1 {
    font-weight: bold;
  }

  header input {
    border: 1.6px solid rgba(128,128,128,0.5);
    padding: .8em 1.6em;
    border-radius: 50px;
    width: 400px;
    font-size: 1.125rem;
  }
  header input::placeholder {
    color: rgba(128,128,128,0.5);
  }

  .cards-container {
    display: flex;
    flex-wrap: wrap;
    gap: 1.2em;
  }

  .card {
    overflow: hidden;
    width: 360px;
    height: 310px;
    border: 1.6px solid rgba(128,128,128,0.5);
    border-radius: 4px;
    display: flex;
    flex-direction: column;
    justify-content: space-between;
    align-items: center;
  }

  img {
    width: 100%;
    background-color: rgba(232, 227, 227, 0.1);
  }
  
  .card-text {
    text-align: center;
    margin-bottom: 20px;
  }

  h2 {
    font-weight: bold;
  }
</style>