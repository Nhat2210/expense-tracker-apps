<template>
    <h4 class="mainTitle">Your Balance</h4>
    <p class="totalMoney">${{ total }}</p>
</template>

<script setup>
import { defineProps } from 'vue';
const props = defineProps({
    total: {
        type: Number,
        Required: true,
    },
});
</script>

<style lang="css" scoped>

</style>