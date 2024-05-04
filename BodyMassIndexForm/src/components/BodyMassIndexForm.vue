<script setup>
import { ref } from 'vue'

// Reactive data for height, weight, and BMI result
const height = ref(null)
const weight = ref(null)
const bmiResult = ref(null)

// Function to emit event with user's height and weight
const calculateBMI = () => {
  if (height.value && weight.value) {
    const bmi = weight.value / (height.value * height.value)
    bmiResult.value = bmi.toFixed(2)
    emit('stats-entered', { height: height.value, weight: weight.value })
  }
}
</script>

<template>
  <div class="red-box">
    <!-- Message to enter height and weight -->
    <p>Enter your height and weight</p>

    <!-- Inputs for height and weight -->
    <div class="input-container">
      <label for="height">Height (meters):</label>
      <input type="number" id="height" v-model="height">
    </div>
    <div class="input-container">
      <label for="weight">Weight (kilograms):</label>
      <input type="number" id="weight" v-model="weight">
    </div>
    <!-- Button to calculate BMI -->
    <button @click="calculateBMI">Calculate</button>

    <!-- Display BMI result -->
    <div v-if="bmiResult !== null">
      <p>BMI is: {{ bmiResult }}</p>
    </div>
  </div>
</template>

<style scoped>
/* Scoped CSS for styling */
.red-box {
  background-color: #ffcccc; /* Red color */
  padding: 20px;
  border: 2px solid #ff0000; /* Red border */
  border-radius: 5px;
  text-align: center;
}
.input-container {
  margin-bottom: 20px;
}
input[type="number"] {
  width: 100px;
  padding: 5px;
  border: 1px solid #ccc;
  border-radius: 5px;
}
button {
  padding: 10px 20px;
  background-color: #007bff;
  color: #fff;
  border: none;
  border-radius: 5px;
  cursor: pointer;
}
button:hover {
  background-color: #0056b3;
}
</style>



