<template>
  <div class="container">
    <div
      class="rectangle"
      ref="rect1"
      @mousedown="handleMouseDown"
      @touchstart="handleTouchStart"
    ></div>
    <div
      class="rectangle"
      ref="rect2"
      @mousedown="handleMouseDown"
      @touchstart="handleTouchStart"
    ></div>
    <div
      class="rectangle"
      ref="rect3"
      @mousedown="handleMouseDown"
      @touchstart="handleTouchStart"
    ></div>
  </div>
</template>

<script>
export default {
  data() {
    return {
      startX: 0,
      currentX: 0,
      activeRect: null,
      isActive: true,
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
    },
    handleTouchStart(event) {
      this.startX = event.touches[0].clientX;
      this.activeRect = event.target;
      window.addEventListener("touchmove", this.handleTouchMove);
      window.addEventListener("touchend", this.handleTouchEnd);
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
    },
  },
};
</script>

<style>
.container {
  display: flex;
  flex-direction: column;
  justify-content: center;
  align-items: center;
  height: 100vh;
  width: 100vw;
}

.rectangle {
  width: 100px;
  height: 100px;
  background-color: red;
  margin: 10px;
  transition: transform 0.3s ease-out;
  touch-action: none; /* to prevent scrolling on mobile */
}
</style>
