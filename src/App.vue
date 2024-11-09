<template>
  <Header/>
  <div class="container">
    <Balance :total="total" />
    <InComeExpense :income="+income" :expenses="-expenses"/>
    <TransactionList 
    :transactions="transactions"
    />
    <AddTransaction/>
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

onMounted(()=> {
  const savedTransactions = JSON.parse(localStorage.getItem('transactions'));
  if(savedTransactions){
    transactions.value = savedTransactions;
  }
});

const total = computed(() => {
  return transactions.value.reduce((acc, transactions) => {
    return acc + transactions.amount;
  }, 0);
});

const income = computed(() => {
  return transactions.value.filter((transactions) => {
    transactions.amount > 0;
  }).reduce((acc, transactions) => {
    acc + transactions.amount;
  }, 0).toFixed(2);
});

const expenses = computed(() => {
  return transactions.value.filter((transactions) => {
    transactions.amount > 0;
  }).reduce((acc, transactions) => {
    acc + transactions.amount;
  }, 0).toFixed(2);
});

const handleTransactionSubmitted = (transactionsData) => {
  transactions.value.push({
    id: generateUniqueId(),
    text: transactionsData.text,
    amount: transactionsData.amount,
  });
  savedTransactionsToLocalStorage();
  toast.success('Thêm thành công!')
};

const savedTransactionsToLocalStorage = () => {
  localStorage.setItem('transactions', JSON.stringify(transactions.value))
};

const generateUniqueId = () => {
  return Math.floor(Math.random() * 100000);
};

</script>

<style lang="css" scoped>
.container{
  width: 500px;
  height: 400px;
  margin: 0 auto;
}
</style>