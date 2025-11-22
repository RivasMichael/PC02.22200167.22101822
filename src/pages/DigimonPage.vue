<template>
  <div class="page-digimons q-pa-md">
    <h3>Lista de Digimons</h3>
    <DigimonList />
  </div>
</template>

<script setup>
import DigimonList from 'src/components/digimon/DigimonList.vue'
</script>

<style scoped>
.page-digimons {
  max-width: 1100px;
  margin: 0 auto;
}
</style>
