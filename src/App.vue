<script setup>
import LogoKampus from '@/components/LogoKampus.vue'
import LogoKampusBesar from '@/components/LogoKampusBesar.vue'
import IdentitasKampus from '@/components/IdentitasKampus.vue'
import DaftarMahasiswa from '@/components/DaftarMahasiswa.vue'
import Interpolasi from '@/components/Interpolasi.vue' 
import Vbin from '@/components/Vbin.vue'
import Vmodel from '@/components/Vmodel.vue'
import KlasifikasiNilai from '@/components/KlasifikasiNilai.vue'
import EksperimenToggle from '@/components/EksperimenToggle.vue'
</script>

<template>
  <main class="container">
    <h1>Halo, Vue!</h1>
    <p>Dibuat oleh: Aditiya Pratama</p>
    <p>Mata kuliah: Pemrograman Web 2</p>
    <p>Kelas: 24A-Informatika</p>
    <p>Npm: 24312126</p>

    <LogoKampus />
    <LogoKampusBesar />
    <IdentitasKampus />
    <DaftarMahasiswa />
    <Interpolasi />
    <Vbin />
    <Vmodel />
    <KlasifikasiNilai />  
    <EksperimenToggle />
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
