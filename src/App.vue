<template>
  <div class="app" :class="mode">
    <Header :mode="mode" @toggle="toggle"></Header>
    <router-view />
  </div>
</template>

<script>
import Header from "@/components/Header.vue";
export default {
  data() {
    return {
      mode: "light",
    };
  },
  components: {
    Header,
  },
  methods: {
    toggle() {
      if (this.mode === "dark") {
        this.mode = "light";
      } else {
        this.mode = "dark";
      }
    },
  },
};
</script>

<style lang="scss">
* {
  margin: 0;
  padding: 0;
  font-family: "Roboto", sans-serif;
}


.app {
  background-color: hsl(0, 0%, 97%);
  color: hsl(200, 15%, 8%);
  transition: background 0.3s ease-in-out;
  min-height: 100vh;
}

.dark {
  background-color: #192734;
  color: hsl(0, 0%, 100%);
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
