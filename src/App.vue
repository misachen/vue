<template>
  <div id="app">
    <navbar></navbar>
    <div class="text-center">     
      <img src="./assets/logo.png">
    </div>
    
    <div class="container">
      <router-view></router-view>
    </div>
    
  </div>
</template>

<script>
  import Navbar from './components/Navbar';
  export default {
    name: 'app',
    components:{
      Navbar
    },  
  }
</script>

<style lang="scss">
@import "~bootstrap/scss/bootstrap";
.router-link-active{
  color:$brand-primary !important;
}
</style>
