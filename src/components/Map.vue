<template>
  <div id="map"></div>
</template>

<script>
import mapboxgl from "mapbox-gl";
import { MAPBOX_ACCESS_TOKEN, MAPBOX_STYLE } from "./../config/dev.env";

export default {
  name: "Map",

  mounted() {
    this.createMap();
  },

  methods: {
    createMap() {
      mapboxgl.accessToken = MAPBOX_ACCESS_TOKEN;
      this.map = new mapboxgl.Map({
        container: "map",
        style: MAPBOX_STYLE,
        center: [-122.33207, 47.60621],
        zoom: 13
      });
    }
  }
};
</script>

<style scope>
#map {
  position: absolute;
  top: 0;
  bottom: 0;
  width: 100vw;
  overflow: auto;
  z-index: -10;
}
</style>