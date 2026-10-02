<script setup>
import { ref } from 'vue'
const nama    = ref('')
const prodi   = ref('Informatika')
const mampir  = ref(false)   // checkbox
const beasiswa= ref('2 semester')      // radio
</script>
 
<template>
  <input v-model="nama" placeholder="Nama" />
  <select v-model="prodi">
    <option>Informatika</option>
    <option>Sistem Informasi</option>
  </select>
  <label><input type="checkbox" v-model="mampir" />Mampir</label>
  <input type="radio" value="A" v-model="beasiswa" /> A
  <input type="radio" value="B" v-model="beasiswa" /> B
 
  Preview: {{ nama }} - {{ prodi }} - {{ mampir }} - {{ beasiswa }}!
</template>