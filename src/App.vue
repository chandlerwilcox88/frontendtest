<script setup>
import { ref } from "vue";
import ChessBoard from "./components/ChessBoard.vue";
import SideBar from "./components/SideBar.vue";

const clickedSquares = ref([]);

const handleSquareClick = (square) => {
  clickedSquares.value.push(square);
};
</script>

<template>
  <div class="container">
    <chess-board @square-clicked="handleSquareClick" />
    <side-bar :clickedSquares="clickedSquares" />
  </div>
</template>

<style>
html,
body {
  background-color: #302e2b;
}
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
}

.container {
  display: flex;
  flex-direction: column;
  align-items: center;
  justify-content: start;
  background-color: #302e2b;
  transition: all 0.3s ease;
  overflow-x: hidden;
}

@media (min-width: 1180px) {
  .container {
    flex-direction: row;
    align-items: start;
    justify-content: start;
    height: 100vh;
    overflow: hidden;
  }
}
</style>
