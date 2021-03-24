<template>
  <div class="home">
    <h1>{{ message }}</h1>
    <!-- <p><button v-on:click="createProduct">Create Product</button></p> -->
    <div v-for="product in products" v-bind:key="product.id">
    <!-- <div v-for="product in products"> -->
    {{ product.name }}
    <hr>
    </div>
  </div>
</template>

<style></style>
<script>
import axios from "axios";

export default {
  data: function () {
    return {
      message: "Welcome to Vue.js!",
      products: [],
      name: "",
      description: "",
    };
  },
  created: function () {
    console.log("in created");
    this.indexProducts();
  },
  methods: {
    indexProducts: function () {
      console.log("in products index");
      // get data from api, then show that data to the user
      axios.get("http://localhost:3000/api/products").then((response) => {
        console.log(response.data);
        this.products = response.data;
      });
    },
    // createProduct: function () {
    //   console.log("in products create");
    //   var params = {
    //     name: "xbox",
    //     description: "gaming console",
    //   };
    // },
    //   axios.post("http://localhost:3000/api/products").then((response) => {
    //   console.log(response.data);

    // })
  },
};
</script>