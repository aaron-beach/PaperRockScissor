<template>
  <div class="button">
    <ul v-bind:class="active" v-on:click.prevent>
      <button href="#" class="home" v-on:click="makeActive('home')">
        Refresh
      </button>
      <button href="#" class="rock" v-on:click="makeActive('rock')">
        Rock
        <img src="@/assets/rock.png" alt="rock image" class="rock-image" />
      </button>
      <button href="#" class="paper" v-on:click="makeActive('paper')">
        Paper
        <img src="@/assets/paper.png" alt="paper image" class="paper-image" />
      </button>
      <button href="#" class="scissors" v-on:click="makeActive('scissors')">
        Scissors
        <img
          src="@/assets/scissors.png"
          alt="scissors image"
          class="scissors-image"
        />
      </button>
    </ul>
    <h2 class="button-selection">{{ active }} {{ winner }}</h2>
  </div>
</template>

<script>
export default {
  name: "GameButton",
  props: {
    selectedWeapon: {
      type: String,
      required: true,
      validator: function(value) {
        return ["paper", "rock", "scissors"].indexOf(value) !== -1;
      }
    }
  },
  data() {
    return {
      active: "Pick your weapon!",
      choices: ["paper", "rock", "scissors"],
      opponent: "home",
      winner: false
    };
  },
  methods: {
    makeActive: function(item) {
      // When a model is changed, the view will be automatically updated.
      this.active = item;
      this.winner = this.isWinner();
    },
    isWinner: function() {
      if (this.opponent == this.active) {
        return false;
      } else if (
        this.opponent == this.choices[0] &&
        this.active == this.choices[1]
      ) {
        return true;
      } else if (
        this.opponent == this.choices[1] &&
        this.active == this.choices[2]
      ) {
        return true;
      } else if (
        this.opponent == this.choices[2] &&
        this.active == this.choices[0]
      ) {
        return true;
      } else {
        return false;
      }
    }
  },
  updated() {
    let randomIndex = Math.floor(Math.random() * 2);
    this.opponent = this.choices[randomIndex];
  }
};
</script>

<style scoped>
.button {
  width: 80%;
  height: 200px;
}
.rock-image,
.scissors-image,
.paper-image {
  width: 200px;
  border-radius: 100%;
}
</style>
