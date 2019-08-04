<template>
  <div class="container home">
    Search:
    <input v-model="searchFilter" type="text" />
    <div class="row">
      <div v-for="product in filterBy(products, searchFilter, 'name')" class="col-sm-4">
        <div class="card">
          <img v-bind:src="product.image_url" class="card-img-top" alt="..." />
          <div class="card-body">
            <h2 class="card-name">{{ product.name }}</h2>
            <router-link v-bind:to="`/products/${product.id}`">More info</router-link>
          </div>
        </div>
      </div>
    </div>
  </div>
</template>

<style>
img {
  width: 100%;
}
.card {
  margin-bottom: 2rem;
}
</style>

<script>
import axios from "axios";
import Vue2Filters from "vue2-filters";
export default {
  mixins: [Vue2Filters.mixin],
  data: function() {
    return {
      message: "Welcome to the Snack Shop!",
      products: [],
      searchFilter: ""
    };
  },
  created: function() {
    axios.get("/api/products").then(response => {
      this.products = response.data;
      console.log(this.products);
    });
  },
  methods: {}
};
</script>
