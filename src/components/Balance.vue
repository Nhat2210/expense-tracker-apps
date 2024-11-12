<template>
    <h4 class="mainTitle">Số dư hiện tại của bạn</h4>
    <p class="totalMoney">&nbsp;&nbsp;&nbsp;${{ formatCurrency(total) }}</p>
</template>

<script setup>
import { defineProps } from 'vue';
import { formatCurrency } from '@/helpers/formatCurrency';
const props = defineProps({
    total: {
        type: Number,
        required: true,
    },
});
</script>

<style lang="css" scoped>
.mainTitle{
    color: #384B70;
    font-size: 20px;

}
.totalMoney{
    color: #1A1A1D;
    padding: 10px 0;
}
</style>