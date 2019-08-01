<template>
  <div class="container home">
    <h1>{{ message }}</h1>
    <div v-for="product in products">
      <h2>{{ product.name }}</h2>
      <img v-bind:src="product.image_url" alt="" />
      <div>
        <button v-on:click="showProduct(product)">More info</button>
      </div>
      <div v-if="product === currentProduct">
        <p>Price: {{ product.price }}</p>
        <p>Description: {{ product.description }}</p>
        <h4>Edit product</h4>
        <div>
          Name:
          <input v-model="product.name" type="text" />
          Price:
          <input v-model="product.price" type="text" />
          Description:
          <input v-model="product.description" type="text" />
          <button v-on:click="updateProduct(product)">Update Product</button>
        </div>
        <button v-on:click="destroyProduct(product)">Delete Product</button>
      </div>
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
      products: [],
      currentProduct: {}
    };
  },
  created: function() {
    axios.get("/api/products").then(response => {
      this.products = response.data;
      console.log(this.products);
    });
  },
  methods: {
    showProduct: function(inputProduct) {
      if (this.currentProduct === inputProduct) {
        this.currentProduct = {};
      } else {
        this.currentProduct = inputProduct;
      }
    },
    updateProduct: function(inputProduct) {
      var params = {
        name: inputProduct.name,
        supplier: inputProduct.supplier,
        price: inputProduct.price,
        description: inputProduct.description,
        image_url: inputProduct.imageUrl
      };
      axios.patch("/api/products/" + inputProduct.id, params).then(response => {
        console.log("Update successful", response.data);
        inputProduct.name = response.data.name;
        inputProduct.supplier = response.data.supplier;
        inputProduct.price = response.data.price;
        inputProduct.description = response.data.description;
        inputProduct.imageUrl = response.data.imageUrl;
      });
    },
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
