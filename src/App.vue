<template>
  <button
    class="bg-red-400 mt-8 rounded-md p-2 disabled:opacity-50"
    @click="startGame"
    :disabled="isPlaying"
  >
    {{ startGameBtn }}
  </button>
  <Block @end="endGame" v-if="isPlaying" :delay="delay" />
  <Results v-if="isResult" :score="score" />
</template>

<script>
import Results from "./components/Results.vue";
import Block from "./components/Block.vue";

export default {
  name: "App",
  components: {
    Block,
    Results,
  },
  data() {
    return {
      startGameBtn: "Click and start a game!",
      isPlaying: false,
      delay: null,
      score: null,
      isResult: false,
    };
  },
  methods: {
    startGame() {
      this.delay = 2000 + Math.random() * 5000;
      this.isPlaying = true;
      this.isResult = false;
    },
    endGame(reactionTime) {
      this.score = reactionTime;
      this.isResult = true;
      this.isPlaying = !this.isPlaying;
      console.log(this.score);
    },
  },
};
</script>
