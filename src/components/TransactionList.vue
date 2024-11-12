<template>
    <h3 class="mainTitle">Lịch sử chi tiêu</h3>
    <ul id="list" class="list">
        <li
        v-for="transaction in transactions"
        :key="transaction.id"
        :class="transaction.amount < 0 ? 'minus' : 'plus'
        ">
        {{ transaction.text }} 
        <span class="color">{{ formatCurrency(transaction.amount) }}$</span>
        <button class="delete btn" @click="deleteTransaction(transaction.id)">x</button>
        </li>
    </ul>
</template>

<script setup>
import { defineProps } from 'vue';
import { formatCurrency } from '@/helpers/formatCurrency';
const props = defineProps({
    transactions:{
        type: Array,
        required: true,
    },
});



const emit = defineEmits(['transactionDeleted']);

const deleteTransaction = (id) => {
    emit('transactionDeleted', id);
};


</script>

<style lang="css" scoped>
.mainTitle{
    color: #384B70;
}
.list{
    color: #384B70;
}
.list li{
    list-style-type: none;
    margin: 10px 0;
    font-size: 14px;
}
.minus .color{
    color: red;
    margin-left: 5px;
}
.plus .color{
    color: green;
    margin-left: 5px;
}
.delete{
    margin-left: 5px;
    width: 25px;
    height: 25px;
    border: none;
    border-radius: 2px;
    cursor: pointer;
}
.delete:hover{
    color: red;
    background-color: #FFF8DE;
}
</style>