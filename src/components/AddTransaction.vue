<template>
    <h3>Thêm khoản chi</h3>
    <form 
    id="form" 
    @submit.prevent="onSubmit
    ">
        <div 
        class="form-control">
            <label 
            for="text">Tên khoản chi</label>
            <input
            type="text" 
            id="text" 
            placeholder="Nhập tiêu đề ..."
            v-model="text"
            >
        </div>
        <div 
        class="form-control">
            <label 
            for="amount">
                Chi phí 
            </label>
            <input 
            type="text" 
            id="amount" 
            placeholder="Nhập chi phí..." 
            v-model="amount">
        </div>
        <button class="btn-add">Thêm khoản cần chi</button>
    </form>
</template>

<script setup>
import { useToast } from 'vue-toastification';
import { ref } from 'vue';
const text = ref('');
const amount = ref('');

const toast = useToast();

const emit =defineEmits(['transactionSubmitted']);

const onSubmit = () => {
    if(!text.value || !amount.value) {
        toast.error("Các trường không được để trống !");
        return;
    };
    const transactionData = {
        text: text.value,
        amount: parseFloat(amount.value),
    };
    emit('transactionSubmitted', transactionData);

    text.value = '';
    amount.value = '';
}
</script>

<style lang="css" scoped>

</style>