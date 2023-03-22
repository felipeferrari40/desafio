<template>
  <div class="container">
    <List/>
  </div>
</template>

<script>

import List from '@/components/List.vue'

export default {
  name: 'AboutView',
  components:{
    List
  }
}
</script>

<style scoped>
.container{
  min-height: 64.5%;
}

</style>