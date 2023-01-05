<template>
 <h1>Hi, let's check your reaction time</h1>
 <h2>It's simple just click on the button and wait for green block then click on it</h2>
 <button id="buttonstart" @click="start" :disabled="isPlaying">Let's Start!</button>
 <Block v-if="isPlaying" :delay="delay" @result="endGame"/>
 <Results v-if="showScore" :score="score"/>
 <button id="btndetails" @click="toggleDetails">About the test</button>
 <div id="testinfo" v-if="showDetails">
 <p>This is a simple tool to measure your reaction time.</p>
 <p> According to  <a href="https://humanbenchmark.com/tests/reactiontime/statistics">HumanBenchmark</a> the average reaction time is<span id="average"> 284 milliseconds</span>.</p>
 <p>In addition to measuring your reaction time, this test is affected by the latency of your computer and monitor. </p>
 <p> Using a fast computer and low latency / high framerate monitor will improve your score.</p>
 <button id="btnclose" @click="toggleDetails">close</button>
 </div>  

</template>

<script>
import Block from './components/block.vue'
import Results from './components/Results.vue'

export default {
  name: 'App',
  components: {
    Block,
    Results
  },
  data(){
    return {
      isPlaying: false,
      delay: null,
      score: null,
      showScore: false,
      showDetails: false
    }
  },
  methods: {
    start(){
      this.isPlaying = true 
      this.delay = 2000 + Math.random() * 5000
      this.showScore = false
    },
    endGame(reactionTime){
      this.score = reactionTime
      this.isPlaying = false
      this.showScore = true
    },
    toggleDetails(){
      this.showDetails = !this.showDetails

    }
  },
}
</script>

<style>
#app {
  display: flex;
  flex-direction: column;
  justify-content: center;
  align-items: center;
  font-family: 'Courier New', Courier, monospace;
  margin-top:60px;


}
</style>
