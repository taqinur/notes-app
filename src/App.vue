<script setup>
</script>

<template>
  <main>
    <div class="overlay">
      <div class="modal">
        <textarea name="note" id="note" cols="30" rows="10"></textarea>
        <button>Confirm</button>
        <button class="close">Close</button>
      </div>
    </div>
    <div class="container">
      <header>
        <h1>My Notes</h1>
        <button>Add new</button>
      </header>
      <div class="cards-container">
        <div class="card">
          <p class="main-text">Lorem ipsum dolor sit amet consectetur adipisicing elit. Commodi, blanditiis deserunt minima dolorum ad culpa nisi corrupti.</p>
          <p class="date">30/1/2023</p>
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

  header{
    display: flex;
    justify-content: space-between;
    align-items: center;
  }
  h1{
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
  .cards-container{
    display: flex;
    flex-wrap: wrap;
  }
  .card{
    width: 250px;
    height: 250px;
    background-color: darkslategray;
    padding: 10px;
    display: flex;
    flex-direction: column;
    justify-content: space-between;
    margin-right: 20px;
    margin-bottom: 20px;
    border-radius: 10px;
    color: white;
  }
  .overlay{
    position: absolute;
    width: 100%;
    height: 100%;
    background-color: rgb(0, 0, 0, 0.70);
    z-index: 10;
    display: flex;
    align-items: center;
    justify-content: center;
  }
  .modal{
    width: 750px;
    background-color: white;
    border-radius: 10px;
    padding: 30px;
    position: relative;
    display: flex;
    flex-direction: column;
  }
  .modal button{
    padding: 10px 20px;
    font-size: 20px;
    width: 100%;
    background-color: rgb(66, 42, 66);
    border: none;
    color: aliceblue;
    cursor: pointer;
    border-radius: 4px;
    margin-top: 10px;
  }
  .modal .close{
    background-color: rgb(100, 9, 9);
  }
</style>
