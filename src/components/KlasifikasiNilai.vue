<script setup>
import { ref } from 'vue'

// TODO: 1. Buat ref nilai, contoh 88
const nilai = ref(98)
</script>

<template>
  <div>
    <!-- TODO: 2. Gunakan v-if/v-else-if/v-else -->
    <p v-if="nilai >= 90 && nilai <= 100">Kategori: A (Sangat Baik)</p>
    <p v-else-if="nilai >= 80">Kategori: B (Baik)</p>
    <p v-else-if="nilai >= 70">Kategori: C (Cukup)</p>
    <p v-else-if="nilai >= 60">Kategori: D (Kurang)</p>
    <p v-else-if="nilai < 60 && nilai >= 0">Kategori: E (Tidak Lulus)</p>
    <p v-else>Nilai tidak valid</p>
  </div>
</template>