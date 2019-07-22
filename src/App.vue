<template>
  <div id="app">
    <MainScroll></MainScroll>
  </div>
</template>

<script>
import MainScroll from "./components/MainScroll";

export default {
  name: "app",
  components: {
    MainScroll
  }
};
</script>

<style>
#app {
  font-family: "Avenir", Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  color: #2c3e50;
}
</style>
