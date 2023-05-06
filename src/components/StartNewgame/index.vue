<template>
  <div
    class="start-new-game"
    @click="
      {
        resetGame();
      }
    "
  >
    <button
      type="button"
      :class="`button ${activeClassButton ? 'active' : ''}`"
    >
      <p>New Game</p>
    </button>
  </div>
</template>

<style scoped>
@import "./style.scss";
</style>

<script>
export default {
  name: "StartNewgame",
  setup() {
    return {};
  },
  props: ["resetGame"],
};
</script>