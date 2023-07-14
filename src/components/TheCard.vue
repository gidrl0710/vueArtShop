<template>
  <div class="contents flex-container flex-start" >
    <div v-for="(home, i) in houseList" :key="i">
      <img :src="home.image" class="roomImg">
      <h2 @mouseover="overEvent" :class="subStyle" > {{ home.title }} </h2>
      <button @mouseover="overEvent" class="btn2" :style="overData" @click="sendMd(i)">more detail</button>
    </div> 
  </div>
</template>

<script>
export default {
  name: 'TheCard',
  props: {
    houseList: Array,
    slctNum: Number, 

    subStyle: String,
  },
  data() {
    return {
      overData: ''
    }
  },
  methods: {
    sendMd(i) {
      this.$emit('openModal', i);
    },
    overEvent() {
      this.overData = "cursor:pointer;"
    }
  }
  
}
</script>

<style>

</style>