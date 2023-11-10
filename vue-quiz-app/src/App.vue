<script setup>
  import quizesJson from "./assets/quizes.json";
  import { ref, watch } from "vue";
  import Card from "./components/Card.vue";
  import { RouterView, RouterLink } from "vue-router";

  const quizes = ref(quizesJson);
  const search = ref("");

  watch(search, () => {
    quizes.value = quizesJson.filter(quiz => quiz.name.toLowerCase().includes(search.value.toLowerCase()))
  })

</script>

<template>
  <div class="container">
    <!-- {{ quizesJson }} -->
    <header>
      <h1>Quizes</h1>
      <input v-model.trim="search" type="text" placeholder="Search quizes here">
    </header>
    <div class="cards-container">
      <Card v-for="quiz in quizes" :key="quiz.id" :quiz="quiz" />
      <!-- <div 
          v-for="quiz in quizes"
          :key="quiz.id"
          class="card">
        <img :src="quiz.img" alt="">
        <div class="card-text">
          <h2>{{ quiz.name }}</h2>
          <p>{{ quiz.questions.length }} questions</p>
        </div>
      </div> -->
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

  
</style>