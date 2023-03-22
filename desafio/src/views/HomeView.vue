<template>
  <div class="home container">
      <Form/>
  </div>
</template>

<script>

import Form from '@/components/Form.vue';

export default {
  name: 'HomeView',
  components:{
    Form,
  }
}
</script>

<style>

.container{
  min-height: 64.5%;
}

</style>