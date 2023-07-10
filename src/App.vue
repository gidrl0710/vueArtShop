<template>
  <div class="menu">
    <a v-for="(menu, i) in menuList" :key="i">{{ menu }}</a>
  </div>
  <!-- <div v-for="a in houseList" :key="a">
    <h2 :class="subStyle"> {{ a }} 원룸</h2>
    <p> 월세: {{ price }} 만원</p>
  </div> -->
  <div>
    <h2 :class="subStyle"> {{ houseList[0] }} </h2>
    <p> 월세: {{ price }} 만원</p>
  </div> 
  <div>
    <h2 :class="subStyle"> {{ houseList[1] }} </h2>
    <p> 월세: {{ price02 }} 만원</p>
  </div> 
  <div>
    <h2 :class="subStyle"> {{ houseList[2] }} </h2>
    <p> 월세: {{ price03 }} 만원</p>
  </div> 
</template>

<script>

export default {
  name: 'App',
  data() {
    return{
      menuList : ['Home', 'Products', 'About'],
      houseList: ['AA원룸','BB원룸','CC원룸'],
      price: 100,
      price02: 100,
      price03: 150,

      subStyle: 'subStyle'
    }
  },
  components: {
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
}
.subStyle {
  color: rgb(102, 102, 153);
}
.menu {
  background: darkslateblue;
  padding: 15px;
  border-radius:  5px;
}
.menu a {
  color: white;
  padding: 250px
}
</style>
