<template>
  <div class="container">
    <AppModule
      :header="header"
      :subheader="subheader"
      :module="module"
    />
    <AppSpinner
      :loading="loading"
    />
  </div>
</template>

<script setup>
import { ref, onMounted } from 'vue';
import axios from "axios";
import AppModule from "./components/AppModule.vue";
import AppSpinner from "./components/AppSpinner.vue";

const loading = ref(true);
const header = ref(null);
const subheader = ref(null);
const module = ref([]);

onMounted(() => {
  const url = './module.json';
  axios
      .get(url)
      .then(response => {
        header.value = response.data.header;
        subheader.value = response.data.subheader;
        module.value = response.data.module;
      })
      .catch(err => {
        console.error(err);

      })
      .finally(() => (loading.value = false));
})
</script>
