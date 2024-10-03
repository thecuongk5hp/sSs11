<template>
  <div>
    <h1>Thời gian hiện tại: {{ time }}</h1>
  </div>
</template>

<script setup>
import { ref, onMounted, onUnmounted } from "vue";

const time = ref("");
let interval;

const updateTime = () => {
  const now = new Date();
  time.value = now.toLocaleTimeString();
};

onMounted(() => {
  updateTime();
  interval = setInterval(updateTime, 1000);
});

onUnmounted(() => {
  clearInterval(interval);
});
</script>

<style></style>
