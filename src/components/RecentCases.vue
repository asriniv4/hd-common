<script setup>
import { onMounted, ref } from 'vue';
import axios from 'axios';

const loading = ref(true);
const cases = ref(null);

const GET_RECENT_CASES_URL = 'https://common.ismorebetter.com/.netlify/functions/get-recent-cases';

onMounted(() => {
  axios.get(GET_RECENT_CASES_URL)
    .then((response) => {
      console.log('recent cases ...')
      console.log(response)
      cases.value = response.data;
      loading.value = false;
    })
    .catch((error) => {
      loading.value = false;
      console.log(error);
    })
})
</script>

<template>
  Recent Cases
</template>

<style scoped>
</style>