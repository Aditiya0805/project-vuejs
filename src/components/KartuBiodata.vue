<script setup>
const mhs = {
  nama: "Ahmad Fauzi",
  nim: "221051122",
  prodi: "Informatika",
  angkatan: 2024,
  ipk: 3.72
}
</script>

<template>
  <div class="biodata">
    <h3>{{ mhs.nama }}</h3>
    <p><strong>NIM:</strong> {{ mhs.nim }}</p>
    <p><strong>Program Studi:</strong> {{ mhs.prodi }}</p>
    <p><strong>Angkatan:</strong> {{ mhs.angkatan }}</p>
    <p><strong>IPK:</strong> {{ mhs.ipk }}</p>
  </div>
</template>

<style scoped>
.biodata {
  border: 1px solid #999;
  border-radius: 8px;
  padding: 12px;
  margin-bottom: 10px;
}
</style>
