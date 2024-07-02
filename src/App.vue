<template>
  <div class="menu">
    <a v-for="(menu, i) in menus" :key="menu[i]">{{menu}}</a>
  </div>

  <transition>
    <div class="black-bg" v-if="isOpen">
      <Modal :products="sortedProducts" :clickedIndex="clickedIndex" @closeModal="closeModal" />
    </div>
  </transition>

  <div class="sorting-flex-group">
    <button @click="priceUp">가격 낮은순 정렬</button>
    <button @click="priceDown">가격 높은순 정렬</button>
    <button @click="sortReset">되돌리기</button>
  </div>

  <Discount v-if="showDiscount" :discountNumber="discountNumber"/>

  <ul>
    <Card v-for="(product) in sortedProducts" :key="product.id" :product="product" @openModal="openModal($event)" />
  </ul>
</template>

<script>

import Discount from './components/discount.vue'
import oneRooms from './assets/oneroom.js';
import Modal from './components/modal.vue'
import Card from './components/card.vue'

export default {
  name: 'App',
  data(){
    return {
      showDiscount: true,
      discountNumber: 10,
      clickedIndex:0,
      isOpen: false,
      menus: ['Home', 'Product', 'MyPage'],
      initialProducts : [...oneRooms],
      sortedProducts: oneRooms
    }
  },
  created(){
    // 서버에서 데이터 가져올 때 주로 사용, 컴포넌트 생성되기 전에 가져오도록 함
  },
  mounted(){
    // 컴포넌트 생성되고 해제될 때 사용
    // setTimeout(() => {
    //   this.showDiscount = false
    // }, 5000);
    setInterval(() => {
      this.decreasePercentage()
    }, 1000);
  },
  components: {
    Modal,
    Card,
    Discount
  },
  methods: {
    increase(index){
      this.products[index].count += 1
    },
    openModal(e) {
      this.isOpen = true;
      this.clickedIndex = e;
    },
    closeModal() {
      this.isOpen = false;
      this.clickedIndex = 0;
    },
    priceUp() {
      this.sortedProducts.sort((a,b) => a.price - b.price);
    },
    priceDown() {
      this.sortedProducts.sort((a,b) => b.price - a.price);
    },
    sortReset() {
      this.sortedProducts = [...this.initialProducts];
    },
    decreasePercentage() {
      if(this.discountNumber === 0){
        return false
      }
      this.discountNumber--;
    }
  },
}
</script>

<style>
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}
.menu {
  background : darkslateblue;
  padding : 15px;
  border-radius : 5px;
}
.menu a {
  color : white;
  padding : 10px;
}
body {
  margin : 0;
}
div {
  box-sizing: border-box;
}
.black-bg {
  width: 100vw; height:100vh;
  background: rgba(0,0,0,0.5);
  position: fixed; 
  padding: 20px;
}

.v-enter-active,
.v-leave-active {
  transition: opacity 0.5s ease;
}

.v-enter-from,
.v-leave-to {
  opacity: 0;
}

.sorting-flex-group {
  width: 100%;
  display: flex;
  align-content: center;
  justify-content: center;
  gap: 12px;
}
</style>
