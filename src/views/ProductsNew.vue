<template>
  <div class="container new">
    <!--     <h1>New Product</h1>
    Name:
    <input v-model="name" type="text" />
    Supplier:
    <input v-model="supplier" type="text" />
    Price:
    <input v-model="price" type="text" />
    Description:
    <input v-model="description" type="text" />
    Image URL:
    <input v-model="imageUrl" type="text" />
    <button v-on:click="createProduct()">Create</button> -->
    <form v-on:submit.prevent="createProduct()">
      <h1>New Product</h1>
      <div class="form-group">
        Name:
        <input v-model="name" type="text" class="form-control" />
      </div>
      <div class="form-group">
        Price:
        <input v-model="price" type="text" class="form-control" />
      </div>
      <div class="form-group">
        Description:
        <input v-model="description" type="text" class="form-control" />
      </div>
      <div class="form-group">
        Image URL:
        <input v-model="image_url" type="text" class="form-control" />
      </div>
      <input type="submit" value="Create" class="btn btn-primary" />
    </form>
  </div>
</template>

<style></style>

<script>
import axios from "axios";
export default {
  data: function() {
    return {
      products: [],
      currentProduct: {},
      name: "",
      supplier: "",
      price: "",
      description: "",
      image_url: ""
    };
  },
  methods: {
    createProduct: function() {
      console.log("Add a product...");
      var params = {
        name: this.name,
        price: this.price,
        description: this.description,
        supplier_id: 1,
        image_url: this.image_url
      };
      axios
        .post("/api/products", params)
        .then(response => {
          console.log("Success", response.data);
          this.$router.push("/");
        })
        .catch(error => console.log(error.response));
    }
  }
};
</script>
