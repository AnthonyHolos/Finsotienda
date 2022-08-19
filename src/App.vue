<template>
  <div id="app">
    <headshop></headshop>
    <LeftBar></LeftBar>
    <!--<RightBar></RightBar>-->
    <products></products>
  </div>
</template>

<script>
import headshop from './components/Header.vue'
import LeftBar from './components/LeftBar.vue'
import RightBar from './components/RightBar.vue'
import products from './components/Products.vue'

export default {
  name: 'App',
  components: {
    headshop,
    LeftBar,
    RightBar,
    products
}
}
</script>

<style>
#app {
  /*font-family: Avenir, Helvetica, Arial, sans-serif;*/
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  /*text-align: center;
  color: #2c3e50;
  margin-top: 60px;*/
}
</style>
