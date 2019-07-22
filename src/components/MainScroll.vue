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
      <div class="graphic" slot="graphic">{{ currStep }}</div>
      <div class="step" data-step-no="1">step 1</div>
      <div class="step" data-step-no="2">step 2</div>
      <div class="step" data-step-no="3">step 3</div>
    </Scrollama>
    <div class="outro">
      Lorem ipsum dolor sit amet consectetur adipisicing elit. Soluta, at velit
      sint facere ipsam doloremque placeat vel impedit sapiente alias.
    </div>
  </div>
</template>

<script>
import "intersection-observer";
import Scrollama from "vue-scrollama"; // https://github.com/shenoy/vue-scrollama#vue-scrollama

export default {
  props: [],
  components: {
    Scrollama
  },

  data() {
    return {
      currStep: null
    };
  },

  methods: {
    stepEnterHandler({ element, index, direction }) {
      // handle the step-event as required here
      console.log(element, index, direction);
      this.currStep = "Hello " + element.dataset.stepNo;
    }
  }
};
</script>

<style src="vue-scrollama/dist/vue-scrollama.css"></style>

<style>
.intro,
.outro {
  padding: 20vh;
}
.graphic {
  height: 100vh;
  border: 1px solid #ccc;
  background-color: #eee;
  font-size: 10rem;
  display: flex;
  align-items: center;
  justify-content: center;
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
#app {
  font-family: "Avenir", Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}
</style>