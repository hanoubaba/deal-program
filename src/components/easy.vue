<template>
    <div class="container">
        <div class="fl">
            <el-form ref="dataForm" label-width="100px">
                <el-form-item label="现价：" prop="num">
                    <el-input v-model="num"></el-input>
                </el-form-item>
                <el-form-item label="">
                    <el-button type="primary" style="width:100%;margin-bottom:20px" @click="getResult">开始计算</el-button>
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
            num: '',
            up1: '',
            down1: '',
        }
    },
    methods: {
        getResult () {
            this.up1 = (this.num * 1.01).toFixed(2)
            this.down1 = (this.num * 0.99).toFixed(2)
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
    color: #fc0048;
    font-size: 14px;
}
</style>
