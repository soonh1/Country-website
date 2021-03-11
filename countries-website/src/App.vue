<template>
<div class="app" :class="mode">
  <Header :mode="mode" @toggle="toggle"></Header>
  <CountryList :mode="mode" @toggle="toggle"></CountryList>
  <router-view />
  </div>
</template>

<script>
import Header from "@/components/Header.vue";
import CountryList from './components/CountryList.vue';
export default {
  name: 'app',
  data() {
    return {
      mode: 'light'
    }
  },
  components: {
    Header,
    CountryList
  },
  methods: {
    toggle () {
      if (this.mode === "dark") {
        this.mode = "light"
      } else {
        this.mode = "dark"
      }
    }
  }
};
</script>

<style lang="scss">
* {
  margin: 0;
  padding: 0;
  font-family: 'Roboto', sans-serif;
}

.app {
  background: #f3f3f3;
  color: #15202B;
  transition: background 0.3 ease-in-out;
}

.dark {
  background-color: #192734;
  color: #f3f3f3
}


:root {
  background-color: var(--color-primary);
   color: var(--font-color);
}

.theme-light {
   --color-primary: hsl(0, 0%, 98%);
   --color-secondary: hsl(0, 0%, 100%);
   --color-accent: hsl(0, 0%, 52%);
   --font-color: hsl(200, 15%, 8%);

}

.theme-dark {
   --color-primary: hsl(207, 26%, 17%);
   --color-secondary: hsl(209, 23%, 22%);
   --font-color: hsl(0, 0%, 100%);

}


#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
}

#nav {
  padding: 30px;

  a {
    font-weight: bold;
    color: #2c3e50;

    &.router-link-exact-active {
      color: #42b983;
    }
  }
}
</style>
