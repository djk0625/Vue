<template>
  <div id="app">
    <div class="clicktoast" v-bind:class="{'toast':istoast}">버튼을 클릭했습니다.</div>
    <div class="vue-display">
        <p class="sentence">{{sentence}}</p>
        <button class="btn" type="button" v-on:click="onClick">버튼</button>
    </div>
  </div>

</template>

<script>
export default {
  name: 'App',
  data(){
    return {
      sentence : "어뮤즈트래블은 돌봄여행을 제공하는 컨시어지 여행사입니다.",
      istoast: false,
      cnt : 0,
    }
  },
  methods: {
    onClick : function(){
      this.istoast=true;
      this.cnt++;
      if(this.cnt>=1){
        let arr = this.sentence.split('');
        arr.push(arr.shift());
        this.sentence = arr.join('');
        setTimeout(()=> this.istoast=false,800);
        clearTimeout;
       }
      },
    },  
}
</script>

<style>
html,body{
  width: 100vw;
  height: 100%;
 
}
#app {
  position: relative;
  display:flex;
  justify-content: center;
  align-items: center;
  width: 100%;
  height: 100%;
}
.vue-display{
  text-align: center;
}
.sentence{
  font-size : 2rem;
}
.btn{
  width:200px;
  height: 40px;
}
.clicktoast{
  position: absolute;
  top: 10px;
  right: 100px;
  width: 200px;
  height: 50px;
  background: #191919;
  color:#fefefe ;
  display: flex;
  justify-content: center;
  align-items: center;
  opacity: 0;
  transition: all .8s ease;
}
.toast{
  opacity: 1;
  transform: translate(0,30px);
}
</style>