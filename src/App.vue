<template>
  <div id="app">
    <EventMediator></EventMediator>
  </div>
</template>

<script>
import EventMediator from "./components/EventMediator";

export default {
  name: "app",
  components: {
    EventMediator
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
