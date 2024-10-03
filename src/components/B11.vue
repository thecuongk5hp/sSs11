<template>
  <div class="traffic-light">
    <div class="light red" :class="{ active: currentLight === 'red' }">
      <span v-if="currentLight === 'red'">{{ countdown }}</span>
    </div>
    <div class="light green" :class="{ active: currentLight === 'green' }">
      <span v-if="currentLight === 'green'">{{ countdown }}</span>
    </div>
    <div class="light yellow" :class="{ active: currentLight === 'yellow' }">
      <span v-if="currentLight === 'yellow'">{{ countdown }}</span>
    </div>
  </div>
</template>

<script setup>
import { ref, onMounted, onBeforeUnmount } from "vue";
const currentLight = ref("red");
// Thời gian đếm ngược ban đầu cho đèn đỏ
const countdown = ref(40);
let intervalId = null;

const lightDurations = {
  red: 40,
  yellow: 3,
  green: 60,
};

const changeLight = () => {
  switch (currentLight.value) {
    case "red":
      currentLight.value = "green";
      countdown.value = lightDurations.green;
      break;
    case "green":
      currentLight.value = "yellow";
      countdown.value = lightDurations.yellow;
      break;
    case "yellow":
      currentLight.value = "red";
      countdown.value = lightDurations.red;
      break;
  }
};

// Function để bắt đầu quá trình đếm ngược và chuyển đèn
const startTrafficLight = () => {
  intervalId = setInterval(() => {
    countdown.value--;
    if (countdown.value <= 0) {
      changeLight();
    }
  }, 1000);
};

onMounted(() => {
  startTrafficLight();
});

onBeforeUnmount(() => {
  if (intervalId) {
    clearInterval(intervalId);
  }
});
</script>

<style>
.traffic-light {
  display: flex;
  gap: 10px;
  padding: 10px;
}

.light {
  width: 80px;
  height: 80px;
  border-radius: 50%;

  display: flex;
  justify-content: center;
  align-items: center;
  font-size: 20px;
  color: white;
  font-weight: bold;
}

.red {
  background-color: red;
}

.yellow {
  background-color: yellow;
}

.green {
  background-color: green;
}
</style>
