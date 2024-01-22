<template>
  <div class="sidebar">
    <div class="title">Game Moves</div>
    <ol>
      <li>Move</li>
      <li>Move</li>
    </ol>
  </div>
</template>

<script setup></script>

<style lang="scss" scoped>
.sidebar {
  display: flex;
  flex: 1;
  flex-direction: column;
  background-color: #262522;
  padding: 2rem 1rem;
  margin: 3rem;
  border-radius: 0.3rem;
}
@media (min-width: 1024px) {
  .sidebar {
    flex: 1;
  }
}
.title {
  color: #c3c2c2;
  font-size: 1.4rem;
  font-weight: bold;
}
ol {
  list-style: none;
  padding: 0;
  margin: 0;
}
li {
  color: #c3c2c2;
  font-size: 0.8rem;
  font-weight: bold;
  margin: 0.5rem 0;
  &:before {
    color: #939190;
  }
}
</style>
