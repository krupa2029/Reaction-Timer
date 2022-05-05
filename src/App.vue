<template>
 <h1>Let's see how fast you are!!</h1> 
 <button @click="startGame" :disabled="isPlaying">Play</button>
 <Block :delay="delay" v-if="isPlaying" @end="endGame" />
 <p>Reaction time: {{score}}</p>
</template>

<script>
import Block from './components/Block.vue';

export default {
  name: 'App',
  components: {
    Block
  },
  data() {
    return {
      isPlaying: false,
      delay: null,
      score: null
    }
  },
  methods: {
    startGame(){
      this.delay = 2000 + Math.random() * 5000;
      this.isPlaying = true;
      console.log(this.delay);
    },
    endGame(reactionTime){
      this.score = reactionTime
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
