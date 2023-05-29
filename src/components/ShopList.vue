<template>
  <div class="container">
    <h1 class="mb-5 mt-5">{{ msg }}</h1>
    <div class="col-lg-6">
      <div class="input-group">
        <input
          type="text"
          placeholder="Product name"
          v-model="item"
          class="form-control"
        />
        <button @click="addItem" class="btn btn-primary">Add item</button>
      </div>
      <p v-if="items.length === 0" class="mt-3">
        Your basket is empty! Please add some items in your basket
      </p>
      <ul class="list">
        <li
          class="list-item card p-3 mb-3"
          v-for="(item, index) in items"
          :key="index"
          @click="deleteItem(index)"
        >
          {{ item }}
        </li>
      </ul>
    </div>
  </div>
</template>

<script>
export default {
  name: "ShopList",
  data() {
    return {
      msg: "Shop",
      item: "",
      items: ["Milk", "Meat", "Eggs"],
    };
  },
  methods: {
    addItem() {
      if (this.item.length >= 3) {
        this.items.push(this.item);
        this.item = "";
      }
    },
    deleteItem(index) {
      this.items.splice(index, 1);
    },
  },
};
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped lang="scss">
.list {
  padding: 20px 0;
  &-item {
    cursor: pointer;
    &:hover {
      background: #0d6efd;
      color: #fff;
      transition: all 0.3s ease-in-out;
    }
  }
}
</style>
