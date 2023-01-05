<template>
  <h3>You reaction time: {{score}}ms</h3>
  <p class="rank">{{rank}}</p>
</template>

<script>
export default {
 props:['score'],
 data(){
     return{
         rank: null
     }
 },
 mounted(){
     if (this.score<250){
         this.rank = 'Fast fingers'
     } else if( this.score < 400){
         this.rank = 'Average reflex'
     } else{
         this.rank = 'Snail pace'
     }
 }
}
</script>

<style>
.rank{
    font-family: 'Courier New', Courier, monospace;
    color: lightgreen;
}
</style>