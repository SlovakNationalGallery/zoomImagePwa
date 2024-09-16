<template>
  <div class="image-container" @touchstart="onTouchStart" @touchmove="onTouchMove" @touchend="onTouchEnd">
    <img
      src="../assets/beef.jpg"
      ref="image"
      :style="{ transform: `scale(${scale}) translate(${translateX}px, ${translateY}px)` }"
      class="zoomable-image"
      alt="Zoomable"
    />
  </div>
</template>

<script setup>
import { ref } from 'vue';

// Image source (You can replace this with the actual image URL)
// const imageSrc = '/assets/beef.jpg';

// Pinch-to-zoom variables
const scale = ref(1);
const lastScale = ref(1);
const translateX = ref(0);
const translateY = ref(0);
const lastTranslateX = ref(0);
const lastTranslateY = ref(0);
const startX = ref(0);
const startY = ref(0);
const initialPinchDistance = ref(null);

// Helper function to calculate distance between two touch points
const getDistance = (touches) => {
  const [touch1, touch2] = touches;
  return Math.sqrt(
    (touch1.pageX - touch2.pageX) ** 2 +
    (touch1.pageY - touch2.pageY) ** 2
  );
};

// Handle touch start
const onTouchStart = (e) => {
  if (e.touches.length === 2) {
    initialPinchDistance.value = getDistance(e.touches);
    lastScale.value = scale.value;
  } else if (e.touches.length === 1) {
    startX.value = e.touches[0].pageX - lastTranslateX.value;
    startY.value = e.touches[0].pageY - lastTranslateY.value;
  }
};

// Handle touch move
const onTouchMove = (e) => {
  if (e.touches.length === 2) {
    const currentDistance = getDistance(e.touches);
    scale.value = lastScale.value * (currentDistance / initialPinchDistance.value);
  } else if (e.touches.length === 1) {
    translateX.value = e.touches[0].pageX - startX.value;
    translateY.value = e.touches[0].pageY - startY.value;
  }
};

// Handle touch end
const onTouchEnd = () => {
  lastTranslateX.value = translateX.value;
  lastTranslateY.value = translateY.value;
};
</script>

<style scoped>
.image-container {
  overflow: hidden;
  touch-action: none;
  width: 100%;
  height: 100vh;
  display: flex;
  justify-content: center;
  align-items: center;
  background-color: #000;
}

.zoomable-image {
  max-width: 100%;
  max-height: 100%;
  transition: transform 0.1s;
}
</style>
