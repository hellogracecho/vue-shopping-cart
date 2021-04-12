<template>
  <div class="menu">
    <a v-for="(nav, index) in menu" :key="index"> {{ nav }}</a>
  </div>
  <button @click="isModalOpen = true">Open Modal</button>
  <div class="modal-container" v-if="isModalOpen">
    <div class="modal">
      <h2>Modal Popup</h2>
      <pre>hello Vue.js</pre>
      <button @click="isModalOpen = false">Close</button>
    </div>
  </div>
  <div class="item-container">
    <div class="item" v-for="(product, index) in products" :key="index">
      <img :src="product.imgUrl" :alt="product.title" />
      <h4>{{ product.title }}</h4>
      <p>{{ product.price }}</p>
      <button @click="addItem(index)">Add</button>
      <button @click="deleteItem(index)">Delete</button>
      <span>{{ product.count }}</span>
    </div>
  </div>
</template>

<script>
export default {
  title: "Shop My Fruit",
  data() {
    return {
      menu: ["Home", "Shop", "About"],
      isModalOpen: false,
      products: [
        {
          title: "Apple",
          price: 4.99,
          imgUrl: "https://via.placeholder.com/150/ff0000/",
          count: 0,
        },
        {
          title: "Banana",
          price: 3.99,
          imgUrl: "https://via.placeholder.com/150/e2e62c/",
          count: 0,
        },
        {
          title: "Carrot",
          price: 1.59,
          imgUrl: "https://via.placeholder.com/150/ff9900/",
          count: 0,
        },
      ],
    };
  },
  methods: {
    addItem(index) {
      this.products[index].count++;
    },
    deleteItem(index) {
      const itemCount = this.products[index].count;
      if (itemCount > 0) {
        this.products[index].count -= 1;
      }
    },
  },
  components: {},
};
</script>

<style>
*,
*:befor,
*:after {
  box-sizing: border-box;
}
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
}

.menu {
  display: flex;
  justify-content: center;
  background-color: rgb(39, 35, 63);
}
.menu a {
  padding: 20px;
  color: wheat;
  cursor: pointer;
}

.item-container {
  display: flex;
  justify-content: center;
  flex-wrap: wrap;
}
.item {
  padding: 20px;
}

.modal-container {
  width: 100%;
  height: 100%;
  background: rgbc(0, 0, 0, 0.5);
  position: fixed;
  padding: 20px;
}

h4,
p {
  margin: 0;
}
span {
  margin-left: 10px;
}
</style>
