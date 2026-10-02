<script setup>
defineProps({
  mahasiswa: {
    type: Object,
    required: true
  }
})
</script>

<template>
  <div class="kartu">
    <h3>{{ mahasiswa.nama }}</h3>
    <p>{{ mahasiswa.prodi }}</p>
    <span>Angkatan {{ mahasiswa.angkatan }}</span>
  </div>
</template>

<style scoped>
.kartu {
  border: 2px solid #41B883;
  border-radius: 8px;
  padding: 12px;
  margin-bottom: 10px;
}
</style>
