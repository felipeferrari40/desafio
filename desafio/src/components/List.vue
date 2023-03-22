<template>
  <div class="mt-3">
    <div class="row">
      <button class="card col mx-2 py-5 align-items-center text-center">
        Lista 1
      </button>
      <button class="card col mx-2 py-5 align-items-center text-center">
        Lista 2
      </button>
      <button class="card col mx-2 py-5 align-items-center text-center">
        Lista 3
      </button>
    </div>
  </div>
</template>

<script>
export default {
  name: "List",
  methods: {
    /*async getListas() {
      const req = await fetch("http://localhost:3000/listas");

      const data = await req.json();

      this.listas = data;

      console.log(data);
    },*/
  },

  mounted() {
    this.getListas();
  },
};
</script>

<style scoped>
</style>