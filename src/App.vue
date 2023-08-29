<template>
  <div id="app">
      <router-view></router-view>
  </div>
</template>

<script>

export default {
  name: 'App',
  components: {
  }
}
</script>

<style>
  #app {
    font-family: Avenir, Helvetica, Arial, sans-serif;
    -webkit-font-smoothing: antialiased;
    -moz-osx-font-smoothing: grayscale;
    text-align: center;
    color: #2c3e50;
    margin: 0;
    padding: 0;
    background-color: rgb(44, 62, 80);
    width: 100%;
    height: 100%;
  }

  body{
    margin: 0;
    height: 100%;
    width: 100%;
    background-color: rgb(0, 10, 10);
  }

  html {
    height: 100%;
  }
</style>
