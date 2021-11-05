<template>
  <div class="start-menu" v-if="showStartMenu">
    <h1>CLICKOMANIA</h1>
    <select v-model="gameTime">
      <option value="10000">hard(10secs)</option>
      <option value="15000">mid(15secs)</option>
      <option value="30000">easy(30secs)</option>
    </select>
    <button @click="startGame()" :disabled="Playing">play</button>
    <br />
    <!-- <select v-model="Planet">
    <option value="../public/mercury.jpg">mercury</option>
    <option value="../public/venus.jpg">venus</option>
    <option value="../public/neptune.jpg">neptune</option>
    <option value="../public/jupiter.jpg">jupiter</option>
  </select> -->
  </div>
  <h1 v-if="showPrep" id="prep">{{ this.prep }}</h1>
  <block
    v-if="Playing"
    v-bind:delay="delay"
    :planet="planet"
    :gameTime="gameTime"
    @clicks="endGame"
  />
  <results v-if="showResults" :score="score" />
</template>

<script>
import block from "./components/block.vue";
import results from "./components/results.vue";

export default {
  name: "App",
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
      showStartMenu: true,
      gameTime: "10000",
      showPrep: true,
      prep: "",
      planet: "",
    };
  },
  methods: {
    startGame() {
      this.clicks = 0;
      console.log(12);
      setTimeout(() => {
        this.prep = "ready";
      }, 0);
      setTimeout(() => {
        this.prep = "steady";
      }, 1000);
      setTimeout(() => {
        this.prep = "GO!";
      }, 2500);
      setTimeout(() => {
        this.showPrep = false;
      }, 2700);
      this.showStartMenu = false;
      this.delay = 2800;
      this.Playing = true;
      this.showResults = false;
      setTimeout(() => {
        this.showStartMenu = true;
        this.Playing = false;
        this.showResults = true;
      }, this.gameTime);
    },
    endGame(clicks) {
        this.score = clicks;
    },
  },
};
</script>

<style>
@import url("https://fonts.googleapis.com/css2?family=Fruktur&display=swap");

#app {
  font-family: fruktur;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}
.start-menu {
  margin-top: 310px;
}
#prep {
  margin-top: 450px;
}
h1 {
  color: rgba(255, 255, 255, 0.5);
  font-size: 70px;
  font-weight: 100;
}
button {
  color: white;
  background-color: rgba(255, 255, 255, 0.247);
  font-size: medium;
  border: none;
  width: 100px;
  height: 50px;
  border-radius: 10px;
}
button:active {
  background-color: grey;
}
h3 {
  font-weight: 200;
  color: rgba(255, 255, 255, 0.562);
}
select {
  color: white;
  padding: 10px 6px;
  margin-right: 20px;
  background-color: rgba(255, 255, 255, 0.288);
  border: none;
  border-radius: 5px;
}
body {
  background-image: url(../public/photo-1534796636912-3b95b3ab5986.jpeg);
  background-size: cover;
}
.reaction-card {
  background-image: url(../public/venus.jpg);
  background-repeat: no-repeat;
  background-size: cover;
}
</style>
