<template>
<div class="body">
  <Header/>
  <div class="main_container">
    <Balance :total="total" />
    <InComeExpense :income="+income" :expenses="-expenses"/>
    <TransactionList 
    :transactions="transactions"
    @transactionDeleted="handleTransactionDeleted"
    />
    <AddTransaction @transactionSubmitted="handleTransactionSubmitted"/>
  </div>
</div>

</template>

<script setup>
import Header from './components/Header.vue';
import Balance from './components/Balance.vue';
import InComeExpense from './components/InComeExpense.vue';
import AddTransaction from './components/AddTransaction.vue';
import TransactionList from './components/TransactionList.vue';

import { ref, computed, onMounted } from 'vue';
import { useToast } from 'vue-toastification';

const transactions = ref([]);
const toast = useToast();


const total = computed(() => {
  return transactions.value.reduce((acc, transactions) => {
    return acc + transactions.amount;
  }, 0);
});

const income = computed(() => {
  return transactions.value.filter((transactions) => {
    return transactions.amount > 0;
  }).reduce((acc, transactions) => {
    return acc + transactions.amount;
  }, 0).toFixed(2);
});

const expenses = computed(() => {
  return transactions.value.filter((transactions) => {
    return transactions.amount < 0;
  }).reduce((acc, transactions) => {
    return acc + transactions.amount;
  }, 0).toFixed(2);
});

const handleTransactionSubmitted = (transactionsData) => {
  transactions.value.push({
    id: generateUniqueId(),
    text: transactionsData.text,
    amount: transactionsData.amount,
  });
  toast.success('Thêm thành công!')
};

const handleTransactionDeleted = (id) => {
  transactions.value = transactions.value.filter((transaction) =>{
    return  transaction.id !== id;
  })
};

const generateUniqueId = () => {
  return Math.floor(Math.random() * 100000);
};

</script>

<style lang="scss" scoped>
.body{
  width: 500px;
  height: 100%;
  background: #C2FFC7;
  margin: 0 auto;
  padding-top: 10px;
  margin-top: 100px;
  margin-bottom: 100px;
  border-radius: 15px;
  box-shadow: rgba(0, 0, 0, 0.35) 0px 5px 15px;}
.main_container{
  padding: 0 90px 20px;
}
</style>