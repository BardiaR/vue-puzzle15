<template>
  <div
    class="winner-message"
    v-if="numbers.every((number) => number.value === number.index + 1)"
  >
    <p>congraduation...!!! You Won.</p>

    <StartNewgame :resetGame="resetGame" />
  </div>
</template>

<style scoped>
@import "./style.scss";
</style>

<script>
import StartNewgame from "./../StartNewgame/index.vue";

export default {
  name: "WinnerMessage",
  props: ['numbers','resetGame'],
  setup() {
    return {};
  },

  components: { StartNewgame },
};
</script>