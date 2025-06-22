<template>

  <div class="black-bg" v-if="모달창열렸니">
    <div class="white-bg">
      <h4>상세페이지</h4>
      <p>상세페이지 내용</p>
      <button @click="모달창열렸니 = false">닫기</button>
    </div>
  </div>

  <div class="menu">
    <a v-for="a in 메뉴들" :key="a"> {{ a }} </a>
  </div>
  <div v-for="(products, i) in products" :key="i">
    <img :src="products.image" alt="room image" class="room-img">
    <h4 @click="모달창열렸니 = true">{{ products.title }} 원룸</h4>
    <p>{{ products.price }} 만원</p>
    <button @click="increase(i)">허위매물신고</button>
    <span> 신고수 : {{ 신고수[i] }}</span>
  </div>
</template>

<script>
import data from './assets/oneroom.js'

export default {
  name : 'App',
  data() { // 모든 변수 데이터
    return {
      products : data,
      모달창열렸니 : false,
      신고수 : [0, 0, 0],
      메뉴들 : ['Home', 'Shop', 'About'],
    }
  },
  methods: {
    increase(x) {
      this.신고수[x] += 1;
    }
  },
  components : {
  }
}
</script>

<style>
body {
  margin: 0
}
div {
  box-sizing: border-box;
}
.black-bg {
  width: 100%; height: 100%;
  background: rgba(0, 0, 0, 0.5);
  position: fixed; padding: 20px;
}
.white-bg {
  width: 100%; background: white;
  border-radius: 8px;
  padding: 20px;
}
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
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
.room-img {
  width: 100%;
  margin-top: 40px;
}
</style>