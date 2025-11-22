<template>
  <div class="digimon-list">
    <q-card v-for="digimon in digimons" :key="digimon.name" class="digimon-card">
      <q-img :src="digimon.img" :alt="digimon.name" class="digimon-img" />
      <q-card-section>
        <div class="digimon-name">{{ digimon.name }}</div>
        <div class="digimon-level">Nivel: {{ digimon.level }}</div>
      </q-card-section>
    </q-card>
  </div>
</template>

<script>
export default {
  name: 'DigimonList',
  data() {
    return {
      digimons: []
    }
  },
  async mounted() {
    const res = await fetch('https://digimon-api.vercel.app/api/digimon');
    const data = await res.json();
    this.digimons = data;
  }
}
</script>

<style scoped>
.digimon-list {
  display: flex;
  flex-wrap: wrap;
  gap: 24px;
  justify-content: center;
  margin-top: 32px;
}
.digimon-card {
  width: 220px;
  background: linear-gradient(135deg, #f7d358 0%, #f5a623 100%);
  border-radius: 16px;
  box-shadow: 0 4px 16px rgba(0,0,0,0.12);
  transition: transform 0.2s;
}
.digimon-card:hover {
  transform: scale(1.05);
  box-shadow: 0 8px 24px rgba(0,0,0,0.18);
}
.digimon-img {
  height: 160px;
  object-fit: contain;
  background: #fffbe6;
  border-radius: 16px 16px 0 0;
}
.digimon-name {
  font-size: 1.2rem;
  font-weight: bold;
  color: #e65100;
  text-align: center;
  margin-bottom: 8px;
}
.digimon-level {
  font-size: 1rem;
  color: #6d4c41;
  text-align: center;
}
</style>
