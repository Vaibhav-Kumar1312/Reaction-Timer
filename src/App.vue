<template>
  <h1>Reaction Timer</h1>
  <button @click ="start" :disabled="isPlaying">Play</button>
  <Block v-if="isPlaying" :delay="delay" @end ="endGame"/>
  <Results v-if="displayScore" :reactTime="score"/>
  <!-- <p v-if="displayScore">REACTION TIME : {{this.score}}</p> -->
</template>

<script>
import Block from './components/Block.vue'
import Results from './components/Results.vue'
export default {
  name: 'App',
  components: {
    Block, 
    Results
  },
  data(){
    return {
      isPlaying : false,
      delay : null, 
      score: null,
      displayScore : false
    }
  },
  methods : {
start(){
  this.delay = 2000 + Math.random() * 5000
  this.isPlaying = true
  this.displayScore = false
  // console.log(this.delay)
},
endGame(reactionTime){
this.score = reactionTime
this.displayScore = true
this.isPlaying = false
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
  color: #2c3e50;
  margin-top: 60px;
}
</style>
