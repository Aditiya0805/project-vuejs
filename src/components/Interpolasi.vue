<script setup>
import { ref } from 'vue'
const name   = ref('Adit')
const score  = ref(88)
const passed = ref(true)
const title  = ref('Web Programming 2')
</script>
 
<template>
  <h1>Hello {{ name }}!</h1>
  <p>Course: {{ title.toUpperCase() }}</p>
  <p>Score +5 = {{ score + 5 }}</p>
  <p>Status: {{ passed ? 'PASS' : 'RETRY' }}</p>
 
  <!-- mustache in attributes: WRONG -->
  <!-- <img src="{{ url }}" /> -->
</template>