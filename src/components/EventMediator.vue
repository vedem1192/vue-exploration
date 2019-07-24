<template>
  <div>
    <Map id="map"></Map>
    <Scrollama v-on:scroll-action="handleScrollEvent"></Scrollama>
    <LeftMenu id="left-menu" v-bind:coordinates="coordinates"></LeftMenu>
  </div>
</template>

<script>
import Map from "./Map";
import Scrollama from "./Scrollama";
import LeftMenu from "./LeftMenu";

export default {
  name: "EventMediator",

  components: {
    Map,
    Scrollama,
    LeftMenu
  },

  data() {
    return {
      coordinates: { longitude: 10, lattitude: 12 }
    };
  },

  methods: {
    handleScrollEvent({ index }) {
      //   Map.methods.moveTo(index);
      console.log("Received", index);
    }
  }
};
</script>

<style scoped>
#map {
  position: fixed;
  top: 0;
  right: 0;
  height: 100vh;
  width: 100vw;
  overflow: auto;
  z-index: -10;
}

#left-menu {
  float: left;
}
</style> 
