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
    <!-- Old code
      <ul>
      <li v-for="item in countries" :key="item.name">
        <img :src="item.flag" alt="" />
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
