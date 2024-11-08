<template>
    <div class="inc-exp-container">
        <div class="income">
            <h4>Income</h4>
            <div id="money-plus" class="money plus">+$0.00</div>
        </div>
        <div class="expense">
            <h4>Expense</h4>
            <div id="money-minus" class="money minus">-$0.00</div>
        </div>
    </div>
</template>

<script setup>

</script>

<style lang="css" scoped>
.inc-exp-container{
    display: flex;
    justify-content: space-around;
}
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