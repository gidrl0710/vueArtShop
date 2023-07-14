<template>
  <div class="discount">
    <h2 style="color:rgb(212, 212, 9);">{{ amount }}% off when you pay now!!!</h2>
  </div>
</template>

<script>
export default {
  props: {
    amount: Number,
  }
}
</script>

<style scoped>
.discount {
  background: #eee;
  padding: 10px;
  margin: 10px 50px;
  border-radius: 5px;
}
</style>