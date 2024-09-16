<script setup>
import ImageZoom from './components/ImageZoom.vue'
import PWABadge from './components/PWABadge.vue'
</script>

<template>
  Zoom in and out on the image below. You can also install this app on your device.
  <ImageZoom />
  <PWABadge />
</template>

<style>
html, body, #app {
  margin: 0;
  padding: 0;
  height: 100%;
  overflow: hidden;
}
</style>