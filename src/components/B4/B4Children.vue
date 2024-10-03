<template>
  <div></div>
</template>

<script setup>
import { onUpdated } from "vue";

const props = defineProps(["age"]);
onUpdated(() => {
  alert("Giá trị biến age đã thay đổi ");
});
</script>

<style></style>
