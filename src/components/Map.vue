<template>
  <div id="map"></div>
</template>

<script>
import mapboxgl from "mapbox-gl";
import { MAPBOX_ACCESS_TOKEN, MAPBOX_STYLE } from "./../config/dev.env";
import { locations } from "./../assets/data/CityCameraSetting";
let map;

export default {
  name: "Map",

  mounted() {
    this.createMap();
    this.initControls();
  },

  methods: {
    createMap() {
      console.log("Creating map");
      mapboxgl.accessToken = MAPBOX_ACCESS_TOKEN;

      map = new mapboxgl.Map({
        container: "map",
        style: MAPBOX_STYLE,
        center: [-122.33207, 47.60621],
        zoom: 13
      });
      console.log("Map created ", map);
    },

    initControls() {
      map.on("click", point => {
        this.$emit("map-clicked", point.lngLat);
      });
    },

    moveTo(index) {
      map.flyTo(locations[index].camera);
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