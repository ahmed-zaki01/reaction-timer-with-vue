<template>
  <h1>Reaction Timer</h1>
  <button id="play" @click="start" :disabled="isPlaying">Play</button>
  <block v-if="isPlaying" :delay="delay" @end="endGame" />
  <result v-if="showResult" :score="score" />
</template>

<script>
import Block from "./components/Block.vue";
import Result from "./components/Result.vue";
export default {
  name: "App",
  components: { Block, Result },
  data() {
    return {
      isPlaying: false,
      delay: null,
      score: null,
      showResult: false,
    };
  },
  methods: {
    start() {
      this.delay = 2000 + Math.random() * 5000;
      this.isPlaying = true;
      this.showResult = false;
    },
    endGame(reactionTime) {
      this.score = reactionTime;
      this.isPlaying = false;
      this.showResult = true;
    },
  },
};
</script>

<style>
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #444;
  margin-top: 60px;
}
button#play {
  padding: 8px 16px;
  font-size: 1em;
  letter-spacing: 1px;
  background: #0faf87;
  color: #e6e6e6;
  border: none;
  border-radius: 5px;
  cursor: pointer;
}

button#play[disabled] {
  cursor: not-allowed;
  opacity: 0.6;
}
</style>
