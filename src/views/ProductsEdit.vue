<template>
  <div class="container new">
    <h1>Edit Product</h1>
    <div>
      Name:
      <input v-model="product.name" type="text" />
      Price:
      <input v-model="product.price" type="text" />
      Description:
      <input v-model="product.description" type="text" />
      Image URL:
      <input v-model="product.imageUrl" type="text" />
      <button v-on:click="updateProduct(product)">Update</button>
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
      product: {}
    };
  },
  created: function() {
    axios.get("/api/products/" + this.$route.params.id).then(response => {
      this.product = response.data;
    });
  },
  methods: {
    updateProduct: function(inputProduct) {
      var params = {
        name: inputProduct.name,
        price: inputProduct.price,
        description: inputProduct.description,
        image_url: inputProduct.imageUrl
      };
      axios.patch("/api/products/" + inputProduct.id, params).then(response => {
        this.$router.push("/");
      });
    }
  }
};
</script>
