<template>
  <header>
    <div>
      <ul>
        <li><a href="">Where in the world?</a></li>
        <li><button>Dark Mode</button><a href=""></a></li>
      </ul>
    </div>
  </header>
</template>
<script>
export default {};
</script>
<style scoped lang="scss">
header {
  box-shadow: 1px 1px 10px #888888;
  height: 100px;
}

ul {
  display: flex;
  margin: 0;

    li {
      margin-top: 20px;
      margin-right: 30px;
      padding: 20px;
      list-style-type: none;

      button {
        border: none;
        background-color: transparent;
        cursor: pointer;
      }
  }


    li:nth-child(2) {
    margin-left: auto;
  }
  
  
}




</style>
