<template>
  <div id="app">
    <!-- <img src="./assets/logo.png" /> -->
    <Calculator />
  </div>
</template>

<script>
import Calculator from "./components/Calculator";

export default {
  name: "App",
  components: {
    Calculator
  }
};
</script>

<style>
#app {
  background-color: rgba(29, 41, 58, 1);
  overflow: hidden;
  max-width: 100%;
}
</style>
