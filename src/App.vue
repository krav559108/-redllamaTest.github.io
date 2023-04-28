<template>
  <div class="main">
    <background-layer></background-layer>
  </div>
</template>

<script>
import BackgroundLayer from './components/BgrLayer.vue';


export default {
  name: "App",
  components: {
    BackgroundLayer,
  },
};
</script>

<style>
body {
  margin: 0;
  padding: 0;
  padding: env(safe-area-inset-top) env(safe-area-inset-right) env(safe-area-inset-bottom) env(safe-area-inset-left);


}
.main {
  box-sizing: border-box;
  display: flex;
  height: 100vh;
}
</style>
