<template>
  <div class="container">
    <div class="row justify-content-evenly">
      <div class="col-3">
        <RecentOrders />
        <OrdersList />
      </div>
      <div class="col-5">
        <!-- <RecentCases /> -->
        hello
        <RecentCasesForClinician />
      </div>
    </div>
  </div>
</template>

<script>
//import RecentCases from './components/RecentCases.vue';
import RecentOrders from './components/RecentOrders.vue';
import RecentCasesForClinician from '@rad/hd-csats';
import OrdersList from '@rad/hd-aurora';

export default {
  name: 'App',
  components: {
    // RecentCases,
    RecentOrders,
    OrdersList,
    RecentCasesForClinician,
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
