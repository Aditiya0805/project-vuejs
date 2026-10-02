<script setup>
import KartuProfil from '@/components/KartuProfil.vue'
import KartuBiodata from '@/components/KartuBiodata.vue'
import KotakInfo from '@/components/KotakInfo.vue'

const mahasiswa1 = {
  nama: "Aditiya Pratama",
  prodi: "Informatika",
  angkatan: 2024
}

const mahasiswa2 = {
  nama: "M Jidan Fadillah",
  prodi: "Informatika",
  angkatan: 2024
}
</script>

<template>
  <section class="daftar-mahasiswa">
    <h2>Daftar Mahasiswa</h2>

    <p>Mahasiswa 1 (Shorthand v-bind :mahasiswa)</p>
    <KartuProfil :mahasiswa="mahasiswa1" />

    <p>Mahasiswa 2 (Nama Panjang v-bind:mahasiswa)</p>
    <KartuProfil v-bind:mahasiswa="mahasiswa2" />

    <p>Biodata Mahasiswa 1</p>
    <KartuBiodata />

    <p>Biodata Mahasiswa 2</p>
    <KartuBiodata />

    <KotakInfo />
  </section>
</template>

<style scoped>
.daftar-mahasiswa {
  margin-top: 15px;
}
</style>
