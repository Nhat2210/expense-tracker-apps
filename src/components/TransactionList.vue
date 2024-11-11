<template>
    <h3 class="mainTitle">Lịch sử chi tiêu</h3>
    <ul id="list" class="list">
        <li
        v-for="transaction in transactions"
        :key="transaction.id"
        :class="transaction.amount < 0 ? 'minus' : 'plus'
        ">
        {{ transaction.text }} 
        <span>${{ transaction.amount }}</span>
        <button class="delete btn" @click="deleteTransaction(transaction.id)">x</button>
        </li>
    </ul>
</template>

<script setup>
import { defineProps } from 'vue';

const props = defineProps({
    transactions:{
        type: Array,
        required: true,
    }
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
    height: 100px;
}
.list li{
    list-style-type: none;
}
.minus{
    color: red;
}
.plus{
    color: green;
}
</style>