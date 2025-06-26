<template>
  <div class="black-bg" v-if="모달창열렸니">
    <div class="white-bg">
      <h4>{{ products[productsClick].title }}</h4>
      <img :src="products[productsClick].image" alt="room image" class="room-img" style="width: 100%">
      <p>{{ products[productsClick].content }}</p>
      <input v-model.number="month">
      <p> {{ month }}개월 선택함 : {{ products[productsClick].price * month}} 원</p>
      <button @click="closeModal()">닫기</button>
    </div>
  </div>
</template>

<script>
export default {
  name: 'Modal',
  data() {
    return {
      month: 1,
    }
  },
  watch: {
    month(monthNum) {
      if (monthNum === '') return;
      if (
        typeof monthNum !== 'number' ||
        isNaN(this.month) ||
        monthNum < 0 ||
        monthNum > 12
      ) {
        alert('1~12 사이의 숫자만 입력할 수 있습니다.');
        this.month = 1;
      }
    }
  },
  props: {
    products: Array,
    productsClick: Number,
    모달창열렸니: Boolean,
  },
  methods: {
    closeModal() {
      this.$emit('closeModal');
    },
  },
}
</script>

<style>

</style>