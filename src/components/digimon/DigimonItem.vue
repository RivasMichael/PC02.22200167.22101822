<template>
  <div class="digimon-card">
    <img :src="digimon.img" :alt="digimon.name" class="digimon-img" />
    <div class="digimon-info">
      <h4 class="digimon-name">{{ digimon.name }}</h4>
      <div class="digimon-level">{{ digimon.level }}</div>
    </div>
  </div>
</template>

<script setup>
const { digimon } = defineProps({
  digimon: { type: Object, required: true },
})
</script>

<style scoped>
.digimon-card {
  border: 1px solid #e0e0e0;
  border-radius: 8px;
  overflow: hidden;
  display: flex;
  flex-direction: column;
  align-items: center;
  padding: 8px;
  background: #fff;
  width: 100%;
  max-width: 220px;
  margin: 0 auto;
}
.digimon-img {
  width: 100%;
  height: 140px;
  object-fit: contain;
  background: #fafafa;
}
.digimon-info {
  width: 100%;
  padding: 8px 4px;
  text-align: center;
}
.digimon-name {
  margin: 0;
  font-size: 16px;
}
.digimon-level {
  color: #666;
  font-size: 13px;
}
</style>
