<template>
    <div class="white-bg">
      <h4>{{products[clickedIndex].title}}</h4>
      <p>{{products[clickedIndex].content}}</p>
      <p>{{products[clickedIndex].price}}원</p>
      <Discount/>
      <input v-model.number="month" />
      <br>
      <p>{{month}}개월 선택함 : {{products[clickedIndex].price * month}}</p>
      <br>
      <br>
      <button @click="$emit('closeModal')">닫기</button>
    </div>
</template>

<script>
export default {
  name: 'DefaultModal',
  data(){
    return {
        month: 0,
    }
  },
  watch: {
    month(currentNumber){
        if (isNaN(currentNumber) === true){
            this.month = 1;
            return alert('문자입력 흐즈므르');
        }
        if(currentNumber > 12){
            this.month = 1;
            return alert('12개월 이하만 거래 가능!')
        }
    }
  },
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