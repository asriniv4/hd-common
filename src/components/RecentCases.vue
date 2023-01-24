<script setup>
import { onMounted, ref } from 'vue';
import axios from 'axios';
import CaseDetail from './CaseDetail.vue';

const loading = ref(true);
const recentCases = ref(null);

const GET_RECENT_CASES_URL = 'https://common.ismorebetter.com/.netlify/functions/get-recent-cases';

onMounted(() => {
  axios.get(GET_RECENT_CASES_URL)
    .then((response) => {
      console.log('recent cases ...')
      recentCases.value = response.data;
      loading.value = false;
    })
    .catch((error) => {
      loading.value = false;
      console.log(error);
    })
})
</script>

<template>
  <div v-if="loading" class="spinner-border text-info" role="status">
    <span class="visually-hidden">Loading...</span>
  </div>  
  <ul>
    <CaseDetail v-for="recentCase in recentCases" :key="recentCase.id" :recentCase="recentCase" />
  </ul>
</template>

<style scoped>
</style>