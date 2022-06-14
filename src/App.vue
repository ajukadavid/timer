<script setup lang="ts">
// This starter template is using Vue 3 <script setup> SFCs
// Check out https://vuejs.org/api/sfc-script-setup.html#script-setup

import Timer from '@/components/Timer.vue'
import { ref, onMounted, onUnmounted } from 'vue'

const newYears = "1 Jan 2023"
const remainingDays = ref("")
const remainingHours = ref("")
const remainingMinutes = ref("")
const remainingSeconds = ref("")


function countDown() {
const newYearsDate: Date = new Date(newYears)
const currentDate: Date = new Date()

const totalSeconds = (newYearsDate.getTime() -  currentDate.getTime()) / 1000

const days = Math.floor(totalSeconds / 3600 / 24)
const hours = Math.floor(totalSeconds / 3600 ) % 24
const mins = Math.floor(totalSeconds / 60) % 60
const seconds = Math.floor(totalSeconds) % 60

// remainingDays.value = days.toString()

console.log(days, hours, mins, seconds)

}

let timeInterval : ReturnType<typeof setInterval>

onMounted(() => {
 timeInterval = setInterval(countDown, 1000)
})

onUnmounted(() => {
  clearInterval(timeInterval)
})
</script>

<template>
  <div class="container">
<div class="title">
  New Year Count Down
  </div>
  <div class="timer">
    <Timer label="Days"/>
    <Timer label="Hours"/>
    <Timer label="Minutes"/>
    <Timer label="Seconds"/>
  </div>
</div>
</template>

<style>
@import url('https://fonts.googleapis.com/css2?family=Roboto+Slab&display=swap');
body {
  margin: 0;
  font-family: 'Merriweather', serif;
  font-family:'Roboto Slab', serif;
}
.container {
  height: 100vh;
  background-image: url("@/assets/bg-timer.jpg");
  background-repeat: no-repeat;
  background-size: cover;
  background-position: center center;
  text-align: center;
}
.title {
  font-size: 5rem;
  font-weight: bold;

}
.timer {
  display: flex;
  align-items: center;
  justify-content: space-around;
}
</style>
