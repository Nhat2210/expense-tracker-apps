<template>
    <div class="wrapper">
        <h2 class="mainTitle"><span class="gradientTitle">QUẢN LÝ CHI TIÊU</span></h2>
        <p class="content">Hãy chi tiêu một cách hợp lý</p>
    </div>
</template>

<script setup>

</script>

<style lang="scss" scoped>
    .wrapper{
        text-align: center;
        margin: 50px;
        .mainTitle{
            font-size: 36px;
            position: relative;
            .gradientTitle{
                background: linear-gradient(45deg, #227B94, #78B7D0);
                -webkit-background-clip: text;
                color: transparent;
            }
        }
        .mainTitle::before{
            content: "";
            width: 30%;
            height: 10px;
            background: #D4F6FF;
            position: absolute;
            top: 70%;
            z-index: -999;      
            right:35%;      
        }
        .content{
            padding-top: 10px;
            color: #6A9AB0;
        }
    }
</style>