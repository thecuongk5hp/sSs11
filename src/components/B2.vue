<template>
  <div>
    <p>counter: {{ counter }}</p>
    <button @click="handleCounter">Counter</button>
  </div>
</template>

<script setup>
import { ref, onBeforeUpdate, onUpdated } from "vue";

const counter = ref(0);

onBeforeUpdate(() => {
  console.log("Before updated được gọi");
});

onUpdated(() => {
  console.log("Updated được gọi");
});

const handleCounter = () => {
  counter.value++;
};
</script>

<style></style>
