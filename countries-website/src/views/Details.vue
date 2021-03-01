<template>
  <h1>Country Page</h1>
  <country-info :name="itemname"></country-info>
</template>

<script>
import CountryInfo from "@/components/CountryInfo.vue";
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