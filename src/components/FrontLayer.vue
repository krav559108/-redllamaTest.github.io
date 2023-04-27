<template>
  <div class="_01" ref="mainContainer">
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
      ref="frontContainer"
    >
      <Moveable
        class="moveableContainer"
        v-if="isSecond"
        ref="moveableRef"
        :target="'.target'"
        :draggable="true"
        :throttleDrag="throttleDrag"
        :edgeDraggable="edgeDraggable"
        :startDragRotate="startDragRotate"
        :throttleDragRotate="throttleDragRotate"
        @dragStart="onDragStart"
        @drag="onDrag"
        @dragEnd="onDragEnd"
      >
        <img class="Group_2 sticker85" src="../assets/Group-2.png" />
      </Moveable>
      <Moveable
        class="moveableContainer"
        v-if="isFifth"
        ref="moveableRef"
        :target="'.target'"
        :draggable="true"
        :throttleDrag="throttleDrag"
        :edgeDraggable="edgeDraggable"
        :startDragRotate="startDragRotate"
        :throttleDragRotate="throttleDragRotate"
        @dragStart="onDragStart"
        @drag="onDrag"
        @dragEnd="onDragEnd"
      >
        <img class="Group_5 sticker85" src="../assets/Group-5.png" />
      </Moveable>
      <Moveable
        class="moveableContainer"
        v-if="isNineth"
        ref="moveableRef"
        :target="'.target'"
        :draggable="true"
        :throttleDrag="throttleDrag"
        :edgeDraggable="edgeDraggable"
        :startDragRotate="startDragRotate"
        :throttleDragRotate="throttleDragRotate"
        @dragStart="onDragStart"
        @drag="onDrag"
        @dragEnd="onDragEnd"
      >
        <img
          class="Group_9 sticker70"
          v-show="isNineth"
          src="../assets/Group-9.png"
        />
      </Moveable>
      <Moveable
        class="moveableContainer"
        v-if="isThird"
        ref="moveableRef"
        :target="'.target'"
        :draggable="true"
        :throttleDrag="throttleDrag"
        :edgeDraggable="edgeDraggable"
        :startDragRotate="startDragRotate"
        :throttleDragRotate="throttleDragRotate"
        @dragStart="onDragStart"
        @drag="onDrag"
        @dragEnd="onDragEnd"
      >
        <img class="Group_3 sticker80" src="../assets/Group-3.png" />
      </Moveable>
      <Moveable
        class="moveableContainer"
        v-if="isFourth"
        ref="moveableRef"
        :target="'.target'"
        :draggable="true"
        :throttleDrag="throttleDrag"
        :edgeDraggable="edgeDraggable"
        :startDragRotate="startDragRotate"
        :throttleDragRotate="throttleDragRotate"
        @dragStart="onDragStart"
        @drag="onDrag"
        @dragEnd="onDragEnd"
      >
        <img class="Group_4 sticker60" src="../assets/Group-4.png" />
      </Moveable>
      <Moveable
        class="moveableContainer"
        v-if="isEighth"
        ref="moveableRef"
        :target="'.target'"
        :draggable="true"
        :throttleDrag="throttleDrag"
        :edgeDraggable="edgeDraggable"
        :startDragRotate="startDragRotate"
        :throttleDragRotate="throttleDragRotate"
        @dragStart="onDragStart"
        @drag="onDrag"
        @dragEnd="onDragEnd"
      >
        <img class="Group_8 sticker60" src="../assets/Group-8.png" />
      </Moveable>
      <Moveable
        class="moveableContainer"
        v-if="isSixth"
        ref="moveableRef"
        :target="'.target'"
        :draggable="true"
        :throttleDrag="throttleDrag"
        :edgeDraggable="edgeDraggable"
        :startDragRotate="startDragRotate"
        :throttleDragRotate="throttleDragRotate"
        @dragStart="onDragStart"
        @drag="onDrag"
        @dragEnd="onDragEnd"
      >
        <img class="Group_6 sticker65" src="../assets/Group-6.png" />
      </Moveable>
      <Moveable
        class="moveableContainer"
        v-if="isSeventh"
        ref="moveableRef"
        :target="'.target'"
        :draggable="true"
        :throttleDrag="throttleDrag"
        :edgeDraggable="edgeDraggable"
        :startDragRotate="startDragRotate"
        :throttleDragRotate="throttleDragRotate"
        @dragStart="onDragStart"
        @drag="onDrag"
        @dragEnd="onDragEnd"
      >
        <img class="Group_7 sticker80" src="../assets/Group-7.png" />
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
    const containerScale = 1;
    const throttleDrag = 1;
    const edgeDraggable = false;
    const startDragRotate = 0;
    const throttleDragRotate = 0;
    const xInputRef = null;
    const yInputRef = null;
    const moveableRef = null;
    const requestCallbacks = (() => {
      function request() {
        moveableRef.request(
          "draggable",
          {
            x: parseInt(xInputRef.value),
            y: parseInt(yInputRef.value),
          },
          true
        );
      }
      return {
        onInput(e) {
          const ev = e.nativeEvent || e;
          if (typeof ev.data === "undefined") {
            request();
          }
        },
        onKeyUp(e) {
          e.stopPropagation();
          if (e.keyCode === 13) {
            request();
          }
        },
      };
    })();

    return {
      // moveable: {
      //   draggable: true,
      //   throttleDrag: 0,
      // },
      isActive: true,

      isSecond: true,
      isThird: true,
      isFourth: true,
      isFifth: true,
      isSixth: true,
      isSeventh: true,
      isEighth: true,
      isNineth: true,

      xStart: 0,
      xEnd: 0,
      yStart: 0,
      yEnd: 0,

      containerScale,
      throttleDrag,
      edgeDraggable,
      startDragRotate,
      throttleDragRotate,
      moveableRef,
      requestCallbacks,
    };
  },

  methods: {
    clickedOutside() {
      this.isActive = false;
    },
    onDrag(e) {
      e.target.style.transform = e.transform;
      e.transform ? (this.isActive = false) : false;
    },
    onDragStart(e) {
      requestAnimationFrame(() => {
        this.xStart = e.clientX;
        this.yStart = e.clientY;
      });
    },
    onDragEnd(e) {
      requestAnimationFrame(() => {
        this.xEnd = e.clientX;
        this.yEnd = e.clientY;
        let rule1 = this.xEnd - this.xStart;
        let rule2 = this.yEnd - this.yStart;
        if (rule1 > 100 || rule1 < -100 || rule2 > 100 || rule2 < -100) {
          e.target.remove();
          console.log("deleted");
        }
        if (this.$refs.frontContainer.hasChildNodes() == false) {
          console.log("empty container");
          this.$refs.mainContainer.remove();
        }
      });
    },
  },
  computed: {},
  mounted() {
    this.moveableRef = this.$refs.moveableRef;
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
