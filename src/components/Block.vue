<template>
  <div class="block" v-if="showTimer" @click="stopTimer">
      Click Me
  </div>
</template>

<script>
export default {
    props:['delay'],
    data(){
        return {
            showTimer:false,
            timer:null,
            reactionTime:0,
        }
    },
    mounted(){
        setTimeout(()=>{
            this.showTimer = true
            this.startTimer()
        }, this.delay)
    },
    methods:{
        startTimer(){
            this.timer = setInterval( () => {
                this.reactionTime += 10
            }, 10)
        }, 
        stopTimer(){
            clearInterval(this.timer)
            this.$emit('end', this.reactionTime)
        }
    }
}
</script>

<style>
.block{
    width: 400px;
    border-radius: 20px;
    background-color: #0faf87;
    color: white;
    text-align: center;
    padding: 100px 0;
    margin: 40px auto;
}
</style>