<template>
  <div
    class="tile"
    :class="`${number.value === 16 ? 'disabled' : ''} slot--${number.index} ${
      number.value === number.index + 1 ? 'currect' : ''
    }`"
    @click="
      {
        moveTiles(number);
      }
    "
  >
    <p v-if="number.value !== 16">{{ number.value }}</p>
  </div>
</template>

<style scoped>
@import "./style.scss";
</style>

<script>
export default {
  name: "Tiles",
  props: ['number','moveTiles'],
  setup() {
    return {};
  },
};
</script>