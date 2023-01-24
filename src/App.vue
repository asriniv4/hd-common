<template>
  <RecentOrdersList></RecentOrdersList>
</template>

<script>
import { RecentOrdersList } from '@rad/hd-aurora';


export default {
  name: 'App',
  components: {
    RecentOrdersList,
  }
}
</script>

<style>
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}
</style>
