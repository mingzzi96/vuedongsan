<template>
  <div class="menu">
    <a>Home</a>
  </div>

  <img alt="Vue logo" src="./assets/logo.png">
  <ul>
    <li v-for="(product, i) in products" :key="product.name+i" :id="product.name+i">
      <h4>{{product.name}}</h4>
      <p>{{product.price}}만원</p>
      <div>
        <button @click="increase(i)">허위매물 신고</button>
        <span>신고수: {{product.count}}</span>
      </div>
    </li>
  </ul>
</template>

<script>

export default {
  name: 'App',
  data(){
    return {
      products : [{name:'역삼동원룸', price: 46, count: 0}, {name:'천호동원룸', price:50, count: 0}, {name:'마포구원룸', price: 60, count: 0}],
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
</style>
