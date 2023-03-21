<template>
  <div class="container" v-if="item">
    <img class="img" :src="item.flag" alt="" />

    <div class="wrapper">
      <div class="countryname">{{ name }}</div>
      <div class="text-flex">
        <div class="text1">
          <div>
            <p><b>Population:</b> {{ item.population }}</p>
          </div>
          <div>
            <p><b>Region:</b> {{ item.region }}</p>
          </div>
          <div>
            <p><b>Capital:</b> {{ item.capital }}</p>
          </div>
          <div>
            <p><b>Native Name:</b> {{ item.nativeName }}</p>
          </div>
          <div>
            <p><b>Subregion:</b> {{ item.subregion }}</p>
          </div>
        </div>
        <div class="text2">
          <div>
            <p><b>Top level domain:</b> {{ item.topLevelDomain.[0] }}</p>
          </div>
          <div>
            <b>Languages:</b>
            <ul>
              <li v-for="language in item.languages" :key="language">
                {{ language.name }}
              </li>
            </ul>
          </div>
          <div>
            <b>Currencies:</b>
            <ul>
              <li v-for="currency in item.currencies" :key="currency">
                {{ currency.name }}
              </li>
            </ul>
          </div>
        </div>
      </div>
      <div class="borders">
        <b>Border Countries:</b>
        <ul>
          <li v-for="border in borders" :key="border">
            <button>{{ border }}</button>
          </li>
        </ul>
      </div>
    </div>
  </div>
</template>

<script>
import axios from "axios";
export default {
data() {
return {
  item: null
};
},
props: ["name"],
created() {
axios({
  method: "get",
  url: "https://restcountries.com/v2/name/" + this.name,
})
  .then((response) => {
    this.item = response.data.[0];
    this.borders = response.data.[0].borders;
  })
  .catch((err) => console.log(err));
},
};
</script>

<style scoped lang="scss">
.container {
  display: flex;
  text-align: left;
  justify-content: center;
  align-items: center;
  margin: 20px;
}

p {
  line-height: 1.8rem;
}

.img {
  width: 500px;
  height: auto;
  margin: 2vw;
}

.wrapper {
  margin: 2vw;
}

.text-flex {
  display: flex;
  justify-content: space-between;
}

.text1 {
}
.text2 {
  ul {
    display: inline-flex;
    margin-top: 0.5rem;
    li {
      margin-left: 1rem;
    }
  }
}

.borders {
  margin-top: 1rem;
  ul {
    display: inline-flex;
    li {
      margin-left: 1rem;
      button {
        width: 40px;
      }
    }
  }
}

ul {
  display: inline-flex;
  list-style: none;
}

.countryname {
  font-size: 1.5rem;
  font-weight: 600;
  margin-bottom: 1rem;
}
</style>
