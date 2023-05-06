<template>
  <div class="board-wrapper">
    <div class="title">
      <div class="logo">
        <img src="./../../assets/images/iconmonstr-puzzle-15.svg" />
      </div>
      <div class="text">
        <p>Welcom To This Game Puzzle</p>
      </div>
    </div>
    <div class="board">
      <Overlay />
      <Tiles
        :key="{ index }"
        v-for="(number, index) in numbers"
        :number="number"
        :moveTiles="moveTiles"
      />
    </div>
    <WinnerMessage :numbers="numbers" :resetGame="resetGame" />
    <StartNewgame
      v-if="!numbers.every((number) => number.value === number.index + 1)"
      :numbers="numbers"
      :resetGame="resetGame"
    />
  </div>
</template>

<style scoped>
@import "./style.scss";
</style>

<script>
import Tiles from "./../Tiles/index.vue";
import { onMounted, ref } from "vue";
import StartNewgame from "./../StartNewgame/index.vue";
import Overlay from "./../Overlay/index.vue";
import WinnerMessage from "./../WinnerMessage/index.vue";

export default {
  name: "Boards",
  setup() {
    let numbers = ref([]);

    const tiles = () =>
      new Array(16)
        .fill()
        .map((item, index) => index + 1)
        .sort(() => Math.random() - 0.5)
        .map((item, index) => ({ value: item, index }));

    const moveTiles = (tile) => {
      const index16 = numbers.value.find((item) => item.value === 16).index;
      if (
        ![index16 - 1, index16 + 1, index16 - 4, index16 + 4].includes(
          tile.index
        )
      )
        return;

      let newNumbers = [...numbers.value].map((number) => {
        if (number.index !== index16 && number.index !== tile.index)
          return number;
        else if (number.value === 16) return { value: 16, index: tile.index };

        return { value: tile.value, index: index16 };
      });

      numbers.value = newNumbers;
    };

    const resetGame = () => {
      numbers.value = tiles();
    };

    onMounted(() => {
      console.log(tiles());
      resetGame();
    });

    return {
      resetGame,
      moveTiles,
      numbers,
    };
  },
  components: { Tiles, StartNewgame, Overlay, WinnerMessage },
};
</script>