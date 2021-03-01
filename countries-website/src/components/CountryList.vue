<template>
  <div>
    <h1>Country List</h1>
    <ul>
      <li v-for="item in countries" :key="item.name">{{ item.name }} 
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
      countries: []
    };
  },
  created() {
    axios
      .get("https://restcountries.eu/rest/v2/all?fields=name;population;region;capital;nativeName;subregion;topLevelDomain;currencies;languages;borders")
      .then(response => {
        this.countries = response.data;
      })
      .catch(err => console.log(err));
  }
};
</script>