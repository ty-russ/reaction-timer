<template>
  <h1>Ninja reaction timer</h1>
  <button @click="onclick" class="btn" :disabled="isPlaying">Go!</button>
  <Block v-if="isPlaying" :Delay="Delay" @reacted="endGame" />
  <Results v-if="showResults" :score="score" />
</template>

<script>
import Block from "./components/Block.vue";
import Results from "./components/Results.vue";
export default {
  name: "App",
  components: {
    Block,
    Results,
  },
  data() {
    return {
      isPlaying: false,
      Delay: null,
      score: null,
      showResults: false,
    };
  },
  methods: {
    onclick() {
      this.Delay = 2000 + Math.random() * 5000;
      this.isPlaying = true;
      this.showResults = false;
    },
    endGame(reactionTime) {
      this.score = reactionTime;
      this.isPlaying = false;
      this.showResults = true;
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
  color: #2c3e50;
  margin-top: 60px;
}
.btn {
  width: 50px;
  height: 30px;
  background: green;
  color: greenyellow;
}
.btn[disabled] {
  width: 50px;
  height: 30px;
  background: red;
  cursor: not-allowed;
  opacity: 0.2;
}
</style>
