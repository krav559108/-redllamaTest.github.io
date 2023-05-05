<template>
  <div class="main">
    <background-layer></background-layer>
    <!-- <Rectangle /> -->
  </div>
</template>

<script>
import BackgroundLayer from "./components/BgrLayer.vue";
import Rectangle from "./components/test.vue";

export default {
  name: "App",
  components: {
    BackgroundLayer,
    Rectangle,
  },
};
</script>

<style>
body {
  margin: 0;
  padding: 0;
  height: 100vh;
  overflow-x: hidden;
  overflow-y: auto;
}
.main {
  box-sizing: border-box;
  display: flex;
  height: 100vh;
}
</style>
