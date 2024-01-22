<script setup>
import { ref, onMounted, defineEmits } from "vue";

const board = ref([]);
const emit = defineEmits(["square-clicked"]);
const clickedSquares = ref([]);

const createBoard = () => {
  const columns = ["A", "B", "C", "D", "E", "F", "G", "H"];
  for (let i = 0; i < 8; i++) {
    board.value[i] = [];
    for (let j = 0; j < 8; j++) {
      board.value[i][j] = {
        color: (i + j) % 2 === 0 ? "white" : "black",
        position: `${columns[j]}${i + 1}`,
      };
    }
  }
};

const clickSquare = (row, col) => {
  const alreadyClicked = clickedSquares.value.some(
    (square) => square.row === row && square.col === col
  );

  if (!alreadyClicked) {
    const position = board.value[row][col].position;
    emit("square-clicked", position);
    clickedSquares.value.push({ row, col, position });
  }
};

const isClicked = (row, col) => {
  return clickedSquares.value.some(
    (square) => square.row === row && square.col === col
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
  width: 100vh;
  max-width: 100vw;
  aspect-ratio: 1;
}
@media (max-width: 1094px) {
  .chessboard {
    margin: 0 auto;
  }
}
.row {
  display: flex;
  flex: 1 0 12.5%;
}
.square {
  position: relative;
  flex: 1 0 12.5%;
  padding-top: 12.5%;
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
