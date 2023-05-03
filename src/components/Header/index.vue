<template>
  <div class="sticky top-0 w-full text-xl text-end p-5" style="background-color: #852b08;">
    <div class="container">
      <router-link
      class="p-4"
      @mouseover="hover1 = true"
      @mouseleave="hover1 = false"
      :class="{ active1: hover1 }"
      to="/">Cadastro</router-link> 
      <router-link
      class="p-4"
      @mouseover="hover2 = true"
      @mouseleave="hover2 = false"
      :class="{ active2: hover2 }"
      to="/about">Listas</router-link>
    </div> 
  </div>
</template>

<script>
export default {
  name: 'Header',
  data(){
    return{
      hover1: false,
      hover2: false
    }
  }

};
</script>

<style lang="postcss" scoped>

.active1, .active2{
  @apply bg-red-300 text-gray-800 rounded-full p-4
}

</style>