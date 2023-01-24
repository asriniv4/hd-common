<script setup>
defineProps({
  order: {
    type: Object,
    required: true,
  }
});
</script>

<template>
  <li>
    {{ order.requestor }} ordered a {{ order.model_type }} and it is {{ order.status }}.
  </li>
</template>

<style scoped>
</style>