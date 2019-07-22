<template>
  <mgl-map :accessToken="accessToken" :mapStyle.sync="mapStyle" :center="[-100, 40]" :zoom="4.2"></mgl-map>
</template>

<script>
import Mapbox from "mapbox-gl";
import { MglMap } from "vue-mapbox";
import { MAPBOX_ACCESS_TOKEN, MAPBOX_STYLE } from "./../config/dev.env";

export default {
  components: {
    MglMap
  },

  data() {
    return {
      accessToken: MAPBOX_ACCESS_TOKEN,
      mapStyle: MAPBOX_STYLE
    };
  },

  created() {
    console.log("Component created");
    this.map = null;
  },

  methods: {
    onMapLoaded(event) {
      // in component
      console.log("Map loaded");
      this.map = event.map;
      console.log("MAP : ", this.map);
    }
  }
};
</script>