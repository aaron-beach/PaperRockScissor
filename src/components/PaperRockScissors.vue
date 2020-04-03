<template>
  <div class="paper_rock_scissors">
    <h1 class="game-wins">Wins: {{ wins }}</h1>
    <h1 class="game-loses">Loses: {{ loses }}</h1>
    <div v-bind:class="active" v-on:click.prevent>
      <button class="rock game-btn" v-on:click="makeActive('rock')">
        Rock
        <img src="@/assets/rock.png" alt="rock image" class="rock-image" />
      </button>
      <button class="paper game-btn" v-on:click="makeActive('paper')">
        Paper
        <img src="@/assets/paper.png" alt="paper image" class="paper-image" />
      </button>
      <button class="scissors game-btn" v-on:click="makeActive('scissors')">
        Scissors
        <img
          src="@/assets/scissors.png"
          alt="scissors image"
          class="scissors-image"
        />
      </button>
    </div>
    <h1 v-if="opponent != 'home'">I choose {{ opponent }}</h1>
    <h2 v-if="winner">{{ active }}! You Win!</h2>
    <h2 v-if="loser">{{ active }}. You Lose!</h2>
    <h2 v-if="tied">You Tied!</h2>
  </div>
</template>
<script>
export default {
  name: "PaperRockScissors",
  data() {
    return {
      active: "Pick your weapon!",
      choices: ["rock", "paper", "scissors"],
      opponent: "home",
      winner: false,
      loser: false,
      tied: false,
      wins: 0,
      loses: 0
    };
  },
  methods: {
    makeActive: function(item) {
      // When a model is changed, the view will be automatically updated.
      this.active = item;
      this.loser = false;
      this.tied = false;
      this.winner = false;
      this.randomChoice();
      this.isWinner();
    },
    isWinner: function() {
      if (this.opponent == this.active) {
        this.tied = true;
      } else if (
        this.opponent == this.choices[0] &&
        this.active == this.choices[1]
      ) {
        this.winner = true;
        this.wins++;
      } else if (
        this.opponent == this.choices[1] &&
        this.active == this.choices[2]
      ) {
        this.winner = true;
        this.wins++;
      } else if (
        this.opponent == this.choices[2] &&
        this.active == this.choices[0]
      ) {
        this.winner = true;
        this.wins++;
      } else {
        this.loser = true;
        this.loses++;
      }
    },
    randomChoice: function() {
      let randomIndex = Math.floor(Math.random() * 2);
      this.opponent = this.choices[randomIndex];
    }
  }
};
</script>

<style scoped>
.game-btn {
  border-radius: 100%;
  width: fit-content;
  outline: none;
  border: none;
}
.rock-image,
.scissors-image,
.paper-image {
  width: 200px;
  height: 200px;
  border-radius: 100%;
}
</style>
