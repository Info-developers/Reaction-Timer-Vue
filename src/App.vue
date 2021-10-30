<template>
  <h1>Reaction Timer Game</h1>
  <button @click="start" :disabled="isPlaying">Play</button>
  <Block v-if="isPlaying" :delay="delay" @end="endGame" />
  <Results v-if="showResult" :score="score" />
  <!-- <p v-if="showResult">Reaction Time is {{Result}}</p> -->
</template>

<script>
import Block from './components/Block.vue'
import Results from './components/Results.vue'
export default {
name:'App',
components:{Block,Results},
data(){
  return {
    isPlaying:false,
    showResult:false,
    delay:null,
    score:0
  }
},
methods:{
  start(){
    this.delay = 2000 + Math.random() * 5000
    this.isPlaying = true
    this.showResult = false
  },
  endGame(reactionTime){
    this.score = reactionTime
    this.isPlaying = false
    this.showResult = true
    console.log(reactionTime)
  }
}
}
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
  border: none;
  padding: 8px 16px;
  margin: 10px;
  cursor: pointer;
  font-size: 16px;
  border-radius: 4px;
}
button[disabled]{
  cursor: not-allowed;
  opacity: 0.2;
}
</style>