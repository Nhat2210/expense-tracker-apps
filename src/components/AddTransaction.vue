<template>
    <h3 class="mainTitle">Thêm khoản chi</h3>
    <form 
    id="form" 
    @submit.prevent="onSubmit
    ">
        <div 
        class="form-control">
            <label 
            for="text"
            class="subject"
            >Tên khoản chi</label><br>
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
            for="amount"
            class="money"
            >
                Chi phí 
            </label> <br>
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
.mainTitle{
    color: #384B70;
}
.subject{
    color: #384B70;
    display: inline-block;
    padding: 10px 0;
}
.money{
    color: #384B70;
    display: inline-block;
    padding: 10px 0;
}
input{
    border: none;
    padding: 8px 50px 8px 20px;
    background-color: #6A9AB0;
    color: #fff;
    border-radius: 5px;
}
input:focus{
    outline: none;
}
input::placeholder{
    color: #fff;
    opacity: 0.8;
}
button{
    padding: 10px 20px;
    margin-left: 20px;
    margin-top: 20px;
    border-radius: 5px;
    border: none;
    background: #EAD8B1;
    font-size: 12px;
    margin-bottom: 50px;
}
button:hover{
    background: #FFF8DE;
}
</style>