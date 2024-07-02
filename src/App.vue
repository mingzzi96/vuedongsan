<template>
  <div class="menu">
    <a v-for="(menu, i) in menus" :key="menu[i]">{{menu}}</a>
  </div>

  <div class="black-bg" v-if="isOpen === true">
    <Modal :products="products" :clickedIndex="clickedIndex" @closeModal="closeModal" />
  </div>


  <img alt="Vue logo" src="./assets/logo.png">

  <ul>
    <Card v-for="(product, i) in products" :key="product.id" :product="product" @openModal="openModal(i)" />
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
    openModal(index) {
      this.isOpen = true;
      this.clickedIndex = index;
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
width: 100%; height:100%;
background: rgba(0,0,0,0.5);
position: fixed; padding: 20px;
}
</style>
