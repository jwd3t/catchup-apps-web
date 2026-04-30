<script setup>
import axios from 'axios';
import {ref, onMounted} from "vue";

const universities = ref([]);
const loading = ref(false);
const error = ref(null);

onMounted(async () => {
  loading.value = true;
  try {
    const response = await axios.get(
        'http://universities.hipolabs.com/search?country=peru');
    universities.value = response.data;

  } catch (err) {
    error.value = "Error al cargar los datos"
    console.error(err);
  } finally {
    loading.value = false;
  }
})

</script>

<template>
  <div>
    <p v-if="loading">Cargando...</p>

    <p v-else-if="error">
      {{ error }}
    </p>

    <pv-card v-for="xd in universities": key="xd.name">
      <template #header>
        {{xd.name}}
      </template>
    </pv-card>
  </div>
</template>

<style scoped>

</style>