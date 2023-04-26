<template>
  <div class="_01" v-if="isFilled">
    <div class="Group_13 fade-in" v-show="isActive">
      <img class="frontPhrase" src="../assets/frontPhrase.png" />
      <img class="stickersAction" src="../assets/stickersAction.png" />
      <img class="arrows" src="../assets/arrows.png" />
      <img class="frontBackground" src="../assets/frontBackground.png" />
    </div>
    <div
      class="Group_10"
      @click="clickedOutside"
      @v-touch="clickedOutside"
      v-if="isFilled"
    >
      <Moveable
        class="moveableContainer"
        v-bind="moveable"
        v-if="isSecond"
        @drag="handleDrag"
        @dragEnd="disableSticker(2)"
      >
        <img
          class="Group_2 sticker85"

          src="../assets/Group-2.png"
        />
      </Moveable>
      <Moveable
        class="moveableContainer"
        v-bind="moveable"
        @drag="handleDrag"
        @dragEnd="disableSticker(5)"
        v-if="isFifth"
      >
        <img
          class="Group_5 sticker85"

          src="../assets/Group-5.png"
        />
      </Moveable>
      <Moveable
        class="moveableContainer"
        v-bind="moveable"
        @drag="handleDrag"
        v-if="isNineth"
        @dragEnd="disableSticker(9)"
      >
        <img
          class="Group_9 sticker70"
          v-show="isNineth"
          src="../assets/Group-9.png"
        />
      </Moveable>
      <Moveable
        class="moveableContainer"
        v-bind="moveable"
        @drag="handleDrag"
        v-if="isThird"
        @dragEnd="disableSticker(3)"
      >
        <img
          class="Group_3 sticker80"

          src="../assets/Group-3.png"
        />
      </Moveable>
      <Moveable
        class="moveableContainer"
        v-bind="moveable"
        @drag="handleDrag"
        @dragEnd="disableSticker(4)"
        v-if="isFourth"
      >
        <img
          class="Group_4 sticker60"

          src="../assets/Group-4.png"
        />
      </Moveable>
      <Moveable
        class="moveableContainer"
        v-bind="moveable"
        @drag="handleDrag"
        @dragEnd="disableSticker(8)"
        v-if="isEighth"
      >
        <img
          class="Group_8 sticker60"

          src="../assets/Group-8.png"
        />
      </Moveable>
      <Moveable
        class="moveableContainer"
        v-bind="moveable"
        @drag="handleDrag"
        @dragEnd="disableSticker(6)"
        v-if="isSixth"
      >
        <img
          class="Group_6 sticker65"

          src="../assets/Group-6.png"
        />
      </Moveable>
      <Moveable
        class="moveableContainer"
        v-bind="moveable"
        @drag="handleDrag"
        @dragEnd="disableSticker(7)"
        v-if="isSeventh"
      >
        <img
          class="Group_7 sticker80"

          src="../assets/Group-7.png"
        />
      </Moveable>
    </div>
  </div>
</template>

<script>
import Vue2TouchEvents from "vue2-touch-events";
import Moveable from "vue-moveable";
export default {
  components: {
    Moveable,
    Vue2TouchEvents,
  },
  data() {
    return {
      moveable: {
        draggable: true,
        throttleDrag: 0,
      },
      isActive: true,
      isFilled: true,
      isSecond: true,
      isThird: true,
      isFourth: true,
      isFifth: true,
      isSixth: true,
      isSeventh: true,
      isEighth: true,
      isNineth: true,
    };
  },
  methods: {
    clickedOutside() {
      this.isActive = false;
    },
    handleDrag({ target, transform }) {
      transform ? (this.isActive = false) : false;
      target.style.transform = transform;
    },
    disableSticker(num) {
      switch (num) {
        case 2:
          this.isSecond = false;
          break;
        case 3:
          this.isThird = false;
          break;
        case 4:
          this.isFourth = false;
          break;
        case 5:
          this.isFifth = false;
          break;
        case 6:
          this.isSixth = false;
          break;
        case 7:
          this.isSeventh = false;
          break;
        case 8:
          this.isEighth = false;
          break;
        case 9:
          this.isNineth = false;
          break;
      }
    },
  },
  computed: {
    disableLayer() {
      if (
        !this.isSecond &&
        !this.isThird &&
        !this.isFourth &&
        !this.isFifth &&
        !this.isSixth &&
        !this.isSeventh &&
        !this.isEighth &&
        !this.isNineth
      ) {
        this.isFilled = false;
      }
    },
  },
};
</script>

<style>
.moveableContainer {
  position: absolute;
  width: 100%;
  height: 100%;
}
.moveable-line {
  display: none !important;
}
.sticker85 {
  width: 85%;
}
.sticker80 {
  width: 80%;
}
.sticker70 {
  width: 70%;
}
.sticker65 {
  width: 65%;
}
.sticker60 {
  width: 60%;
}
._01 {
  position: absolute;
  left: 0px;
  top: 0px;
  width: 100%;
  height: 100%;
  z-index: 26;
  display: flex;
  align-items: center;
  justify-content: center;
}
.Group_13 {
  position: relative;
  display: flex;
  flex-direction: column;
  width: 100%;

  z-index: 25;
}
.frontPhrase {
  position: absolute;
  top: 7%;
  left: 50%;
  width: 45%;
  transform: translateX(-50%);
}
.stickersAction {
  position: absolute;
  bottom: 38%;
  left: 50%;
  width: 30%;
  transform: translateX(-50%);
}
.arrows {
  position: absolute;
  bottom: 15%;
  left: 50%;
  width: 20%;
  transform: translateX(-50%);
}
.frontBackground {
}
.Group_10 {
  position: absolute;
  left: 0px;
  top: 0px;
  width: 100%;
  height: 100%;
  z-index: 19;
}
.Group_5 {
  position: absolute;
  left: 10%;
  bottom: 6%;
  z-index: 18;
}
.Group_2 {
  position: absolute;
  left: 4%;
  top: 5%;
  z-index: 17;
}
.Group_9 {
  position: absolute;
  left: 0;
  top: 0;
  z-index: 16;
}
.Group_3 {
  position: absolute;
  right: 0;
  z-index: 15;
}
.Group_4 {
  position: absolute;
  left: 0;
  top: 27%;
  z-index: 14;
}
.Group_8 {
  position: absolute;
  right: 0;
  top: 30%;
  z-index: 13;
}
.Group_6 {
  position: absolute;
  right: 0;
  bottom: 0;
  z-index: 12;
}
.Group_7 {
  position: absolute;
  left: 0;
  bottom: 0;
  z-index: 11;
}
.fade-in {
  opacity: 1;
  animation-name: fadeInOpacity;
  animation-iteration-count: 1;
  animation-timing-function: ease-in;
  animation-delay: 0.5s;
  animation-duration: 1s;
}

@keyframes fadeInOpacity {
  0% {
    opacity: 0;
  }
  100% {
    opacity: 1;
  }
}
</style>
