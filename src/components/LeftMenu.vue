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
export default {
  name: "leftMenu",
  props: ["coordinates"],

  methods: {
    buttonWasClicked() {
      console.log("Button was clicked");
      this.$emit("menu-action", { action: "go-to-seattle" });
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
