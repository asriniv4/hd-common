<template>
  <div class="container">
    <div class="row justify-content-evenly">
      <div class="col-3">
        <RecentOrders />
      </div>
      <div class="col-5">
         <RecentCases />
      </div>
    </div>
  </div>
</template>

<script>
import RecentCases from './components/RecentCases.vue';
import RecentOrders from './components/RecentOrders.vue';

export default {
  name: 'App',
  components: {
    RecentCases,
    RecentOrders,
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
