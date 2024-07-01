<template>
  <div class="menu">
    <a v-for="(menu, i) in menus" :key="menu[i]">{{menu}}</a>
  </div>

  <div class="black-bg" v-if="isOpen === true">
    <div class="white-bg">
      <h4>상세페이지</h4>
      <p>상세페이지내용임</p>
      <button @click="isOpen = false">닫기</button>
    </div>
  </div>

  <img alt="Vue logo" src="./assets/logo.png">
  <ul>
    <li v-for="(product, i) in products" :key="product.id" :id="product.title+product.id">
      <img :src="product.image" :alt="product.title + '이미지'" srcset="">
      <h4 @click="isOpen = true">{{product.title}}</h4>
      <p>{{product.price}}원</p>
      <span>{{product.content}}</span>
      <div>
        <button @click="increase(i)">허위매물 신고</button>
        <span>신고수: {{product.count}}</span>
      </div>
    </li>
  </ul>
</template>

<script>

import onerooms from './assets/oneroom.js';

export default {
  name: 'App',
  data(){
    return {
      isOpen: false,
      menus: ['Home', 'Product', 'MyPage'],
      products : onerooms
    }
  },
  components: {
  },
  methods: {
    increase(index){
      this.products[index].count += 1
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
.white-bg {
  width: 100%; background: white;
  border-radius: 8px;
  padding: 20px;
} 
</style>
