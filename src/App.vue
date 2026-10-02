<script setup>
import LogoKampus from '@/components/LogoKampus.vue'
import LogoKampusBesar from '@/components/LogoKampusBesar.vue'
import IdentitasKampus from '@/components/IdentitasKampus.vue'
import DaftarMahasiswa from '@/components/DaftarMahasiswa.vue'
</script>

<template>
  <main class="container">
    <h1>Halo, Vue!</h1>
    <p>Dibuat oleh: Aditiya Pratama</p>
    <p>Mata kuliah: Pemrograman Web 2</p>

    <LogoKampus />
    <LogoKampusBesar />
    <IdentitasKampus />
    <DaftarMahasiswa />
  </main>
</template>

<style scoped>
.container {
  max-width: 800px;
  margin: 0 auto;
  padding: 20px;
  font-family: Arial, sans-serif;
  color: #2c3e50;
}
</style>
