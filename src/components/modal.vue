<template>
    <div class="white-bg">
      <h4>{{products[clickedIndex].title}}</h4>
      <p>{{products[clickedIndex].content}}</p>
      <p>{{products[clickedIndex].price}}원</p>
      <Discount/>
      <button @click="$emit('closeModal')">닫기</button>
    </div>
</template>

<script>
export default {
  name: 'DefaultModal',
  props: {
    products: Array,
    clickedIndex: Number,
  }
}
</script>

<style>
    .white-bg {
    width: 100%; background: white;
    border-radius: 8px;
    padding: 20px;
    } 
</style>