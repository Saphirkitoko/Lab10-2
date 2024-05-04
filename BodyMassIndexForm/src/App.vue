<script setup>
import BodyMassIndexForm from './components/BodyMassIndexForm.vue'
import { ref } from 'vue'

// Reactive data for BMI
const bmi = ref(null)

// Function to calculate BMI when stats are entered
const calculateBMI = (stats) => {
  const { height, weight } = stats
  if (height && weight) {
    bmi.value = weight / (height * height)
  }
}
</script>

<template>
  <div class="blue-box">
    <h1 class="app-title">Body Mass Index Calculator</h1>
    <!-- Include BodyMassIndexForm component -->
    <BodyMassIndexForm @stats-entered="calculateBMI"></BodyMassIndexForm>
    <!-- Display calculated BMI -->
    <div v-if="bmi !== null" class="bmi-result">
      <h2>Your Body Mass Index (BMI) is: {{ bmi.toFixed(2) }}</h2>
    </div>
  </div>
</template>

<style scoped>
/* Scoped CSS for styling */
.blue-box {
  background-color: #cce5ff; /* Blue color */
  padding: 20px;
  border: 2px solid #007bff; /* Blue border */
  border-radius: 5px;
  text-align: center;
}
.app-title {
  margin-bottom: 20px;
}
.bmi-result {
  margin-top: 20px;
}
</style>

