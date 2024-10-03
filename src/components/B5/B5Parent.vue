<template>
  <div>
    <button @click="handleShowToggle">Toggle</button>
    <B5Children v-if="isVisible" />
  </div>
</template>

<script setup>
import { ref } from "vue";
import B5Children from "./B5Children.vue";

const isVisible = ref(false);

const handleShowToggle = () => {
  isVisible.value = !isVisible.value;
};
</script>

<style></style>
