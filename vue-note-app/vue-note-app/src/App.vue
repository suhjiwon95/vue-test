<script setup>
  import { ref } from 'vue';
  import { RouterLink, RouterView } from 'vue-router';

  const showModal = ref(false);
  const newNote = ref("");
  const notes = ref([]);
  let errorMessage = ref("");
 
  const randomHsl = () => `hsla(${Math.random() * 360}, 100%, 50%, 1)`

  const addNote = () => {
    if (newNote.value.length < 10) {
      return errorMessage.value = "Enter more than 10 characters";

    } 
      notes.value.push({
        id: Math.floor(Math.random() * 100000),
        text: newNote.value,
        date: new Date(),
        backgroundColor: randomHsl()
      });
      showModal.value = false; //update the state of showModel: close automatically when clicking add note button
      newNote.value = "";
      errorMessage.value = "";
    }
</script>

<template>
  
  <div v-if="showModal" class="overlay">
    <div class="modal">
      
      <button class="close" @click="showModal = false">X</button>
      <textarea name="note" id="note" cols="30" rows="30" v-model.trim="newNote"></textarea>
      <p v-if="errorMessage" class="error">{{errorMessage}}</p>
      <button @click="addNote">Add Note</button>
      
    </div>
  </div>
  <main>
    <div class="container">
      <header>
        <h1>Notes</h1>
        <div class="nav-wrapper">
          <nav>
            <RouterLink to="/about">About</RouterLink>
          </nav>
        </div>
        <RouterView />
        <button @click="showModal = true">+</button>
      </header>
      <div class="cards-container">
        <div v-for="note in notes" 
             :key="note.id"
             class="card" 
             :style="{backgroundColor: note.backgroundColor}">
          <p class="main-text">{{ note.text }}</p>
         
          <p class="date">{{ note.date.toLocaleDateString('en-US') }}</p>
        </div>
      </div>
    </div>
  </main>
</template>

<style scoped>
  main {
    height: 100vh;
    width: 100vw;
  }

  .container {
    max-width: 1000px;
    padding: 2em;
    margin: 0 auto;
  }

  header {
    display: flex;
    justify-content: space-between;
    align-items: center;
    margin-bottom: 2em;
  }

  h1 {
    font-size: 2rem;
    font-weight: bold;
  }

  button {
    cursor: pointer;
  }

  header button,
  .close {
    padding: 1em;
    border-radius: 50%;
    width: 32px;
    height: 32px;
    display: flex;
    justify-content: center;
    align-items: center;
    border: 1px solid royalblue;
    background-color: royalblue;
    color: white;
    font-weight: bold;
    font-size: 1.25rem;
  }

  .cards-container {
    display: flex;
    flex-wrap: wrap;
    gap: 1.2em;
  }

  .card {
    width: 225px;
    height: 225px;
    background-color: black;
    border-radius: 8px;
    padding: 1.2em;
    display: flex;
    flex-direction: column;
    justify-content: space-between;
    align-items: flex-start;
    color: white;
  }

  .date {
    font-size: 14px;
  }

  .overlay {
    position: absolute;
    width: 100%;
    height: 100%;
    background-color: rgba(0,0,0,0.5);
    z-index: 10;
    display: flex;
    align-items: center;
    justify-content: center;
  }

  .modal {
    width: 750px;
    border-radius: 8px;
    position: relative;
    display: flex;
    flex-direction: column;
    padding: 2em;
    background-color: aliceblue;
  }

  textarea {
    padding: 2em;
    font-size: 1.125;
    
  }
  .modal button {

    padding: 1.2em;
    border: 1px solid royalblue;
    background-color: royalblue;
    color: white;
    font-weight: bold;
    font-size: 1.25rem;
  }

  .close {
    align-self: flex-end;
    margin-bottom: 20px;
  }

  .error {
    color: red;
  }

</style>