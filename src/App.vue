<template>
  <div class="menu">
    <a v-for="(menu, i) in menus" :key="menu[i]">{{menu}}</a>
  </div>

  <div class="black-bg" :class="{end: isOpen}">
    <Modal :products="products" :clickedIndex="clickedIndex" @closeModal="closeModal" />
  </div>


  <img alt="Vue logo" src="./assets/logo.png">

  <ul>
    <Card v-for="(product) in products" :key="product.id" :product="product" @openModal="openModal($event)" />
  </ul>
</template>

<script>

import oneRooms from './assets/oneroom.js';
import Modal from './components/modal.vue'
import Card from './components/card.vue'

export default {
  name: 'App',
  data(){
    return {
      clickedIndex:0,
      isOpen: false,
      menus: ['Home', 'Product', 'MyPage'],
      products : oneRooms
    }
  },
  components: {
    Modal,
    Card
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
    }
  }
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
  opacity: 0;
  pointer-events: none;
  transition: 0.2s;
}
.end {
  pointer-events: all;
  opacity: 1;
}
</style>
