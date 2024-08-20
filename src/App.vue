<template>
  <div class="black-bg" v-if="모달창열렸니 == true">
    <div class="white-bg">
      <h4>상세페이지</h4>
      <p>{{products[selectedIndex].content}}</p>
      <button @click="모달창열렸니 = false">닫기</button>
    </div>
  </div>

  <div class="menu">
    <a v-for="(a,i) in menu" :key="i">{{a}}</a>
  </div> <!-- navigation -->

  <div v-for="(a, i) in products" :key="i">
    <img :src="products[i].image" class="room-img">
    <h4 @click="openModal(i)" class="clickable">{{products[i].title}}</h4>
    <p>{{products[i].price}}만원</p>
  </div> 



  <!-- <div>
    <h4>{{products[0]}}</h4>
    <p>50만원</p>
    <button @click="increase">허위매물신고</button> <span>신고수 : {{신고수}}</span>
  </div>
    <div>
    <h4>{{products[1]}}</h4>
    <p>60만원</p>
  </div>
    <div>
    <h4>{{products[2]}}</h4>
    <p>70만원</p>
  </div> -->
</template>

<script>

import data from '@/assets/oneroom.js';

export default {
  name: 'App',
  data(){
    return{
      모달창열렸니 : false,
      selectedIndex: null,  // 선택된 항목의 인덱스를 저장
      menu : ['Home', 'Shop', 'About'],
      products : data,
    }
  },
  methods: {
     openModal(i) {
      this.selectedIndex = i; // 선택된 인덱스를 저장
      this.모달창열렸니 = true; // 모달창 열기
    },
    increase(i){
      this.신고수[i] += 1;
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

body {
  margin: 0;
}

div {
  box-sizing: border-box;
}

.black-bg {
  width: 100%;
  height: 100%;
  background: rgba(0, 0, 0, 0.5);
  position: fixed;
  padding: 20px;
}

.white-bg {
  width: 100%;
  background: white;
  border-radius: 8px;
  padding: 20px;
}

.menu {
  background: darkslateblue;
  padding: 15px;
  border-radius: 5px;
}

.menu a {
  color: white;
  padding: 10px;
}

.room-img{
  width: 100%;
  margin-top: 40px;
}

.clickable {
  cursor: pointer;
}
</style>
