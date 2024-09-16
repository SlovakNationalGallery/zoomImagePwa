<script setup>
import { ref, onMounted } from "vue";
import PWABadge from "./components/PWABadge.vue";
import { Zoompinch } from "zoompinch";
import "zoompinch/style.css";
const transform = ref({ x: 0, y: 0, scale: 1, rotate: 0 });

function fit(animate) {
  transform.value = { x: 0, y: 0, scale: 1, rotate: 0 };
}
onMounted(() => {
  setTimeout(() => fit(true));
});
</script>

<template>
  <zoompinch
    v-model:transform="transform"
    :width="8975"
    :height="13676"
    :min-scale="1"
    :max-scale="15"
    :rotation="false"
    :bounds="true"
    mouse
    touch
    wheel
    gesture
  >
    <template #canvas>
      <img src="./assets/beef.jpg" style="width: 8975px; height: 13676px" />
    </template>
  </zoompinch>

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
}
.zoompinch {
  background-color: #e8e2d2;
}
</style>
