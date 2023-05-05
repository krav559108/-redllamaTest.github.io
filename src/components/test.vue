<template>
    <div class="rectangle"
         :style="{ transform: `translateX(${position}px)` }"
         @mousedown="handleMouseDown"
         @touchstart="handleTouchStart"
         @touchmove="handleTouchMove"
         @touchend="handleTouchEnd">
    </div>
  </template>
  
  <script>
  export default {
    data() {
      return {
        position: 0,
        startX: 0,
        currentX: 0,
        isDragging: false,
      };
    },
    methods: {
      handleMouseDown(event) {
        this.isDragging = true;
        this.startX = event.clientX;
      },
      handleMouseMove(event) {
        if (this.isDragging) {
          const diffX = event.clientX - this.startX;
          this.currentX = this.position + diffX;
          this.setPosition(this.currentX);
        }
      },
      handleMouseUp() {
        this.isDragging = false;
        this.position = this.currentX;
      },
      handleTouchStart(event) {
        const touch = event.touches[0];
        this.startX = touch.clientX;
      },
      handleTouchMove(event) {
        const touch = event.touches[0];
        const diffX = touch.clientX - this.startX;
        this.currentX = this.position + diffX;
        this.setPosition(this.currentX);
      },
      handleTouchEnd() {
        this.position = this.currentX;
      },
      setPosition(x) {
        const minX = -window.innerWidth / 2 + 50;
        const maxX = window.innerWidth / 2 - 50;
        if (x < minX) {
          x = minX;
        } else if (x > maxX) {
          x = maxX;
        }
        this.position = x;
      },
    },
    mounted() {
      document.addEventListener("mousemove", this.handleMouseMove);
      document.addEventListener("mouseup", this.handleMouseUp);
    },
    beforeUnmount() {
      document.removeEventListener("mousemove", this.handleMouseMove);
      document.removeEventListener("mouseup", this.handleMouseUp);
    },
  };
  </script>
  
  <style scoped>
  .rectangle {
    width: 100px;
    height: 100px;
    background-color: red;
    position: absolute;
    top: 50%;
    left: 50%;
    transform: translate(-50%, -50%);
    transition: transform 0.3s ease-out;
  }
  </style>
  