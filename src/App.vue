<script setup>
import { ref } from "vue";
import ChessBoard from "./components/ChessBoard.vue";
import SideBar from "./components/SideBar.vue";

const clickedSquares = ref([]);

const handleSquareClick = (square) => {
  clickedSquares.value.push(square);
  console.log(clickedSquares.value);
};
</script>

<template>
  <div class="container">
    <chess-board @square-clicked="handleSquareClick" />
    <side-bar :clickedSquares="clickedSquares" />
  </div>
</template>

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
