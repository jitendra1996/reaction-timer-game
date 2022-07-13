<template>
    <div class="block" v-if="showBlock" @click="hideBlock">
        click me
    </div>
</template>

<script>
export default{
    props:['delay'],
    data(){
        return {
            showBlock : false,
            timer:null,
            reaction : 0
        }
    },
    methods:{
        hideBlock(){
            this.showBlock=false;
            this.endTimer();
        },
        startTimer(){
            this.timer=setInterval(()=>{
                this.reaction+=10
                },10)
        },
        endTimer(){
            clearInterval(this.timer);
            this.$emit('enable',this.reaction); 
        }
    },
    mounted(){
        setTimeout(()=>{
            this.showBlock = true;
            this.startTimer();
        },this.delay)
    }
}
</script>

<style scoped>
.block{
    position: absolute;
    top:50%;
    left: 50%;
    transform: translate(-50%,-50%);
    background: #50C878;
    color: #fff;
    padding: 100px;
    border-radius: 20px;
    cursor: pointer;
}
</style>