<template>
  <div class="mx-10">
    <AddItem class="ml-3 p-5" />
    <ModalFinish class="m-10"/>
  </div>
</template>

<script>
// @ is an alias to /src
import AddItem from '@/components/AddItem'
import ModalFinish from '@/components/ModalFinish'

export default {
  components:{
    AddItem,
    ModalFinish
  }

}
</script>
