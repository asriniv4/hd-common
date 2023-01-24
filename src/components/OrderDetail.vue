<script setup>
  defineProps({
    order: {
      type: Object,
      required: true,
    }
  })
</script>

<template>
  <li><strong>{{ order.requestor }}</strong> ordered a <code>{{ order.model_type }} Model</code> and it is <em>{{ order.status }}</em></li>
</template>

<style scoped>
</style>