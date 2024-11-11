<template>
    <div class="container">
        <div class="income">
            <h4>Thu nhập</h4>
            <p class="money plus" id="money plus">+${{ income }}</p>
        </div>
        <div class="expense">
            <h4>Chi tiêu</h4>
            <p id="money-minus" class="money minus">-${{ expenses }}</p>
        </div>
    </div>
</template>

<script setup>
import { defineProps } from 'vue';
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

<style lang="css" scoped>
.money{
    text-transform: uppercase;
}
.plus{
    color:green;
}
.minus{
    color: red;
}
</style>