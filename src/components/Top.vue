<template>
  <button class="btn shadow" @click='top'>
      <b-icon icon="arrow-bar-up"></b-icon>
  </button>
</template>

<script>
export default {
    name:'Top',
    methods:{
      top(){
        window.scrollTo(0,0);
      }
    }
}
</script>

<style>
button{
  position: fixed;
  z-index: 99;
  right: 15px;
  bottom: 10px;
  font-weight: 600;
  font-size: 20px;
}
</style>