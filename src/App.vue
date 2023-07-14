<template>

  <transition name="fade">
    <Modal @closeModal="modalShow=false" :houseList="houseList01" :slctNum="slctNum" :modalShow="modalShow" :subStyle="subStyle"/>
  </transition>
  <transition name="fade">
    <Modal @closeModal="modalShow02=false" :houseList="houseList02" :slctNum="slctNum02" :modalShow="modalShow02" :subStyle="subStyle"/>
  </transition>

  <div class="menu">
    <p class="mainTitle">Welcome! Yeeun Art Shop</p>
    <a v-for="(menu, i) in menuList" :key="i">{{ menu }}</a>
  </div>

  <Discount v-if="showDiscount ==  true" :amount="amount"/>

  <div class="sortBtn">
    <button class="sort btn3" @click="priceSort">가격 순 정렬</button>
    <button class="sort btn3" @click="sortBack">기본정렬</button>
  </div>

  <Card @openModal="modalShow=true; slctNum=$event" :houseList="houseList01" :subStyle="subStyle"/>
  <Card @openModal="modalShow02=true; slctNum02=$event" :houseList="houseList02" :subStyle="subStyle"/>
  
</template>

<script>
// import {houseList} from './assets/roomData.js'
import { houseList01, houseList02 } from './assets/roomData.js'
import Discount from './components/TheDiscount.vue';
import Modal from './components/TheModal.vue';
import Card from './components/TheCard.vue';

export default {
  name: 'App',
  data() {
    return{
      menuList : ['Home', 'Products', 'About'],
      houseOne: [...houseList01], // 복원 데이터
      houseTwo: [...houseList02],
      houseList01: houseList01,
      houseList02: houseList02,
      slctNum: 0,
      slctNum02: 0,

      modalShow: false, // modal창 상태
      modalShow02: false,

      showDiscount: true, // Discount show여부
      amount: 30, // 할인률

      subStyle: 'subStyle'
    }
  },
  methods: {
    increase() {
      this.numCrim[0] = this.numCrim[0]+1;
    },
    priceSort() {
      this.houseList01.sort(function(a, b){
        return a.price02 - b.price02
      });
      this.houseList02.sort(function(a, b){
        return a.price02 - b.price02
      });
    },
    sortBack() {
      this.houseList01 = [...this.houseOne];
      this.houseList02 = [...this.houseTwo];
    }
  },
  mounted() {
    // setTimeout(() =>{
    //   this.showDiscount = false;
    // },10000)
    setInterval(()=>{
      if(this.amount > 0){
        this.amount--;
      }else{
        return;
      }
    }, 1000)
  },
  components: {
    Discount,
    Modal,
    Card,
  },
}
</script>

<style>
body {
  margin: 0;
}
div {
  box-sizing: border-box;
}
.flex-container {
  display: flex;
}
.flex-container.flex-start {
  justify-content: flex-start;
}
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
}
.contents {
  margin: auto;
  padding: 0 60px;
  width: 100%;  
}
.black-bg {
  width:100%; height: 100%;
  background: rgba(0,0,0,0.5);
  position: fixed; padding: 20px;
}
.white-bg {
  width: 50%; height: 60%;
  background: white;
  border-radius: 8px;
  padding: 20px;
  position: fixed;
  top: 50%; left: 50%;
  transform: translate(-50%, -50%);
}

.subStyle {
  color: rgb(12, 12, 153);
}
.menu {
  background: darkslateblue;
  padding: 10px 15px;
  border-radius:  5px;
}
.menu a {
  color: white;
  padding: 250px
}
.btn {
  background: rgb(145, 140, 140);
  margin-top: 30px;
  padding: 0.5rem 0.5rem;
  font-weight: 700;
  border-radius: .25rem;
  border: 0 solid #ebedef;
  color: white;
}
.btn2 {
  background: rgb(136, 165, 229);
  margin-top: 5px;
  padding: 0.5rem 0.5rem;
  font-weight: 700;
  border-radius: .25rem;
  border: 0 solid #ebedef;
  color: white;
}
.btn3 {
  background: rgb(119, 114, 114);
  margin: 5px 5px;
  padding: 0.5rem 0.5rem;
  font-weight: 700;
  border-radius: .25rem;
  border: 0 solid #ebedef;
  color: white;
}
.roomImg {
  margin-top: 80px;
  margin-right: 50px;
  width: 500px;
  height: 250px;
  border-radius: .25rem;
}
.roomSImg {
  margin-top: 0;
  margin-right: 50px;
  width: 500px;
  height: 250px;
  border-radius: .25rem;
}
.mainTitle {
  color: white;
  font-weight: 800;
  font-size: 35px;
}
div.sortBtn {
  margin-left: 88%;
}

.fade-enter-from {
  opacity: 0;
}
.fade-enter-active {
  transition: all 1s;
}
.fade-enter-to {
  opacity: 1;
}
.fade-leave-from {
  opacity: 1;
}
.fade-leave-active {
  transition: all 1s;
}
.fade-leave-to {
  opacity: 0;
}
</style>
