<template>
  <h1>Reaction Timer</h1>
  <button @click="start" :disabled="isPlaying">
    Play
  </button>
  
  <Block v-if="isPlaying" :delay="delay" @end="endGame"/>     
  <Results :score="score" v-if="showResults" />                                  
</template>

<script>
import Block from './components/Block'
import Results from './components/Results'

export default {
  name: 'App',
  components: {
    Block,
    Results
  },
  data() {
    return {
      isPlaying: false,
      delay: null,
      score: null,
      showResults: false,
      score: null
    }
  },

  methods: {
    start() {
      this.isPlaying = true
      this.delay = 2000 + Math.random() * 5000
      this.showResults = false  
    },
    endGame(reactionTime) {
      this.isPlaying = false
      this.score = reactionTime
      this.showResults = true
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
body{
  margin: 0;
}
button {
  padding: 10px 20px;
  letter-spacing: 1px;
  border-radius: 4px;
  font-size: 16px;
  border: 1px solid transparent;
  cursor: pointer;
  color: white;
  background-color: #0faf87;
}
button[disabled] {
  opacity: 0.2;
  cursor:  not-allowed;
}
</style>
