<template>
  <div>
    <DigimonFilter :levels="levels" @filter="onFilter" />

    <div v-if="loading">Cargando Digimons...</div>
    <div v-else-if="error" class="error">Error: {{ error }}</div>

    <div class="grid" v-else>
      <div class="grid-item" v-for="d in filtered" :key="d.name">
        <DigimonItem :digimon="d" />
      </div>
    </div>
  </div>
</template>

<script setup>
import { ref, onMounted, computed } from 'vue'
import DigimonFilter from './DigimonFilter.vue'
import DigimonItem from './DigimonItem.vue'

const all = ref([])
const loading = ref(false)
const error = ref(null)
const nameFilter = ref('')
const levelFilter = ref('')

const levels = computed(() => {
  const set = new Set(all.value.map((d) => d.level).filter(Boolean))
  return Array.from(set).sort()
})

function onFilter({ name, level }) {
  nameFilter.value = name || ''
  levelFilter.value = level || ''
}

const filtered = computed(() => {
  return all.value.filter((d) => {
    const matchesName =
      !nameFilter.value || d.name.toLowerCase().includes(nameFilter.value.toLowerCase())
    const matchesLevel = !levelFilter.value || d.level === levelFilter.value
    return matchesName && matchesLevel
  })
})

onMounted(async () => {
  loading.value = true
  try {
    const res = await fetch('https://digimon-api.vercel.app/api/digimon')
    if (!res.ok) throw new Error(`HTTP ${res.status}`)
    const data = await res.json()
    all.value = data
  } catch (err) {
    error.value = err.message || String(err)
  } finally {
    loading.value = false
  }
})
</script>

<style scoped>
.grid {
  display: grid;
  grid-template-columns: repeat(auto-fill, minmax(180px, 1fr));
  gap: 12px;
}
.grid-item {
  display: block;
}
.error {
  color: red;
}
</style>
