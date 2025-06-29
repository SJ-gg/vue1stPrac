<template>

  <transition name="fade">
  <Modal @closeModal="모달창열렸니 = false" :products="products" :productsClick="productsClick" :모달창열렸니="모달창열렸니"/>
  </transition>

  <div class="menu">
    <a v-for="a in 메뉴들" :key="a"> {{ a }} </a>
  </div>

  <Discount/>

  <button @click="priceSort">가격순정렬</button>
  <button @click="sortBack">되돌리기</button>

    <Card @openModal="모달창열렸니 = true; productsClick = $event" :product="products" v-for="(products, i) in products" :key="i" />

</template>

<script>
import data from './assets/oneroom.js'
import Discount from './Discount.vue'
import Modal from './Modal.vue'
import Card from './Card.vue'

export default {
  name : 'App',
  data() { // 모든 변수 데이터
    return {
      productsOriginal: [...data], // 원본 데이터 보존
      productsClick: 0,
      products : data,
      모달창열렸니 : false,
      메뉴들 : ['Home', 'Shop', 'About'],
    }
  },
  methods: {
    increase(x) {
      this.x += 1;
    },
    priceSort() {
      this.products.sort(function(a,b) {
        return a.price - b.price;
      });
    },
    sortBack() {
      this.products = [...this.productsOriginal];
    }
  },
  components: {
    Discount: Discount, // 'Discount,'과 같음.
    Modal,
    Card,
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

.fade-enter-from {
  opacity: 0;
}
.fade-enter-active {
  transition: all 1s;
}
.fade-enter-to {
  opacity: 1;
}

.fade-leave-from {
  opacity: 1;
}
.fade-leave-active {
  transition: all 1s;
}
.fade-leave-to {
  opacity: 0;
}
/* .modalStart {
  opacity: 0;
  transition: all 1s;
}
.modalEnd {
  opacity: 1;
} */
.discount {
  background: #eee;
  padding: 10px;
  margin: 10px;
  border-radius: 5px;
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