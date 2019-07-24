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
      <div class="step" data-step-no="1">Seattle</div>
      <div class="step" data-step-no="2">Los Angeles</div>
      <div class="step" data-step-no="3">New York</div>
    </Scrollama>
  </div>
</template>

<script>
import "intersection-observer";
import { EVENTS } from "./../utils/events";
import Scrollama from "vue-scrollama"; // https://github.com/shenoy/vue-scrollama#vue-scrollama

export default {
  components: {
    Scrollama
  },

  methods: {
    stepEnterHandler(event) {
      this.$emit(EVENTS.SCROLL, event);
    }
  }
};
</script>

<style src="vue-scrollama/dist/vue-scrollama.css"></style>
<style>
.main-container {
  z-index: 0;
}

.intro {
  background-color: white;
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