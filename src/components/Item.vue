<template>
  <div class="columns is-mobile">
    <div class="column is-3">
      <center><img src="../assets/Yui/yui_1.jpg" alt="yui" style="max-height: 120px"></center>
    </div>
    <div class="column is-7">
      <p>Yahari Ore no Seishun Love Comedy wa Machigatteiru</p>
      <p>Yui Yuigahama</p>
    </div>
    <div class="column is-2">
      <p>Amount of item: {{ cartNum }}</p>
      <p>Total price:</p>
      <p>{{ (price * cartNum).toFixed(2) }}$</p>
      <button class="button is-danger mt-3" @click="removeFromCart">Remove</button>
    </div>
  </div>
</template>

<script>
export default {
  data(){

  },
  props: ['cartNum', 'price'],
  methods:{
    removeFromCart(){
      this.$emit('remove')
    }
  }
  }
</script>

<style>

</style>