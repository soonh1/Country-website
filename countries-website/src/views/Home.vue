<template>
  <div class="home">
    <Search />
    <Filter />
    <CountryList msg="Welcome to Your Vue.js App" />
  </div>
</template>

<script>
// @ is an alias to /src
import CountryList from "@/components/CountryList.vue";
import Filter from "@/components/Filter.vue";
import Search from "@/components/Search.vue";

export default {
  name: "Home",
  components: {
    CountryList,
    Filter,
    Search
  }
};
</script>
