<template>
  <div>
    <h1>Current Company: {{ company }}</h1>
    <h1>Age: {{ age }}</h1>
    <button @click="handleRandom">Random</button>
  </div>
</template>

<script setup>
import { ref, onMounted, onBeforeUpdate } from "vue";

const companies = ["Rikkei Academy", "Rikkei Education", "Rikkei Fukuoka"];
const company = ref(companies[0]);
const age = ref(1);

const handleRandom = () => {
  age.value = Math.floor(Math.random() * 10) + 1;
};

onMounted(() => {
  updateCompany();
});

onBeforeUpdate(() => {
  updateCompany();
});

const updateCompany = () => {
  if (age.value >= 1 && age.value <= companies.length) {
    company.value = companies[age.value - 1];
  }
};
</script>

<style></style>
