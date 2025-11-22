<template>
  <div class="page-digimons">
    <div class="page-container">
      <header class="page-header">
        <h1 class="page-title">Galería de Digimons</h1>
        <p class="page-subtitle">Explora y filtra Digimons por nombre o nivel</p>
      </header>

      <main>
        <DigimonList />
      </main>
    </div>
  </div>
</template>

<script setup>
import DigimonList from 'src/components/digimon/DigimonList.vue'
</script>

<style scoped>
.page-digimons {
  background: transparent;
  /* Aumentar espacio superior para evitar estar pegado al header de la app */
  padding: 90px 0 40px; /* ajusta este valor si tu header es más alto */
}
.page-container {
  max-width: 1200px;
  margin: 0 auto;
  padding: 12px 24px; /* espacio a los lados */
}
.page-header {
  text-align: center;
  margin: 10px 0 26px; /* espacio entre header y el contenido principal */
}
.page-title {
  margin: 0 0 8px;
  font-size: 34px;
  font-weight: 700;
  color: #222;
}
.page-subtitle {
  margin: 0;
  color: #666;
  font-size: 14px;
}
</style>
