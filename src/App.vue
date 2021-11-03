<template>
  <h1>CLICKOMANIA</h1>
  <button @click="startGame()" :disabled="Playing">play</button>
  <block v-if="Playing" v-bind:delay="delay" @end="endGame" />
  <results v-if="showResults" :score="score" />
</template>

<script>
import block from './components/block.vue';
import results from './components/results.vue';

export default {
  name: 'App',
  components: {
    block,
    results,
  },
  data() {
    return {
      delay: null,
      score: null,
      Playing: false,
      showResults: false,
    };
  },
  methods: {
    startGame() {
      this.delay = 1000 + Math.random() * 3000;
      this.Playing = true;
      this.showResults = false;
    },
    endGame(reactionTime) {
      this.score = reactionTime;
      this.Playing = false;
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
h1{
  color: green;
  font-size: xx-large;
  font-weight: 300;
}
button{
  color: green;
  background-color: #bdbdbd;
  font-size: medium;
  border: none;
  width: 100px;
  height: 50px;
  border-radius: 100px;
}
button:active{
  background-color: grey;
}
h3{
  color: green;
}
</style>
