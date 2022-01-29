<template>
    <h1>Time Reaction Game</h1>
    <button @click="start" :disabled="isPlaying" >PLAY</button>
    <Block  v-if="isPlaying" :delay="delay" @end="endGame"/>
    <Results v-if="showResults" :score="score" />
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
  data() {
    return {
      isPlaying: false,
      delay: null,
      score: null,
      showResults: false
    }
  },
  methods: {
    start() {
      this.delay = 2000 + Math.random() * 4000
      this.isPlaying = true
      this.showResults = false
    },
    endGame(reactionTimer) {
      this.score = reactionTimer
      this.isPlaying = false
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
  color: #333333;
  margin-top: 60px;
}
button {
  background: #333333;
  color: #e3e3e3;
  border: none;
  padding: 8px 16px;
  border-radius: 4px;
  font-size: 1rem;
  letter-spacing: 1px;
  cursor: pointer;
  margin: 10px;
}
button[disabled] {
  opacity: 0.2;
  cursor: not-allowed;
}
</style>
