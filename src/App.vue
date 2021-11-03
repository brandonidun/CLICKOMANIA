<template>
<h1>CLICKOMANIA</h1>
 <button @click="startGame()" :disabled= "Playing">
    play
  </button>
<block v-if="Playing" v-bind:delay="delay" @end="endGame"/>
<results v-if="showResults" :score="score"/>
</template>

<script>
import block from './components/block.vue'
import results from "./components/results.vue";

export default {
  name: 'App',
  components: {
    block, results
  },
  data() {
    return {
    delay: null,
    score: null,
    Playing: false,
    showResults: false,
  }
  },
  methods: {    
    startGame(){
      this.delay = 2000 + Math.random() * 100
      this.Playing = true
      this.showResults = false
    },
    endGame(reactionTime){
      this.score = reactionTime
      this.Playing = false
      this.showResults = true
    },
    }
}
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
</style>
