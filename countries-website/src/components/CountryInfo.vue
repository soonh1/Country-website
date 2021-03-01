<template>
<h2>Country Info Component</h2>
<div v-if="item">
    <img :src="item.flag" alt="">
<div>Name: {{ name }}</div>
<div>Population: {{ item.population }}</div>
<div>Region: {{ item.region }}</div>
<div>Capital: {{ item.capital }}</div>
<div>Native Name: {{ item.nativeName }}</div>
<div>Subregion: {{ item.subregion }}</div>
<div>Top level domain: {{ item.topLevelDomain.[0] }}</div>
<div>Languages: 
    <ul>
        <li v-for="language in item.languages" :key="language">{{language.name}}</li>
    </ul>
</div>
<div>Currencies: 
    <ul>
        <li v-for="currency in item.currencies" :key="currency">{{currency.name}}</li>
    </ul>
    </div>
</div>
<div>Border Countries: 
    <ul>
        <li v-for="border in borders" :key="border">{{border}}</li>
    </ul>
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
  url: "https://restcountries.eu/rest/v2/name/" + this.name,
})
  .then((response) => {
    this.item = response.data.[0];
    this.borders = response.data.[0].borders;
  })
  .catch((err) => console.log(err));
},
};
</script>