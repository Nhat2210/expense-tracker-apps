<template>
    <div class="container">
        <div class="income">
            <h4 class="personal_income">Thu nhập</h4>
            <p class="money plus" id="money plus">+${{ formatCurrency(income) }}</p>
        </div>
        <div class="expense">
            <h4 class="personal_expense">Chi tiêu</h4>
            <p id="money-minus" class="money minus">-${{ formatCurrency(expenses) }}</p>
        </div>
    </div>
</template>

<script setup>
import { defineProps } from 'vue';
import { formatCurrency } from '@/helpers/formatCurrency';
const props = defineProps({
    income:{
        type: Number,
        required: true,
    },
    expenses:{
        type:Number,
        required: true,
    }
});
</script>

<style lang="scss" scoped>
.container{
    display: flex;
    .income{
        margin-right: 50px;
    .personal_income{
        color: #384B70;
        font-size: 20px;
        }
    }
    .expense{
        .personal_expense{
            color: #384B70;
            font-size: 20px;
        }
    }
    .plus{
        color: green;
        padding: 5px 0;
    }
    .minus{
        color: red;
        padding: 5px 0;
    }
}

</style>