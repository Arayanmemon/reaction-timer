<template>
  <div v-if="!showBlock" @click="harami" class="block2">Don't Click</div>
  <div class="block" v-if="showBlock" @click="stopTimer">
    Click me
  </div>
</template>

<script>
export default {
  props: ['delay'],
  data() {
    return {
      showBlock : false,
      timer : null,
      reaction: 0
    }
  },
  mounted() {
    setTimeout(()=>{
      this.showBlock = true
      this.startTimer()
    }, this.delay)
  },
  methods: {
    startTimer(){
        this.timer = setInterval(()=>{
          this.reaction += 10
        },10)
    },
    stopTimer(){
      clearInterval(this.timer)
      this.showBlock = false
      this.$emit('stop', this.reaction)
    },
    harami(){
     alert("Don't click until pink box shows")
    }
  },
}
</script>

<style >
.block{
display: inline-block;
width: 300px;
background-color: #f06eaf;
margin: 40px, auto;
padding: 100px 20px;
border-radius: 10px;
color: white;
}   
.block2{
display: inline-block;
width: 300px;
background-color: white;
margin: 40px, auto;
padding: 100px 20px;
border-radius: 10px;
}   
</style>