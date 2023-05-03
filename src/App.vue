<template>
  <div class="flex flex-col h-screen justify-between">
    <Header/>
    <router-view class="mb-auto" />
    <Footer/>
  </div>
</template>

<script>
import Header from './components/Header'
import Footer from './components/Footer'

export default {
  components:{
    Header,
    Footer
  }
}

</script>

<style>
*{
  text-decoration: none;
  color: white;
  font-family:'Trebuchet MS', 'Lucida Sans Unicode', 'Lucida Grande', 'Lucida Sans', Arial, sans-serif
}

body {
  background-color: rgb(25, 25, 120)
}
</style>
