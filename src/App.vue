<template>
  <h1>Mr. Pro Reaction Timer! {{ titel }}</h1>
  <button @click="start" :disabled="isPlaying">Play</button>
  <block v-if="isPlaying" :delay="delay" @end="endGame" />
  <!-- <p v-if="score">Reaction Time: {{ score }} ms</p> -->
  <results v-if="score" :score="score" />
</template>

<script>
import Block from "./components/Block.vue";
import Results from "./components/Results.vue";
export default {
  name: "App",
  components: { Block, Results },
  data() {
    return {
      isPlaying: false,
      delay: null,
      score: null,
    };
  },
  methods: {
    start() {
      this.delay = 2000 + Math.random() * 5000;
      this.isPlaying = true;
      this.score = null;
      // console.log(this.delay)
    },
    endGame(date) {
      console.log("emmit date is: " + date);
      this.score = date;
      this.isPlaying = false;
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
button{
  background: #0faf87;
  color: white;
  padding: 8px 16px;
  border: none;
  border-radius: 5px;
  font-size: 1.2rem;
  cursor: pointer;
  margin: 10px;
}

button[disabled]{
  opacity: 0.5;
  cursor: not-allowed;
}
</style>
