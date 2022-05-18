<template>
    <div class="container">
        <h4>15分钟周期1分钟跟随测试</h4>
        <div class="fl">
            <el-form ref="dataForm" label-width="100px">
                <el-form-item label="现价：" prop="num">
                    <el-input v-model="num"></el-input>
                </el-form-item>
                <el-form-item label="">
                    <el-button type="primary" style="width:100%;margin-bottom:20px" @click="getResult">开始计算</el-button>
                </el-form-item>
                <el-form-item label="1%">
                    <el-tag style="width:100%" type="success">{{res1}}</el-tag>
                </el-form-item>
                <el-form-item label="2%">
                    <el-tag style="width:100%" type="success">{{res2}}</el-tag>
                </el-form-item>
                <el-form-item label="-1%">
                    <el-tag style="width:100%" type="">{{res3}}</el-tag>
                </el-form-item>
                <el-form-item label="-2%">
                    <el-tag style="width:100%" type="">{{res4}}</el-tag>
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
            res1: '',
            res2: '',
            res3: '',
            res4: '',
        }
    },
    methods: {
        getResult () {
            this.res1 = this.num * 1.01
            this.res2 = this.num * 1.02
            this.res3 = this.num * 0.99
            this.res4 = this.num * 0.98
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
