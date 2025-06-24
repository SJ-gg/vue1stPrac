<template>
  <div>
    <img :src="product.image" alt="room image" class="room-img">
    <h4> {{ product.title }} </h4>
    <p>{{ product.price }} 만원</p>
  </div>
</template>

<script>
export default {
  name: 'Card',
  props: {
    product: Object,
  },
}
</script>

<style>

</style>