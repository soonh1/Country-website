<template>
  <header>
    <h1>Where in the world?</h1>
    <button>Dark mode</button>
  </header>
</template>
<script>
export default {};
</script>
<style scoped lang="scss">
header {
  box-shadow: 1px 1px 10px #888888;
  height: 100px;
  display: grid;
  grid-template-columns: auto auto;
  grid-gap: 500px;
  h1 {
    margin: auto 50px;
    text-align: start;
  }
  button {
  }
}
</style>
