<template>
  <div>
    <h1>Country List</h1>
    <h3>Filter By Category</h3>
    <input type="text" v-model="name" placeholder="Filter By Name" />
    <select v-model="countriesCategory">
      <option value="">All</option>
      <option value="Africa">Africa</option>
      <option value="America">America</option>
      <option value="Asia">Asia</option>
      <option value="Europe">Europe</option>
      <option value="Oceania">Oceania</option>
    </select>
    <!-- filter countries by name and category -->
    <ul class="wrapper">
      <li v-for="item in filterCountriesBycCategory" :key="item.name">
        <router-link :to="`/Details/${item.name}`">
        <div class="holder">
        <img class="imgsize" :src="item.flag" alt="" />
        </div>
        <p style="font-weight:bold;">{{ item.name }}</p>
        <p>Population: {{ item.population }}</p>
        <p>Region: {{ item.region }}</p>
        <p>Capital: {{ item.capital }}</p>
        </router-link>
      </li>
    </ul>
  </div>
</template>

<script>
import axios from "axios";

export default {
  props: ['mode'],
  data() {
    return {
      countries: [],
      countriesCategory: "",
      name: "",
    };
  },
  computed: {
    filterCountriesBycCategory: function() {
      return this.countries.filter(
        (item) => !item.region.indexOf(this.countriesCategory) && !item.name.toLowerCase().indexOf(this.name.toLowerCase())
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
  grid-template-columns: repeat( auto-fill, minmax(350px, 1fr) );
}

li {
  margin: 25px;
  background-color:hsl(0, 0%, 100%);
  
  p {
    color: hsl(200, 15%, 8%);
    text-decoration: none;
  }
  a:hover, a:visited, a:link, a:active
{
    text-decoration: none;
}
}

ul {
  list-style: none;
}

.holder {
  display: inline;
}

.imgsize{
  width: 100%;
  height: 180px;
  object-fit: cover;
}

.dark {
  p {
    color: hsl(0, 0%, 100%);
  }
  li {
    background-color: hsl(209, 23%, 22%);
  }
}
</style>