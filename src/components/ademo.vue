<template>
    <div class="container">
        <img src="../assets/hs.png" alt="">
        <div class="time">
            <div class="text">

            </div>
        </div>
    </div>
</template>

<script>
export default {
    name: 'HelloWorld',
    data () {
        return {
            stopNum: '',
            newNum: '',
            resLeverage: '',
        }
    },
    methods: {
        getResult () {

        },
    }
}
</script>

<style scoped>
.container {
    position: relative;
}
.time {
    border: 1px solid red;
    position: absolute;
    left: 0;
    top: 760px;
    width: 1080px;
    height: 200px;
    display: flex;
    justify-content: center;
    align-items: center;
}
.text {
    border: 1px solid blue;
    width: 760px;
    height: 200px;
    /* background-color: #fff; */
}
</style>
