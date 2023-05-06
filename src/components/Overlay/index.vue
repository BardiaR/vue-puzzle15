<template>
  <div
    v-for="(item, index) in new Array(16).fill()"
    className="overlay"
    :key="index"
  ></div>
</template>

<style scoped>
@import "./style.scss";
</style>

<script>
export default {
  name: "Overlay",
  setup() {},
};
</script>