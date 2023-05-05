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
  padding: env(safe-area-inset-top) env(safe-area-inset-right)
    env(safe-area-inset-bottom) env(safe-area-inset-left);
  overflow-x: hidden;
}
.main {
  box-sizing: border-box;
  display: flex;
  height: 100vh;
}
</style>
