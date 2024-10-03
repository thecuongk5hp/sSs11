<template>
  <div>
    <button @click="handleIncrement">Increment</button>
    <p>{{ count }}</p>
  </div>
</template>

<script setup>
import { ref, onUpdated } from "vue";

const count = ref(0);
const handleIncrement = () => {
  count.value++;
};

onUpdated(() => {
  document.title = `Count: ${count.value}`;
});
</script>

<style></style>
