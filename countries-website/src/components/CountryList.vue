<template>
  <div>
    <h1>Country List</h1>
    <h3>Filter By Category</h3>
    <select v-model="category">
      <option value="Accessories">Accessories</option>
      <option value="Laptop">Laptop</option>
      <option value="Stationary">Stationary</option>
    </select>
    <ul>
      <li v-for="product in filterProductsByCategory" :key="product.name">
        Product Name : {{ product.name }} - Price : {{ product.price }} ({{
          product.category
        }})
      </li>
    </ul>
    <ul class="wrapper">
      <li v-for="item in countries" :key="item.name">
        <div class="holder">
        <img class="imgsize" :src="item.flag" alt="" />
        </div>
        <p>{{ item.name }}</p>
        <p>Population: {{ item.population }}</p>
        <p>Region: {{ item.region }}</p>
        <p>Capital: {{ item.capital }}</p>
        <router-link :to="`/Details/${item.name}`">View details</router-link>
      </li>
    </ul>
  </div>
</template>

<script>
import axios from "axios";

export default {
  data() {
    return {
      countries: [],
      category: "",
      products: [
        { name: "Keyboard", price: 44, category: "Accessories" },
        { name: "Mouse", price: 20, category: "Accessories" },
        { name: "Monitor", price: 399, category: "Accessories" },
        { name: "Dell XPS", price: 599, category: "Laptop" },
        { name: "MacBook Pro", price: 899, category: "Laptop" },
        { name: "Pencil Box", price: 6, category: "Stationary" },
        { name: "Pen", price: 2, category: "Stationary" },
        { name: "USB Cable", price: 7, category: "Accessories" },
        { name: "Eraser", price: 2, category: "Stationary" },
        { name: "Highlighter", price: 5, category: "Stationary" },
      ],
    };
  },
  computed: {
    filterProductsByCategory: function() {
      return this.products.filter(
        (product) => !product.category.indexOf(this.category)
      );
    },
  },

  created() {
    axios
      .get(
        "https://restcountries.eu/rest/v2/all?fields=name;population;region;capital;flag"
      )
      .then((response) => {
        this.countries = response.data;
      })
      .catch((err) => console.log(err));
  },
};
</script>

<style scoped lang="scss">
.wrapper {
  display: grid;
  grid-template-columns: repeat( auto-fill, minmax(500px, 1fr) );
}

.holder {
  display: inline;
}

.imgsize{
  max-width: 80%;
  height: auto;
}
</style>