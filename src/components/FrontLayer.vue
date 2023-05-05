<template>
  <div class="_01" ref="mainContainer" v-if="!isCleared">
    <div class="Group_13 fade-in" v-if="isActive">
      <img class="frontPhrase" src="../assets/frontPhrase.png" />
      <img class="stickersAction" src="../assets/stickersAction.png" />
      <img class="arrows" src="../assets/arrows.png" />
      <img class="frontBackground" src="../assets/frontBackground.png" />
    </div>
    <div
      class="Group_10"
      @click="clickedOutside"
      @v-touch="clickedOutside"
      ref="frontContainer"
    >

    <!-- Сходить в магазин  -->
      <img
        class="Group_2"
        src="../assets/Group-2.png" 
        :style="{ transform: `translateX(${position}px)` }"
        ref="rect1"
        @mousedown="handleMouseDown"
        @touchstart="handleTouchStart"
        draggable="false"
      />


      <!-- Помыть посуду  -->
      <img
        class="Group_5"
        src="../assets/Group-5.png"
        :style="{ transform: `translateX(${position}px)` }"
        ref="rect2"
        @mousedown="handleMouseDown"
        @touchstart="handleTouchStart"
        draggable="false"
      />


      <!-- Погладить рубашки  -->
      <img
        class="Group_9 sticker70"
        src="../assets/Group-9.png"
        :style="{ transform: `translateX(${position}px)` }"
        ref="rect3"
        @mousedown="handleMouseDown"
        @touchstart="handleTouchStart"
        draggable="false"
      />


      <!-- Выбрать плитку для кухни  -->
      <img
        class="Group_3 sticker80"
        src="../assets/Group-3.png"
        :style="{ transform: `translateX(${position}px)` }"
        ref="rect4"
        @mousedown="handleMouseDown"
        @touchstart="handleTouchStart"
        draggable="false"
      />


      <!-- Доделать отчет после работы -->
      <img
        class="Group_4 sticker60"
        src="../assets/Group-4.png"
        :style="{ transform: `translateX(${position}px)` }"
        ref="rect5"
        @mousedown="handleMouseDown"
        @touchstart="handleTouchStart"
        draggable="false"
      />


      <!-- Заехать на почту  -->
      <img
        class="Group_8 sticker60"
        src="../assets/Group-8.png"
        :style="{ transform: `translateX(${position}px)` }"
        ref="rect6"
        @mousedown="handleMouseDown"
        @touchstart="handleTouchStart"
        draggable="false"
      />


      <!-- Испечь пирог для гостей  -->
      <img
        class="Group_6 sticker65"
        src="../assets/Group-6.png"
        :style="{ transform: `translateX(${position}px)` }"
        ref="rect7"
        @mousedown="handleMouseDown"
        @touchstart="handleTouchStart"
        draggable="false"
      />


      <!-- Полить растения соседей  -->
      <img
        class="Group_7 sticker80"
        src="../assets/Group-7.png"
        :style="{ transform: `translateX(${position}px)` }"
        ref="rect8"
        @mousedown="handleMouseDown"
        @touchstart="handleTouchStart"
        draggable="false"
      />
    </div>
  </div>
</template>

<script>
export default {
  components: {},
  data() {
    return {
      position: 0,
      startX: 0,
      currentX: 0,
      isDragging: false,
      isActive: true,
      isCleared: false,
    };
  },

  methods: {
    clickedOutside() {
      this.isActive = false;
    },
    handleMouseDown(event) {
      this.startX = event.clientX;
      this.activeRect = event.target;
      window.addEventListener("mousemove", this.handleMouseMove);
      window.addEventListener("mouseup", this.handleMouseUp);
      this.isActive = false;
    },
    handleMouseMove(event) {
      const diffX = event.clientX - this.startX;
      this.currentX = diffX;

      this.activeRect.style.transform = `translateX(${this.currentX}px)`;
    },
    handleMouseUp() {
      const rectBounds = this.activeRect.getBoundingClientRect();
      const windowBounds = document.documentElement.getBoundingClientRect();

      if (
        rectBounds.left + this.currentX > windowBounds.right ||
        rectBounds.right + this.currentX < windowBounds.left
      ) {
        this.activeRect.remove();
      } else {
        this.activeRect.style.transform = "";
      }

      this.startX = 0;
      this.currentX = 0;
      this.activeRect = null;

      window.removeEventListener("mousemove", this.handleMouseMove);
      window.removeEventListener("mouseup", this.handleMouseUp);

      console.log(this.$refs.frontContainer.hasChildNodes());
      if (this.$refs.frontContainer.hasChildNodes() == false) {
        this.$refs.mainContainer.remove();
      }
    },
    handleTouchStart(event) {
      this.startX = event.touches[0].clientX;
      this.activeRect = event.target;
      window.addEventListener("touchmove", this.handleTouchMove);
      window.addEventListener("touchend", this.handleTouchEnd);
      this.isActive = false;
    },
    handleTouchMove(event) {
      const diffX = event.touches[0].clientX - this.startX;
      this.currentX = diffX;

      this.activeRect.style.transform = `translateX(${this.currentX}px)`;
    },
    handleTouchEnd() {
      const rectBounds = this.activeRect.getBoundingClientRect();
      const windowBounds = document.documentElement.getBoundingClientRect();

      if (
        rectBounds.left + this.currentX > windowBounds.right ||
        rectBounds.right + this.currentX < windowBounds.left
      ) {
        this.activeRect.remove();
      } else {
        this.activeRect.style.transform = "";
      }

      this.startX = 0;
      this.currentX = 0;
      this.activeRect = null;

      window.removeEventListener("touchmove", this.handleTouchMove);
      window.removeEventListener("touchend", this.handleTouchEnd);

      console.log(this.$refs.frontContainer.hasChildNodes());
      if (this.$refs.frontContainer.hasChildNodes() == false) {
        this.$refs.mainContainer.remove();
      }
    },
  },
};
</script>

<style>
img {
  touch-action: none; /* to prevent scrolling on mobile */
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
.moveable-control-box {
  width: 100%;
  height: 100%;
}
.Group_10 {
  position: absolute;
  left: 0px;
  top: 0px;
  width: 100%;
  height: 100%;
  z-index: 19;
}
.Group_2 {
  position: absolute;
  left: 20%;
  top: 8%;
  z-index: 17;
  width: 60%;
}
.Group_5 {
  position: absolute;
  left: 15%;
  bottom: 10%;
  z-index: 18;
  width: 65%;
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
