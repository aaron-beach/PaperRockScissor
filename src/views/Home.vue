<template>
  <div class="home">
    <h1 class="intro-header">
      paper. rock. scissors.
    </h1>
    <paper-rock-scissors />
  </div>
</template>

<script>
// @ is an alias to /src
// import HelloWorld from "@/components/HelloWorld.vue";
import PaperRockScissors from "@/components/PaperRockScissors";
export default {
  name: "Home",
  components: {
    // HelloWorld
    PaperRockScissors
  }
};
</script>
<style scoped>
.intro-header {
  margin: 0 auto;
  text-transform: capitalize;
}
</style>
