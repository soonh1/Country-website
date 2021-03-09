<template>
<div :class="theme">
  <Header></Header>
<button id="switch" @click="triggy()">Dark Mode</button>
  <router-view />
  </div>
</template>

<script>
import Header from "@/components/Header.vue";
export default {
  data() {
    return {
      theme: "theme-light"
    }
  },
  components: {
    Header,
  },
  methods:{
    triggy() {
      switch (this.theme) {
        case 'theme-light':
          this.theme = 'theme-dark';
          break;
        case 'theme-dark':
          this.theme = 'theme-light';
          break;
        default:
      }
    }
  }
};
</script>

<style lang="scss">
body {
  margin: 0;
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
