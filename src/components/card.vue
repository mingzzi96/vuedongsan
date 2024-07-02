<template>
    <li>
      <img :src="product.image" :alt="product.title + '이미지'" srcset="">
      <h4 @click="$emit('openModal', product.id)">{{product.title}}</h4>
      <p>{{product.price}}원</p>
      <span>{{product.content}}</span>
    </li>
</template>

<script>
export default {
  name: 'DefaultCard',
  props: {
    product: Object,
}
}
</script>

<style>
  img {
    width: 500px;
    height: 500px;
    object-fit: cover;
  }
</style>