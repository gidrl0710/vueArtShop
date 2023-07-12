<template>
  <div class="black-bg modal" v-if="modalShow">
    <div class="white-bg">
      <h2 :class="subStyle">{{ houseList[slctNum].title }}</h2>
      <img :src="houseList[slctNum].image" class="roomSImg">
      <p>Artist : {{ houseList[slctNum].artist }}</p>
      <p>Details : {{ houseList[slctNum].content }}</p>
      <p>Price : {{ houseList[slctNum].price }}</p>
      <Discount/>
      <button class="btn" @click="$emit('closeModal')">Close</button>
    </div>
  </div>
</template>

<script>
import Discount from './TheDiscount.vue';

export default {
  name: 'TheModal',
  props: {
    houseList: Array,
    slctNum: Number, 
    modalShow: Boolean,

    subStyle: String,
  },
  components: {
    Discount,
  },
}
</script>

<style>
</style>