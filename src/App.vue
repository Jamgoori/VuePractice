<template>

  <div class="black-bg" v-if="modal == 1">
    <div class="white-bg">
      <h4>{{onerooms[select].title}}</h4>
      <p>{{onerooms[select].content}}</p>
      <button @click="modal = 0">닫기</button>
    </div>
  </div>
  <div class="menu">
    <a v-for="a in menus" :key="a">{{a}}</a>
  </div>
  <div>
  <div v-for="(a,i) in onerooms" :key="a">
    <img :src="onerooms[i].image" class="roomImg"/>
    <div @click="modal = 1;  select = onerooms[i].id"> {{onerooms[i].title}}</div>
    <div>{{onerooms[i].price}} 만원</div>
    <button @click="report[i]++">신고</button>
    <span>신고 수 : {{report[i]}}</span>
  </div>
</div>
</template>

<script>

import oneroomData from './assets/oneroom'
export default {
  name: 'App',
  data(){
    return{
      select : 0,
      onerooms : oneroomData,
      modal : 0,
      report : ['0','0','0','0','0','0'],
      price : ['60','70','90'],
      products : ['역삼동원룸','천호동 원룸', '무거동 원룸']
      ,menus : ['Home','Shop','About']
    }
  },
  methods: {
    increase(a,i){
      this.report[i]++;
    }
  },
  components: {
    
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
}
.menu {
  background: darkblue;
  padding: 15px;
  border-radius: 5px;
}
.menu a{
  color: white;
  padding: 10px;
}
.roomImg{
  width: 20%;
  margin-top: 40px;
}
.black-bg{
  width: 100%;
  height: 100%;
  background-color: rgba(0,0,0,0.5);
  position: fixed;
  padding: 20px;
}
.white-bg{
  width: 100%;
  background-color: white;
  border-radius: 8px;
  padding: 20px;
}
</style>
