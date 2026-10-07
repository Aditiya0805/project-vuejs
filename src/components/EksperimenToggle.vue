<script setup>

import { ref } from 'vue'

const tampilIf = ref(true)

const tampilShow = ref(true)

</script>

<template>

  <!-- TODO: 1. Tambahkan tombol untuk toggle tampilIf -->
  <button @click="tampilIf = !tampilIf">Toggle v-if</button>
  <button @click="tampilIf = !tampilIf">Toggle v-if</button>

  <!-- TODO: 2. Tambahkan tombol untuk toggle tampilShow -->
  <button @click="tampilShow = !tampilShow">Toggle v-show</button>

  <p v-if="tampilIf">Elemen ini pakai v-if</p>

  <p v-show="tampilShow">Elemen ini pakai v-show</p>

</template>