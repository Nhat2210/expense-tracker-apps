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
        <div class="button"><button class="btn-add">Thêm chi tiêu</button></div>
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
    width: 100%;
    border: none;
    padding: 8px 50px 8px 20px;
    background-color: #6A9AB0;
    color: #fff;
    border-radius: 5px;
}
input:focus{
    outline: none;
    background-color: #6A9AB0;
}
input::placeholder{
    color: #fff;
    opacity: 0.8;
}
input:last-child{
    position: relative;
}
input:last-child::before{
    content: "VND";
    position: absolute;
    color: red;
    right: 10px;
    top: 50%;
    transform: translateY(-50%);
    z-index: 999;
}
.btn-add{
    padding: 10px 20px;
    margin-left: 20px;
    margin-top: 20px;
    border-radius: 5px;
    border: none;
    background: #EAD8B1;
    font-size: 14px;
    margin-bottom: 50px;
}
.btn-add:hover{
    background: #FFF8DE;
}
.button{
    display: flex;
    justify-content: center;
    align-items: center;
}
</style>