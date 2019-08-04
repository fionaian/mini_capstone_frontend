<template>
  <div class="container home">
    <h1>{{ message }}</h1>
    <div v-for="product in products">
      <h2>{{ product.name }}</h2>
      <img v-bind:src="product.image_url" alt="" />
      <router-link v-bind:to="`/products/${product.id}`">More info</router-link>
    </div>
  </div>
</template>

<style>
img {
  width: 100%;
}
</style>

<script>
import axios from "axios";

export default {
  data: function() {
    return {
      message: "THE S N A C K SHOP!",
      products: []
    };
  },
  created: function() {
    axios.get("/api/products").then(response => {
      this.products = response.data;
      console.log(this.products);
    });
  },
  methods: {
    // updateProduct: function(inputProduct) {
    //   var params = {
    //     name: inputProduct.name,
    //     supplier: inputProduct.supplier,
    //     price: inputProduct.price,
    //     description: inputProduct.description,
    //     image_url: inputProduct.imageUrl
    //   };
    //   axios.patch("/api/products/" + inputProduct.id, params).then(response => {
    //     console.log("Update successful", response.data);
    //     inputProduct.name = response.data.name;
    //     inputProduct.supplier = response.data.supplier;
    //     inputProduct.price = response.data.price;
    //     inputProduct.description = response.data.description;
    //     inputProduct.imageUrl = response.data.imageUrl;
    //   });
    // },
    destroyProduct: function(inputProduct) {
      axios.delete("/api/products/" + inputProduct.id).then(response => {
        console.log("Delete successful", response.data);
        var index = this.products.indexOf(inputProduct);
        this.products.splice(index, 1);
      });
    }
  }
};
</script>
