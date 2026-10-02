<script setup>
import { ref } from 'vue'
const logo   = ref('/img/vue.png')
const site   = ref('https://vuejs.org')
const aktif  = ref(true)
const level  = ref('kartu-lulus')
</script>
 
<template>
  <img :src="logo" />
  <a :href="site">Vue Docs</a>
  <div :class="{ aktif, [level]: true }">Kartu</div>
  <button :disabled="!aktif">Simpan</button>
</template>