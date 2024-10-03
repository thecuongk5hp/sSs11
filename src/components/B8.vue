<template>
  <h4>Chiều rộng cửa sổ: {{ WidthWindow }}px</h4>
</template>

<script setup>
import { ref, onMounted, onUnmounted } from "vue";

const WidthWindow = ref(window.innerWidth);

const updateWidth = () => {
  WidthWindow.value = window.innerWidth;
};
onMounted(() => {
  window.addEventListener("resize", updateWidth);
});
</script>

<style></style>
