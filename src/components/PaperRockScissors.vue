<template>
  <div class="paper_rock_scissors">
    <game-button selectedWeapon="rock" />
  </div>
</template>

<script>
import GameButton from "./GameButton";
export default {
  name: "PaperRockScissors",
  components: {
    GameButton
  }
};
</script>

<style>
.paper_rock_scissors {
  height: 90vh;
  width: 90vw;
  margin: 0 auto;
}
</style>
