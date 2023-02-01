<script setup>
  import { ref } from "vue";

  const showModal = ref(false);
  const newNote = ref("");
  const notes = ref([]);
  const errorMessage = ref("");
  function getRandomColor() {
    return "hsl(" + Math.random() * 360 + ", 50%, 20%)";
  }

  const addNote = () =>{
    if(newNote.value.length <10){
      return errorMessage.value = "You must enter 10 characters"
    }
    notes.value.push({
      key: newNote,
      text: newNote.value,
      date: new Date(),
      backgroundColor: getRandomColor(),
    });
    showModal.value = false;
    newNote.value = "";
    errorMessage.value = "";
  }
</script>

<template>
  <main>
    <div v-if="showModal" class="overlay">
      <div class="modal">
        <textarea v-model.trim="newNote" name="note" id="note" cols="30" rows="10"></textarea>
        <p v-if="errorMessage"> {{ errorMessage }}</p>
        <button @click="addNote">Confirm</button>
        <button class="close" @click="showModal = false">Close</button>
      </div>
    </div>
    <div class="container">
      <header>
        <h1>My Notes</h1>
        <button @click="showModal = true">Add new</button>
      </header>
      <div class="cards-container">
        <div v-for="note in notes" :key="note" class="card" :style="{backgroundColor: note. backgroundColor}">
          <p class="main-text">
            {{ note.text }}
          </p>
          <p class="date">Date: {{ note.date.toLocaleDateString("en-UK")}}</p>
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
  padding: 10px;
  margin: 0 auto;
}

header {
  display: flex;
  justify-content: space-between;
  align-items: center;
}
h1 {
  font-size: 55px;
  margin-bottom: 25px;
  font-weight: 700;
}
header button {
  border: none;
  padding: 10px;
  width: 100px;
  height: 40px;
  background-color: darkslategray;
  border-radius: 5px;
  color: white;
  cursor: pointer;
  font-size: 15px;
}
.cards-container {
  display: flex;
  flex-wrap: wrap;
}
.card {
  width: 250px;
  height: 250px;
  background-color: darkslategray;
  padding: 15px;
  display: flex;
  flex-direction: column;
  justify-content: space-between;
  margin-right: 20px;
  margin-bottom: 20px;
  border-radius: 10px;
  color: white;
}
.overlay {
  position: absolute;
  width: 100%;
  height: 100%;
  background-color: rgb(0, 0, 0, 0.7);
  z-index: 10;
  display: flex;
  align-items: center;
  justify-content: center;
}
.modal {
  width: 750px;
  background-color: white;
  border-radius: 10px;
  padding: 30px;
  position: relative;
  display: flex;
  flex-direction: column;
}
.modal button {
  padding: 10px 20px;
  font-size: 20px;
  width: 100%;
  background-color: rgb(65, 31, 109);
  border: none;
  color: aliceblue;
  cursor: pointer;
  border-radius: 4px;
  margin-top: 10px;
}
.modal p{
  color: rgb(163, 20, 20);
}
.modal .close {
  background-color: rgb(163, 20, 20);
}
</style>
