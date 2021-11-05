<template>
  <div class="block" v-if="showBlock" @click="stopTimer()" :style="{left: x +'px', top: y +'px',}">
    <div class="reaction-card">
    <img src="/public/297404.svg" alt="/">
    <h2>CLICK!</h2>
    </div> 
  </div>
</template>

<script>
export default {
props: ['delay', 'gameTime', 'planet'],
data(){
  return {
    showBlock: false,
    time: null,
    reactionTime: 0,
    x: null,
    y: null,
    clicks: 0,
    totalClicks: 0,
  }
},
mounted(){
setTimeout(() => {
  this.showBlock = true
  this.startTimer()
  this.divLocation()
  console.log("done")
}, this.delay)
},

methods: {
  startTimer(){
    this.showBlock= true
    // this.clicks = setInterval(() => {
    //   this.totalClicks += 1
    //   },1)
    },
  stopTimer(){
    this.divLocation()  
    this.clicks += 1
    // clearInterval(this.clicks)
    this.$emit("clicks", this.clicks)
    // this.$emit("end", this.reactionTime)
    console.log(this.clicks)
  
    },
  divLocation(){
    this.x = (window.innerWidth - 200) * Math.random();
    this.y = (window.innerHeight - 200) * Math.random(); 
  },
}
}
</script>

<style>
.block{
  margin-top: 30px;
  display: flex;
  align-items: center;
  justify-content: center;
  position: fixed;
  background-image: url(/public/photo-1465101162946-4377e57745c3.jpeg);
}
.reaction-card {
  background-image: url(/public/venus.jpg);
  display: flex;
  align-items: center;
  justify-content: center;
  border-radius: 1000px;
  width: 200px;
  height: 200px;
}
h2{
  color: rgba(255, 255, 255, 0.397);
}
</style>