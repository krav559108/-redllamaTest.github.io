<template>
  <div class="_02 imgContainer">
    <div class="innerContainer">
      <img
        class="catchPhrase"
        src="../assets/catchPhrase.png"

      />
      <img class="logo pb-10" src="../assets/logo.png"  />
      <img class="packs pb-10" src="../assets/packs.png"  />
      <img
        class="btn pb-10"
        src="../assets/btn.png"
        @click="redirect"

      />
      <img class="rules" src="../assets/rules.png" />
    </div>
    <front-layer ></front-layer>
  </div>
</template>

<script>
import FrontLayer from "./FrontLayer.vue";

export default {
  components: { FrontLayer },

  name: "backgroundFlex",
  data() {
    return {};
  },
  methods: {
    redirect() {
      window.open("https://redllama.ru/");
    },
  },
};
</script>

<style>
img {
  display: block;
  width: 100%;
}
.pb-10 {
  /* padding-bottom: 5%; */
}
.imgContainer {
  position: relative;
  border: 2px solid rgb(216, 216, 216);
  background-image: url("../assets/bgr.png");
  background-size: cover;
  display: flex;
  flex-direction: column;
  width: 100%;
  margin: auto;
  max-width: 400px;
  max-height: 100vh;
}
.innerContainer {
  display: flex;
  flex-direction: column;
  margin: auto;
  height: 100%;
  padding: 5% 10% 2%;
}
._02 {
  display: flex;
  justify-content: center;

  max-width: 800px;
}
.bgr {
  width: 100%;
  height: 100%;

  display: block;
  object-fit: cover;
  z-index: 2;
}
.logo {
  display: block;
  object-fit: contain;
}
.btn {
  object-fit: contain;
}
.rules {

  object-fit: contain;
  transform: scaleX(120%);
}
.catchPhrase {
  object-fit: contain;
}

.packs {
  margin: 3% 0;
  transform: scale(100%);
  object-fit: contain;
}
</style>
