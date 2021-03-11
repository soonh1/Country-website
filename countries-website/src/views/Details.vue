<template>
  <router-link to="/">
    <button class="backbutton">
      <i class="fa fa-long-arrow-left" aria-hidden="true"></i>
      <p>Back</p>
    </button>
</router-link>
  <CountryInfo :name="itemname" />
</template>

<script>
import CountryInfo from "../components/CountryInfo.vue";
export default {
  props: ["mode"],
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
<style scoped lang="scss">
@import url('https://cdnjs.cloudflare.com/ajax/libs/font-awesome/4.7.0/css/font-awesome.min.css');
a {
  text-decoration: none;
}
.backbutton {
  margin: 25px;
  padding: 12px 32px;
  text-align: center;
  display: flex;
  border: none;
  background-color: hsl(0, 0%, 100%);
  color: hsl(200, 15%, 8%);
  cursor: pointer;
  border-radius: 5px;
  box-shadow: 1px 1px 5px #888888;
  transition: background 0.3s ease-in-out;
  transition: box-shadow 0.3s ease-in-out;
  &:focus {
    outline: none;
  }
  i{
    margin: auto;
    font-size: 16px;
  }
  p{
    margin-left: 8px;
    font-size: 15px;
  }
}

.dark {
  .backbutton {
    background-color: hsl(209, 23%, 22%);
    color: hsl(0, 0%, 100%);
    box-shadow: 1px 1px 5px #292929;
  }
}
</style>
