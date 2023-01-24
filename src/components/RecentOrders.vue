<script setup>
import { ref, onMounted } from 'vue';
import axios from 'axios';
import OrderDetail from './OrderDetail.vue';

const loading = ref(true);
const orders = ref(null);

const GET_RECENT_ORDERS_URL = 'https://common.ismorebetter.com/.netlify/functions/get-recent-orders';

onMounted(() => {
  axios.get(GET_RECENT_ORDERS_URL)
    .then((response) => {
      orders.value = response.data;
      loading.value = false;
    })
    .catch((error) => {
      loading.value = false;
      console.log(error)
    })
})
</script>

<template>
  <div v-if="loading" class="spinner-border text-info" role="status">
    <span class="visually-hidden">Loading...</span>
  </div>  
  <ul>
    <OrderDetail v-for="order in orders" :key="order.id" :order="order" />
  </ul>
</template>

<style scoped>
</style>