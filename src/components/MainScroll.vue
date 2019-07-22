<template>
  <div class="main-container">
    <div class="intro">
      <p>
        Lorem ipsum dolor sit amet consectetur adipisicing elit. Soluta, at
        velit sint facere ipsam doloremque placeat vel impedit sapiente alias.
      </p>
      <p>SCROLL TO CONTINUE</p>
    </div>
    <Scrollama :debug="true" :offset="0.5" v-on:step-enter="stepEnterHandler">
      <Map class="graphic" slot="graphic" v-on:map-clicked="mapClicked"></Map>
      <div class="step" data-step-no="1">Seattle</div>
      <div class="step" data-step-no="2">Los Angeles</div>
      <div class="step" data-step-no="3">New York</div>
    </Scrollama>
    <div class="outro">
      Lorem ipsum dolor sit amet consectetur adipisicing elit. Soluta, at velit
      sint facere ipsam doloremque placeat vel impedit sapiente alias.
    </div>
  </div>
</template>

<script>
import "intersection-observer";
import Map from "./Map";
import Scrollama from "vue-scrollama"; // https://github.com/shenoy/vue-scrollama#vue-scrollama

export default {
  props: [],
  components: {
    Map,
    Scrollama
  },

  data() {
    return {
      currStep: null
    };
  },

  methods: {
    stepEnterHandler({ element, index, direction }) {
      Map.methods.moveTo(index);
    },

    mapClicked({ lng, lat }) {
      console.log("My child was clicked");
      console.log("Longitude : ", lng);
      console.log("Lattitude : ", lat);
      // Map.methods.moveTo(0);
    }
  }
};
</script>

<style src="vue-scrollama/dist/vue-scrollama.css"></style>

<style>
.intro,
.outro {
  padding: 33vh;
}
.graphic {
  height: 100vh;
  width: 100vw;
}
.step {
  padding: 15vh 0;
  width: 50%;
  margin: 0 auto 30vh;
  background-color: beige;
  border: 1px solid #ccc;
  display: flex;
  align-items: center;
  justify-content: center;
}
</style>