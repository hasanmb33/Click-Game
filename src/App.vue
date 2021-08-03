<template>
  
  <h1>Click Game</h1>  
  <button @click="start" :disabled="isPlay">play</button>

<Block v-if="isPlay" :delay="delay"/>
</template>

<script>
import Block from './components/Block.vue'

export default {
  name: 'App',
  components: {
    Block
  },
  data() {
    return{
      isPlay: false,
      delay: 1000,
      result: null
    }
  },
  methods: {
    start(){
      this.isPlay = true
      this.delay = 0 + Math.random()*1000
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
</style>
