<template>
  <div class="_02 imgContainer">
    <div class="innerContainer">
      <img class="catchPhrase" src="../assets/catchPhrase.png" draggable="false" />
      <img class="logo mb-10" src="../assets/logo.png" draggable="false"/>
      <img class="packs mb-10" src="../assets/packs.png" draggable="false"/>
      <img class="btn" src="../assets/btn.png" @click="redirect" draggable="false" />
      <img class="rules" src="../assets/rules.png" draggable="false"/>
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
.mb-5 {
  margin-bottom: 5px;
}
.mb-10 {
  margin-bottom: 10px;
}
img {
  display: block;
  width: 100%;
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
  padding: 5% 10% 2%;
}
._02 {
  display: flex;
  justify-content: center;
  overflow: auto;
}
.bgr {
  width: 100%;
  height: 100%;
  max-width: 800px;
  max-height: 1200px;
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
  transform: scaleX(125%);
}
.catchPhrase {
  object-fit: contain;
}

.packs {
  margin: 3% 0;
  transform: scale(115%);
  object-fit: contain;
}
</style>
