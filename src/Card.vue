<template>
  <div>
    <img :src="product.image" alt="room image" class="room-img">
    <h4 @click="openModal()"> {{ product.title }} </h4>
    <p>월 {{ product.price }} 만원</p>
  </div>
</template>

<script>
export default {
  name: 'Card',
  props: {
    product: Object,
  },
  methods: {
    openModal() {
      this.$emit('openModal', this.product.id);
    }
  }
}
</script>

<style>

</style>