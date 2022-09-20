<template>
  <div>
      <h1>Reaction timer</h1>
      <button @click="start" :disabled="isplaying">Play</button>
  </div><br>
  <Block v-if="isplaying" :delay="delay" @stop="stopGame" />
  <p v-if="!isplaying">A popup box will show down below just click it as fast as you can</p>
  <p v-if="showResult">Result : {{score}} ms</p>
  <p v-if="showResult">{{Regard}}</p>
</template>

<script>
import Block from './components/Block.vue'
export default{
  data() {
      return {
          isplaying : false,
          delay : null,
          score: null,
          showResult : false,
          Regard: "Keep it up"
      }
  },
  components: {Block},
  methods: {
      start(){
          this.delay = 2000 + Math.random()*5000;
          this.isplaying = true; 
          this.showResult = false
      },
      stopGame(reaction){
        this.score = reaction
        this.showResult = true
        this.isplaying = false
        if (this.score <= 250) {
          this.Regard = "Fast as Lightning ⚡"
        }
        else if(this.score >200 && this.score <=500){
            this.Regard = "Keep practicing boss 👍"
        }
        else{
          this.Regard = "So slow buddy 😥"
        }
      }
  },
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
button{
  padding-left: 10px;
  padding-right: 10px;
  margin: 5px;
  background-color: aliceblue;
  border: 1px solid black;
}
</style>
