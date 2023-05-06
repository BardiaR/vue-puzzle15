<script>
import Boards from "./components/Boards/index.vue";

export default {
  name: "App",
  components: { Boards },
};
</script>

<template>
  <div class="app">
    <Boards />
  </div>
</template>

<style>
@import "./assets/scss/main.scss";
</style>