<script setup>
import { ref, onMounted, onBeforeUnmount } from "vue";
import PWABadge from "./components/PWABadge.vue";
import OpenSeaDragon from "openseadragon";
const viewer = ref(null);

onMounted(() => {
  viewer.value = OpenSeaDragon({
    id: "viewer",
    tileSources: "https://img.webumenia.sk/zoom/?path=%2FSNGBA3%2FX13300%2FSNG--G_13269--1_1--_2015_08_13_--L2_WEB.jp2.dzi",
    showNavigationControl: false,
    showNavigator: false,
    visibilityRatio: 1,
    // constrainDuringPan: true,
    defaultZoomLevel: 1,
    minZoomLevel: 1,
  });
});

onBeforeUnmount(() => {
  if (viewer.value) {
    viewer.value.destroy();
  }
});
</script>

<template>
  <div id="viewer"></div>
  <PWABadge />
</template>

<style>
html,
body,
#app {
  margin: 0;
  padding: 0;
  height: 100%;
  width: 100%;
  overflow: hidden;
  background-color: #e8e2d2;
}
#viewer {
  width: 100%;
  height: 100%;
  position: absolute;
  top: 0;
  left: 0;
  bottom: 0;
  right: 0;
  overflow: hidden;
}
</style>
