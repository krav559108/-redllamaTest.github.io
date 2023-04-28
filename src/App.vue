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

  padding-top: constant(safe-area-inset-top); /* iOS 11.0 */
  padding-top: env(safe-area-inset-top); /* iOS 11.2 */


}
.main {
  box-sizing: border-box;
  display: flex;
  height: 100vh;
}
</style>
