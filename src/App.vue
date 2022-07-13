<template>
<h1>Ninja Reaction Time</h1>
<button :class="[isPlaying ? 'disabledBtn' : 'btn' ]" @click="showBlock" :disabled="isPlaying">Play</button>
<div v-if="isPlaying">
  <Block :delay="delay" @enable="enableBtn"/>
</div>
<Result v-if="showResult" :score="reactionTime"/>
</template>

<script>
import Block from './components/Block.vue';
import Result from './components/Result.vue';

export default {
  name: 'App',
  components: { Block, Result },
  data(){
    return {
      isPlaying : false,
      delay : null,
      reactionTime:null,
      showResult:false
    }
  },
  methods:{
    showBlock(){
      this.isPlaying = true;
      this.delay = 2000 + Math.random()*6000;
      this.showResult = false;
    },
    enableBtn(result){
      this.reactionTime = result;
      this.isPlaying = false;
      this.showResult = true;
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
.btn{
  padding: 10px 30px;
  background: #2c3e50;
  color: #fff;
  font-size: 1.3rem;
  font-family: sans-serif;
  border: none;
  border-radius: 1rem;
  cursor: pointer;
}
.disabledBtn{
  background: #999999;
  padding: 10px 30px;
  color: #fff;
  font-size: 1.3rem;
  font-family: sans-serif;
  border: none;
  border-radius: 1rem;
  cursor: pointer;
}
</style>
