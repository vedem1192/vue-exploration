<template>
  <div id="left-menu">
    <p>MENU</p>
    <button v-on:click="buttonWasClicked">To Seattle</button>
    <div>
      <p>Longitude : {{ coordinates.longitude }}</p>
      <p>Lattitude : {{ coordinates.lattitude }}</p>
    </div>
  </div>
</template>

<script>
import { EVENTS } from "./../utils/events";

export default {
  name: "leftMenu",
  props: ["coordinates"],

  methods: {
    buttonWasClicked() {
      console.log("Button was clicked");
      this.$emit(EVENTS.MENU, { action: EVENTS.TO_SEATTLE });
    }
  }
};
</script>


<style scope>
#left-menu {
  height: 80vh;
  margin: 4em;
  width: 300px;
  background-color: aquamarine;
  z-index: 2;
  padding: 2em;
}
</style>
