<template>
  <div>
    <form>
      <input
        type="text"
        v-model="currentItem"
        placeholder="Item"
        style="color: black"
        class="pl-5 p-2 mx-2 mt-3 rounded-full h-10 w-64"
      />
      <input
        type="number"
        min="1"
        placeholder="0"
        v-model="currentValue"
        style="color: black"
        class="pl-5 p-2 mx-3 mt-3 rounded-full h-10 w-16"
      />
      <button
        @click="addItem"
        class="rounded-full bg-green-800 h-10 w-10 hover:bg-green-600 duration-300"
      >
        &plus;
      </button>
    </form>
    <div class="table w-full mt-5">
      <div class="table-header-group">
        <div class="table-row grid grid-cols-12">
          <div class="table-cell text-end text-3xl mb-2 col-span-1">#</div>
          <div class="table-cell text-start text-3xl mb-2 ml-10 col-span-8">
            Produto
          </div>
          <div class="table-cell text-start text-3xl mb-2 col-span-3">
            Quantia
          </div>
        </div>
      </div>
      <div class="table-row-group">
        <div
          v-for="(item, index) in items"
          :key="`${item} - ${index}`"
          class="table-row grid grid-cols-12"
        >
          <div class="table-cell text-end col-span-1 text-xl" v-if="item.name">
            {{ index }}
          </div>
          <div
            class="table-cell text-start ml-10 my-3 col-span-8 text-xl"
            v-if="item.name"
          >
            <span style="text-transform: uppercase">{{ item.name }}</span>
          </div>
          <div
            class="table-cell grid col-span-3 justify-items-start self-star text-xl"
            v-if="item.value"
          >
            <div style="display: flex">
              <input
                type="number"
                min="1"
                v-model="item.value"
                style="color: black"
                class="pl-5 p-2 mx-2 rounded-full h-10 w-20"
              />
              <button
                class="ml-3 rounded-full bg-red-600 hover:bg-red-400 h-10 w-10 duration-300"
                @click="remove(item)"
              >
                &#10006;
              </button>
            </div>
          </div>
        </div>
      </div>
    </div>
  </div>
</template>

<script>
export default {
  data() {
    return {
      items: [{ name: "", value: "" }],
      currentItem: "",
      currentValue: "",
    };
  },

  methods: {
    remove(item) {
      this.items = this.items.filter((t) => t.name !== item.name);
    },

    addItem(e) {
      e.preventDefault();

      if (this.currentValue == 0) {
        this.currentValue = 1;
      }

      if (this.currentItem === "") {
        alert("Nenhum produto adicionado");
        return false;
      }

      this.items.push({
        name: this.currentItem,
        value: this.currentValue,
      });

      this.currentItem = "";
      this.currentValue = "";
    },
  },
};
</script>

<style lang="postcss" scoped>
.table-cell {
  @apply my-2;
}
</style>