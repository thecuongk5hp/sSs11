<template>
  <div>
    <h1>Ứng dụng đếm số</h1>
    <p>Count: {{ count }}</p>
  </div>
</template>

<script setup>
import { ref, onMounted, onUnmounted } from "vue";

const count = ref(0);
let interval;

onMounted(() => {
  interval = setInterval(() => {
    count.value++;
  }, 1000);
});

onUnmounted(() => {
  clearInterval(interval);
});
</script>

<style></style>
