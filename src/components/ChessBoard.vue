<script setup>
import { ref, onMounted, defineEmits } from "vue";

const board = ref([]);
const emit = defineEmits(["square-clicked"]);
const clickedSquares = ref([]);

const createBoard = () => {
  for (let i = 0; i < 8; i++) {
    board.value[i] = [];
    for (let j = 0; j < 8; j++) {
      board.value[i][j] = { color: (i + j) % 2 === 0 ? "white" : "black" };
    }
  }
};

const clickSquare = (row, col) => {
  emit("square-clicked", { row, col });
};

const isClicked = (row, col) => {
  return clickedSquares.value.some(
    (clickedSquare) => clickedSquare.row === row && clickedSquare.col === col
  );
};

// Lifecycle hooks
onMounted(createBoard);
</script>

<template>
  <div class="chessboard">
    <div v-for="(row, i) in board" :key="i" class="row">
      <div
        v-for="(square, j) in row"
        :key="j"
        :class="['square', square.color, isClicked(i, j) ? 'clicked' : '']"
        @click="() => clickSquare(i, j)"
      ></div>
    </div>
  </div>
</template>

<style lang="scss" scoped>
.chessboard {
  display: flex;
  flex-direction: column;
  height: 500px;
  max-width: 500px;
  margin: auto;
  background-color: red;
}
.row {
  display: flex;
  flex: 1;
}
.square {
  flex: 1;
  padding-top: 12.5%;
  position: relative;
}
.white {
  background-color: #e9edcc;
}
.black {
  background-color: #779954;
}
.clicked {
  background-color: #bccb4a;
}
</style>
