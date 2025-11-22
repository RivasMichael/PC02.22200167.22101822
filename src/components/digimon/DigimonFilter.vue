<template>
  <div class="digimon-filter-wrap">
    <div class="digimon-filter">
      <input
        v-model="name"
        @input="emitFilter"
        placeholder="Buscar por nombre"
        class="search-input"
      />

      <select v-model="level" @change="emitFilter" class="level-select">
        <option value="">Todos los niveles</option>
        <option v-for="lvl in levels" :key="lvl" :value="lvl">{{ lvl }}</option>
      </select>
    </div>
  </div>
</template>

<script setup>
import { ref } from 'vue'

const emit = defineEmits(['filter'])
const { levels } = defineProps({
  levels: { type: Array, default: () => [] },
})

const name = ref('')
const level = ref('')

function emitFilter() {
  emit('filter', { name: name.value, level: level.value })
}
</script>

<style scoped>
.digimon-filter-wrap {
  display: flex;
  justify-content: center;
  margin-bottom: 18px;
}
.digimon-filter {
  display: flex;
  gap: 12px;
  align-items: center;
  width: 100%;
  max-width: 820px; /* control width of the filter block */
}
.search-input {
  flex: 1 1 60%;
  max-width: 640px;
  padding: 10px 14px;
  border-radius: 8px;
  border: 1px solid #e0e0e0;
  box-shadow: 0 1px 2px rgba(0, 0, 0, 0.03);
}
.level-select {
  flex: 0 0 160px;
  padding: 8px 10px;
  border-radius: 8px;
  border: 1px solid #e0e0e0;
  background: white;
}

@media (max-width: 720px) {
  .digimon-filter {
    flex-direction: column;
    gap: 8px;
  }
  .level-select {
    width: 100%;
  }
  .search-input {
    max-width: 100%;
  }
}
</style>
