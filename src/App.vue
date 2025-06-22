<template>
  <img alt="Vue logo" src="./assets/logo.png">
  <div>
    <h4>{{ products[0] }} 원룸</h4>
    <p>50 만원</p>  <!-- vue 문법  {{ 변수 }} (-> 자주 변경되거나 중요해보이는 데이터는 데이터 바인딩을 사용한다) -->
  </div>
  <div>
    <h4>{{ products[1] }} 원룸</h4> <!-- :style="blue" (-> HTML 속성을 지정할땐 속성앞 ':' 추가) -->
    <p>70 만원</p>
  </div>
  <div>
    <h4>{{ products[2] }} 원룸</h4> 
    <p> 만원</p>
  </div>
</template>

<script>
export default {
  name : 'App',
  data() { // 모든 면수 데이터
    return {
      products : ['역삼동원룸', '천호동원룸', '마포구원룸']
    }
  },
  components : {
  }
}
</script>

<style>
</style>