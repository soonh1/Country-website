<template>
  <div>
    <h1>Country List</h1>
    <h3>Filter By Category</h3>
    <input type="text" v-model="name" placeholder="Filter By Name"/>
    <select v-model="countriesCategory">
      <option value="">All</option>
      <option value="Africa">Africa</option>
      <option value="America">America</option>
      <option value="Asia">Asia</option>
      <option value="Europe">Europe</option>
      <option value="Oceania">Oceania</option>
    </select>
    <!-- filterCountriesBycCategory -->
    <ul>
      <li v-for="item in filterCountriesBycCategory" :key="item.name">
        <img :src="item.flag" alt="" />
        <p style="font-weight:bold;">{{ item.name }}</p>
        <p>Population: {{ item.population }}</p>
        <p>Region: {{ item.region }}</p>
        <p>Capital: {{ item.capital }}</p>
        <router-link :to="`/Details/${item.name}`">View details</router-link>
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
    </ul> -->
  </div>
</template>

<script>
import axios from "axios";

export default {
  data() {
    return {
      countries: [],
      countriesCategory: "",
    };
  },
  computed: {
    filterCountriesBycCategory: function() {
      return this.countries.filter(
        (item) => !item.region.indexOf(this.countriesCategory)
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