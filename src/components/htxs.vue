<template>
    <div class="container">
        <h2>计算回调系数</h2>
        <div class="fl">
            <el-form ref="dataForm" label-width="100px">
                <el-form-item label="开始：" prop="num1">
                    <el-input v-model="num1"></el-input>
                </el-form-item>
                <el-form-item label="结束：" prop="num2">
                    <el-input v-model="num2"></el-input>
                </el-form-item>
                <el-form-item label="回调：" prop="num3">
                    <el-input v-model="num3"></el-input>
                </el-form-item>
                <el-form-item label="">
                    <el-button type="primary" style="width:100%;margin-bottom:20px" @click="getResult">开始计算</el-button>
                </el-form-item>
                <el-form-item label="系数：" prop="num3">
                    <el-input v-model="res"></el-input>
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
            num1: '',
            num2: '',
            num3: '',
            res: ''
        }
    },
    props: {
        msg: String
    },
    methods: {
        getResult () {
            if (!this.num1) {
                return
            }
            if (!this.res) {
                let gap1 = this.num2 - this.num1
                let gap2 = this.num2 - this.num3
                this.res = gap2 / gap1
            }
            if (!this.num3) {
                let gap1 = this.num2 - this.num1
                this.num3 = gap1 * this.res
            }
        }
    }
}
</script>

<style scoped>
.container {
    margin: 0 auto;
}
.fl {
    flex: 1;
}
</style>
