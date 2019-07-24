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
      <LeftMenu v-on:menu-action="menuAction" v-bind:coordinates="coords"></LeftMenu>
    </Scrollama>
    <div>
      <p>Something</p>
    </div>
    <div class="outro">
      Lorem ipsum dolor sit amet consectetur adipisicing elit. Soluta, at velit
      sint facere ipsam doloremque placeat vel impedit sapiente alias.
    </div>
  </div>
</template>

<script>
import "intersection-observer";
import { CONST } from "./../utils/constants";
import { ACTIONS } from "./../utils/events";
import Map from "./Map";
import LeftMenu from "./LeftMenu";
import Scrollama from "vue-scrollama"; // https://github.com/shenoy/vue-scrollama#vue-scrollama

export default {
  props: [],
  components: {
    Map,
    LeftMenu,
    Scrollama
  },

  data() {
    return {
      coords: { longitude: "", lattitude: "" }
    };
  },

  methods: {
    stepEnterHandler({ element, index, direction }) {
      if (element.classList.contains("step") && direction === CONST.DOWN) {
        Map.methods.moveTo(index);
      }
    },

    mapClicked({ lng, lat }) {
      console.log("My child was clicked");
      this.coords.longitude = lng;
      this.coords.lattitude = lat;
    },

    menuAction({ action }) {
      console.log(action);

      // TODO : Create a dispatch service
      if (action === ACTIONS.TO_SEATTLE) {
        Map.methods.moveTo(0);
      }
    }
  }
};
</script>

<style src="vue-scrollama/dist/vue-scrollama.css"></style>
<style>
.main-container {
  z-index: 0;
}
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