<template>
  <h1>Country Page</h1>
  <CountryInfo :name="itemname"></CountryInfo>
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
    this.itemname = this.$route.params.id;
  },
};
</script>