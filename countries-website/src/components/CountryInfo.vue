<template>
<h2>Country Info Component</h2>
<div v-if="item">
<div>Name: {{ item.name }}</div>
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
  url: "https://restcountries.eu/rest/v2/all?fields=name;population;region;capital;nativeName;subregion;topLevelDomain;currencies;languages;borders" + this.name,
})
  .then((response) => {
    this.item = response.data;
  })
  .catch((err) => console.log(err));
},
};
</script>