<script setup>
import kampus from '@/data/kampus.js'
</script>

<template>
  <div class="kampus">
    <h2>{{ kampus.nama }}</h2>
    <p>{{ kampus.fakultas }}</p>
    <p>{{ kampus.prodi }} — {{ kampus.kota }}</p>
  </div>
</template>

<style scoped>
.kampus {
  background-color: #f4f4f4;
  padding: 12px;
  border-radius: 8px;
  margin-bottom: 15px;
}
</style>
