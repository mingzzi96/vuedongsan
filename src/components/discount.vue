<template>
    <div class="discount">
        <h4>지금 결제하면 {{discountNumber}}% 할인</h4>
    </div>
</template>

<script>
export default {
  name: 'PriceDiscount',
  props: {
    discountNumber: Number,
  }
}
</script>

<style>
  .discount {
    display: flex;
    align-content: center;
    justify-content: center;
    padding: 20px;
    width: 80%;
    background-color: #e6e6e6;
    border-radius: 20px;
  }
</style>