<template>
  <div class="block" v-if="showBlock" @click="stopTimer()">
    <div class="reaction-card">
    <h1>CLICK!</h1>
    </div> 
  </div>
</template>

<script>
export default {
props: ['delay'],
data(){
  return {
    showBlock: false,
    time: null,
    reactionTime: 0,
    x: null,
    y: null,
  }
},
mounted(){
setTimeout(() => {
  this.showBlock = true
  this.startTimer()
}, this.delay)
},

methods: {
  startTimer(){
    this.showBlock= true
    this.time = setInterval(() => {
      this.reactionTime += 10
      },10)
    },
  stopTimer(){
    this.showBlock= false
    clearInterval(this.time)
    this.$emit("end", this.reactionTime)
    }
  }
}
</script>

<style>
.block{
  margin-top: 30px;
  display: flex;
  align-items: center;
  justify-content: center;
}
.reaction-card {
  background-color: pink;
  display: flex;
  align-items: center;
  justify-content: center;
  border-radius: 1000px;
  width: 200px;
  height: 200px;
}
</style>