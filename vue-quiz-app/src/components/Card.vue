<script setup>
  import { defineProps } from "vue";

  const {quiz} = defineProps(['quiz']); // Destructure props

  

</script>

<template>
    <div class="card">
        <img :src="quiz.img" alt="">
        <div class="card-text">
          <h2>{{ quiz.name }}</h2>
          <p>{{ quiz.questions.length }} questions</p>
        </div>
    </div>
</template>

<style scoped>
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
    gap: 0.8em;
  }

  img {
    width: 100%;
    height: 310px;
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