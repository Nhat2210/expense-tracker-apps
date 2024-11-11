<template>
    <h4 class="mainTitle">Số dư hiện tại của bạn</h4>
    <p class="totalMoney">${{ total }}</p>
</template>

<script setup>
import { defineProps } from 'vue';
const props = defineProps({
    total: {
        type: Number,
        required: true,
    },
});
</script>

<style lang="css" scoped>

</style>