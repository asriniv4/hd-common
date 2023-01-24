<script setup>
import { ref, onMounted } from 'vue';
import axios from 'axios';
import OrderDetail from './OrderDetail.vue';

const orders = ref(null);

const GET_RECENT_ORDERS_URL = 'https://common.ismorebetter.com/.netlify/functions/get-recent-orders';

onMounted(() => {
  axios.get(GET_RECENT_ORDERS_URL)
    .then((response) => {
      orders.value = response.data;
      console.log("the response:")
      console.log(response)
    })
    .catch((error) => {
      console.log(error)
    })
})
</script>

<template>
  <ul>
    <OrderDetail v-for="order in orders" :key="order.id" :order="order" />
  </ul>
</template>

<style scoped>
</style>