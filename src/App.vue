<template>
  <div id="app">
    <!-- <main-scroll></main-scroll> -->
    <mgl-map></mgl-map>
  </div>
</template>

<script>
// import MainScroll from "./components/MainScroll";
import MglMap from "./components/Map";

export default {
  name: "app",
  components: {
    // MainScroll,
    MglMap
  }
};
</script>

<style>
#app {
  font-family: "Avenir", Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}
</style>
