<script setup>
import { defineProps } from "vue";
const props = defineProps({
  clickedSquares: Array,
});
</script>

<template>
  <div class="sidebar">
    <div class="title">Game Moves</div>
    <div class="instructions" v-if="props.clickedSquares == 0">
      Click the chessboard to make a move
    </div>
    <ol>
      <li v-for="(square, index) in props.clickedSquares" :key="index">
        {{ square }}
      </li>
    </ol>
  </div>
</template>

<style lang="scss" scoped>
.sidebar {
  display: flex;
  flex-direction: column;
  background-color: #262522;
  border-radius: 0.3rem;
  margin: 1rem;
}
@media (min-width: 1094px) {
  .sidebar {
    flex: 1;
    max-height: 80vh;
    overflow-y: auto;
    margin: 3rem;
  }
}
.title {
  color: #c3c2c2;
  font-size: 1.4rem;
  font-weight: bold;
  background-color: #262522;
  padding: 2rem;
  border-radius: 0.3rem;
}
@media (min-width: 1094px) {
  .title {
    position: sticky;
    top: 0;
  }
}
.instructions {
  margin: 0 2rem;
  color: #c3c2c2;
}
ol {
  counter-reset: li;
  list-style: none;
  padding: 0;
  margin-top: 1rem;
}
li {
  color: #c3c2c2;
  font-size: 0.8rem;
  font-weight: 900;
  padding: 0.5rem 2rem;
  &:before {
    margin-right: 0.3rem;
    content: counter(li) ".";
    counter-increment: li;
    color: #939190;
  }
  &:nth-child(even) {
    background-color: #2a2926;
  }
}
</style>
