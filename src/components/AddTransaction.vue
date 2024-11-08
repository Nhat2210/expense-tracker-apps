<template>
    <h3>Add new transaction</h3>
    <form action="form" @submit.prevent="onSubmit">
        <div class="form-control">
            <label for="text">Text</label>
            <input type="text" id="text" placeholder="Enter text">
        </div>
        <div class="form-control">
            <label for="amount">
                Amount <br/>
                (negative - expense, positive - income)
            </label>
            <input type="text" id="amount" placeholder="Enter amount..." v-model="amount">
        </div>
        <button class="btn-add">Add transaction</button>
    </form>
</template>

<script setup>

</script>

<style lang="css" scoped>

</style>