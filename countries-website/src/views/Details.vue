<template>

  <router-link to="/">Back</router-link>
  <CountryInfo :name="itemname"/>
</template>

<script>
import CountryInfo from "../components/CountryInfo.vue";
export default {
  components: { CountryInfo },
  data() {
    return {
      itemname: "",
    };
  },
  created() {
    this.itemname = this.$route.params.name;
  },
};
</script>