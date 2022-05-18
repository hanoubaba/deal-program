<template>
    <div class="container">
        <h2>机会</h2>
        <div class="fl">
            <el-form ref="dataForm" label-width="100px">
                <el-form-item label="止损价：" prop="stopNum">
                    <el-input v-model="stopNum"></el-input>
                </el-form-item>
                <el-form-item label="现价：" prop="newNum">
                    <el-input v-model="newNum"></el-input>
                </el-form-item>
                <el-form-item label="">
                    <el-button type="primary" style="width:100%;margin-bottom:20px" @click="getResult">开始计算</el-button>
                </el-form-item>
                <el-form-item label="杠杆倍数：">
                    <el-tag style="width:100%" type="success">{{resLeverage}}</el-tag>
                </el-form-item>
            </el-form>
            <p>在认知的安全边际内操作</p>
            <p>以亏损50%的风险去博取等价或者更高的收益</p>
            <p>机会之前忍住 出现机会抓住</p>
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
