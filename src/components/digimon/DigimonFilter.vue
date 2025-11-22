<template>
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
.digimon-filter {
  display: flex;
  gap: 12px;
  align-items: center;
  margin-bottom: 12px;
}
.search-input {
  flex: 1;
  padding: 8px 10px;
  border-radius: 6px;
  border: 1px solid #ddd;
}
.level-select {
  padding: 8px 10px;
  border-radius: 6px;
  border: 1px solid #ddd;
}
</style>
