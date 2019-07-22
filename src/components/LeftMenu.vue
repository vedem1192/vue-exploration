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
import { ACTIONS } from "./../common/actions";

export default {
  name: "leftMenu",
  props: ["coordinates"],

  methods: {
    buttonWasClicked() {
      console.log("Button was clicked");
      this.$emit(ACTIONS.MENU, { action: ACTIONS.TO_SEATTLE });
    }
  }
};
</script>


<style>
#left-menu {
  float: left;
  height: 500px;
  width: 300px;
  background-color: aquamarine;
  z-index: 2;
  padding: 2em;
}
</style>
