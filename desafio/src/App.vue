<template>
  <Header/>
  <router-view/>
  <Footer/>
</template>

<script>

import Header from './components/Header.vue';
import Footer from './components/Footer.vue';

export default {
  components:{
    Header,
    Footer
  } 
}
</script>

<style>

*{
  font-family: 'Roboto', sans-serif;
  padding: 0;
  margin: 0;
  box-sizing: border-box;
  transition: .5s;
}

template{
  position: absolute;
  width: 100%;
  min-height: 100%;
  box-sizing: border-box;
}

</style>
