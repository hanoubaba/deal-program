<template>
    <div class="container">
        <div class="fl">
            <p>顺势而为</p>
            <p>过急必反</p>
            <el-form ref="dataForm" :model="dataForm" label-width="64px" @submit.native.prevent>
                <el-form-item label="现价：">
                    <el-input v-model="num" @keyup.enter.native="getResult"></el-input>
                </el-form-item>
                <el-form-item label="">
                    <el-button type="primary" style="width:100%;margin-bottom:0px" @click="getResult()">计算</el-button>
                </el-form-item>
                <el-form-item label="涨1%：">
                    <el-tag style="width:100%" type="success">{{up1}}</el-tag>
                </el-form-item>
                <el-form-item label="跌1%：">
                    <el-tag style="width:100%" type="danger">{{down1}}</el-tag>
                </el-form-item>
            </el-form>
        </div>
    </div>
</template>

<script>
export default {
    name: 'HelloWorld',
    data () {
        return {
            dataForm: {},
            num: '',
            up1: '',
            down1: '',
        }
    },
    methods: {
        demo () {
            console.log('demo')
        },
        getResult () {
            this.up1 = this.num * 1.01
            this.down1 = this.num * 0.99
        },
    }
}
</script>

<style scoped>
.container {
    color: #333;
    margin: 0 auto;
}
.fl {
    flex: 1;
}
p {
    color: #409eff;
    font-size: 14px;
}
</style>
