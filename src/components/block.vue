<template>
  <div class="block" v-if="showBlock" @click="stopTimer()" :style="{left: x +'px', top: y +'px'}">
    <div class="reaction-card">
    <h2>CLICK!</h2>
    </div> 
  </div>
</template>

<script>
export default {
props: ['delay', 'gameTime'],
data(){
  return {
    showBlock: false,
    time: null,
    reactionTime: 0,
    x: null,
    y: null,
    clicks: null,
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
    clearInterval(this.clicks)
    this.$emit("clicks", this.clicks)
    this.$emit("end", this.reactionTime)
    console.log(this.clicks)
  
    },
  divLocation(){
    this.x = 50 + Math.random()*1428
    this.y = 50 + Math.random()*685
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
}
.reaction-card {
  background-color: grey;
  display: flex;
  align-items: center;
  justify-content: center;
  border-radius: 1000px;
  width: 200px;
  height: 200px;
}
h2{
  color: white;
}
</style>