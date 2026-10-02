<script setup>
const info = {
  judul: "Info Praktikum",
  isi: "Isi file ini memakai class .kartu yang SAMA dengan KartuProfil.vue"
}
</script>

<template>
  <div class="kartu">
    <h3>{{ info.judul }}</h3>
    <p>{{ info.isi }}</p>
  </div>
</template>

<style scoped>
.kartu {
  border: 2px solid #35495e;
  border-radius: 8px;
  padding: 12px;
  margin-bottom: 10px;
}
</style>
