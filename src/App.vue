<template>
  <Header/>
  <div class="container">
    <Balance/>
    <InComeExpense/>
    <TransactionList/>
    <AddTransaction/>
  </div>
</template>

<script setup>
import Header from './components/Header.vue';
import Balance from './components/Balance.vue';
import InComeExpense from './components/InComeExpense.vue';
import AddTransaction from './components/AddTransaction.vue';
import TransactionList from './components/TransactionList.vue';
</script>

<style lang="css" scoped>
.container{
  width: 500px;
  height: 400px;
  margin: 0 auto;
}
</style>