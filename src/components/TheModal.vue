<template>
  <div class="black-bg modal" v-if="modalShow">
    <div class="white-bg">
      <h2 :class="subStyle">{{ houseList[slctNum].title }}</h2>
      <img :src="houseList[slctNum].image" class="roomSImg">
      <p><a>Artist</a> : {{ houseList[slctNum].artist }}</p>
      <p><a>Details</a> : {{ houseList[slctNum].content }}</p>
      <p><a>Price</a> : {{ houseList[slctNum].price }}</p>
      <p><a>Installment</a> : <input v-model="month" @input="monthCal(houseList[slctNum].price02)"> month</p> 
      <p><a>Monthly payment</a> : ￦{{ monthPay }}</p>
      <p v-show="logShow" style="color:red">{{ logMessage }}</p>
      <button class="btn" @click="$emit('closeModal')">Close</button>
    </div>
  </div>
</template>

<script>
export default {
  name: 'TheModal',
  props: {
    houseList: Array,
    slctNum: Number, 
    modalShow: Boolean,

    subStyle: String,
  },
  data() {
    return {
      month: 0,
      monthPay: 0,
      logMessage: '',
      logShow: false,
    }
  },
  methods: {
    monthCal(pay) {
      if(this.month > 1){
        this.monthPay = (pay/this.month).toString().replace(/\B(?<!\.\d*)(?=(\d{3})+(?!\d))/g, ',');
      }else{
        this.monthPay = 0;
      }
    }
  },
  watch: {
    month() {
      return this.month = this.month.replace(/[^0-9]/g, '');
    }
  },
}
</script>

<style scoped>
input {
  width:20px;
}
p > a{
  color: rgb(12, 12, 153);
  font-weight: 550;
}
</style>