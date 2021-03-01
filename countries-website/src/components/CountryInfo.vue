<template>
<h2>Country Info Component</h2>
<div v-if="item">
<div>Name: {{ name }}</div>
<div>Population: {{ item.[0].population }}</div>
<div>Region: {{ item.[0].region }}</div>
<div>Capital: {{ item.[0].capital }}</div>
<div>Native Name: {{ item.[0].nativeName }}</div>
<div>Subregion: {{ item.[0].subregion }}</div>
<div>Top level domain: {{ item.[0].topLevelDomain.[0] }}</div>
<div>Languages: {{ item.[0].languages.[0].name }}</div>
<div>Currencies: {{ item.[0].currencies.[0].name }}</div>
</div>
</template>

<script>
import axios from "axios";
export default {
data() {
return {
  item: null,
};
},
props: ["name"],
created() {
axios({
  method: "get",
  url: "https://restcountries.eu/rest/v2/name/" + this.name,
})
  .then((response) => {
    this.item = response.data;
  })
  .catch((err) => console.log(err));
},
};
</script>