<template>
  <div class="container">
    <chess-board />
    <side-bar />
  </div>
</template>

<script setup>
import ChessBoard from "./components/ChessBoard.vue";
import SideBar from "./components/SideBar.vue";
</script>

<style>
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
}

.container {
  display: flex;
  flex-direction: column;
  align-items: flex-start;
  justify-content: start;
  background-color: #302e2b;
  height: 100vh;
  width: 100vw;
  transition: all 0.3s ease;
}

@media (min-width: 1024px) {
  .container {
    flex-direction: row;
    justify-content: start;
  }
}
</style>
