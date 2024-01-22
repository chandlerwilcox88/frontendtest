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
  flex-direction: row;
  align-items: flex-start;
  justify-content: center;
  background-color: #0f0f0f;
  height: 100vh;
  width: 100vw;
}

@media (max-width: 1024px) {
  .container {
    flex-direction: column;
  }
}
</style>
