<template>
  <div>
    <Map id="map" v-on:map-event="handleMapEvent"></Map>
    <Scrollama v-on:scroll-event="handleScrollEvent"></Scrollama>
    <LeftMenu id="left-menu" v-bind:coordinates="coordinates" v-on:menu-event="handleMenuEvent"></LeftMenu>
  </div>
</template>

<script>
import Map from "./Map";
import Scrollama from "./Scrollama";
import LeftMenu from "./LeftMenu";
import { EVENTS } from "./../utils/events";

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
    handleScrollEvent(event) {
      console.log("Received scroll event", event);
      Map.methods.moveTo(event.index);
    },

    handleMapEvent(event) {
      console.log("Received map event", event);
      this.coordinates = { longitude: event.lng, lattitude: event.lat };
    },

    handleMenuEvent(event) {
      console.log("Received menu event", event);
      if (event.action === EVENTS.TO_SEATTLE) {
        Map.methods.moveTo(0);
      }
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
