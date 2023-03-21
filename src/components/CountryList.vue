<template>
  <div>
    <!-- testing 
    <p>{{ countriesCategory }}</p>
    <input type="text" v-model="username" placeholder="Search for a robot" />
    <ul class="wrapper">
      <li v-for="item in test" :key="item.username">
        <router-link :to="`/Details/${item.username}`">
          <div class="holder">
            <img class="imgsize" :src="item.avatar" alt="" />
          </div>
          <div class="text">
            <p style="font-weight:bold;">{{ item.first_name }}</p>
            <p>Gender: {{ item.gender }}</p>
            <p>Job: {{ item.employment.title }}</p>
            <p>Email: {{ item.email }}</p>
          </div>
        </router-link>
      </li>
    </ul>
    
    -->
    <div class="filter">
      <input type="text" v-model="name" placeholder="Search for a country.." />
      <select v-model="countriesCategory">
        <option value="" disabled selected hidden>Filter by Region</option>
        <option value="">All</option>
        <option value="Africa">Africa</option>
        <option value="America">America</option>
        <option value="Asia">Asia</option>
        <option value="Europe">Europe</option>
        <option value="Oceania">Oceania</option>
      </select>
    </div>

    <!-- filter countries by name and category -->
    <ul class="wrapper">
      <li v-for="item in filterCountriesBycCategory" :key="item.name">
        <router-link :to="`/Details/${item.name}`">
          <div class="holder">
            <img class="imgsize" :src="item.flag" alt="" />
          </div>
          <div class="text">
            <p style="font-weight:bold;">{{ item.name }}</p>
            <p>Population: {{ item.population }}</p>
            <p>Region: {{ item.region }}</p>
            <p>Capital: {{ item.capital }}</p>
          </div>
        </router-link>
      </li>
    </ul>
  </div>
</template>

<script>
import axios from "axios";

export default {
  props: ["mode"],
  data() {
    return {
      countries: [],
      RandomUser: [],
      countriesCategory: "",
      name: "",
      username: "",
    };
  },
  computed: {
    filterCountriesBycCategory: function() {
      return this.countries.filter(
        (item) =>
          !item.region.indexOf(this.countriesCategory) &&
          !item.name.toLowerCase().indexOf(this.name.toLowerCase())
      );
    },
    test: function() {
      return this.RandomUser.filter(
        (item) => !item.username.indexOf(this.username)
      );
    },
  },

  created() {
    axios
      .get(
        "https://restcountries.com/v2/all?fields=name,population,region,capital,flag"
      )
      .then((response) => {
        this.countries = response.data;
      })
      .catch((err) => console.log(err));
    axios
      .get("https://random-data-api.com/api/users/random_user?size=30")
      .then((response) => {
        this.RandomUser = response.data;
      })
      .catch((err) => console.log(err));
  },
};
</script>

<style scoped lang="scss">
.filter {
  display: flex;
  justify-content: space-between;
  margin: 25px 25px 0 25px;
  input {
    padding: 15px;
    width: 25rem;
    border-radius: 5px;
    border-style: none;
    &:focus {
      outline: none;
    }
  }
  select {
    padding: 15px;
    width: 10rem;
    border-radius: 5px;
    border-style: none;
    &:focus {
      outline: none;
    }
  }
}

.wrapper {
  display: grid;
  grid-template-columns: repeat(auto-fill, minmax(350px, 1fr));
}

li {
  margin: 25px;
  background-color: hsl(0, 0%, 100%);
  border-radius: 5px;
  transition: background 0.3s ease-in-out;
  p {
    color: hsl(200, 15%, 8%);
    text-decoration: none;
    line-height: 2rem;
    text-align: left;
  }
  a:hover,
  a:visited,
  a:link,
  a:active {
    text-decoration: none;
  }
}

.text {
  padding: 25px;
}

ul {
  list-style: none;
}

.holder {
  display: inline;
}

.imgsize {
  width: 100%;
  height: 180px;
  object-fit: cover;
  border-top-left-radius: 5px;
  border-top-right-radius: 5px;
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
