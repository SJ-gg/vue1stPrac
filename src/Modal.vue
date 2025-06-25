<template>
  <div class="black-bg" v-if="모달창열렸니">
    <div class="white-bg">
      <h4>{{ products[productsClick].title }}</h4>
      <img :src="products[productsClick].image" alt="room image" class="room-img" style="width: 100%">
      <p>{{ products[productsClick].content }}</p>
      <p>{{ products[productsClick].price }} 원</p>
      <button @click="closeModal()">닫기</button>
    </div>
  </div>
</template>

<script>
export default {
  name: 'Modal',
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