<template>
    <div class="container">
        <h2>{{msg}}</h2>
        <el-form ref="dataForm" label-width="100px">
            <el-form-item label="起始价格：" prop="startNum">
                <el-input v-model="startNum"></el-input>
            </el-form-item>
            <el-form-item label="结束价格：" prop="endNum">
                <el-input v-model="endNum"></el-input>
            </el-form-item>
            <el-form-item label="波动率：">
                <el-tag style="width:100%">{{percent}}</el-tag>
            </el-form-item>
            <el-form-item label="">
                <el-button type="primary" style="width:100%;margin-bottom:20px" @click="getResult">开始计算</el-button>
            </el-form-item>
            <el-form-item label="反向波动率：">
                <el-tag style="width:100%">{{reversePer}}</el-tag>
            </el-form-item>
            <el-form-item label="平仓价格：">
                <el-tag style="width:100%" type="success">{{resPrice}}</el-tag>
            </el-form-item>
            <el-form-item label="杠杆倍数：">
                <el-tag style="width:100%" type="success">{{resLeverage}}</el-tag>
            </el-form-item>
        </el-form>
    </div>
</template>

<script>
export default {
    name: 'HelloWorld',
    data () {
        return {
            startNum: '',
            endNum: '',
            eatNum: 0.618,
            percent: '',
            reversePer: '',
            resPrice: '',
            resLeverage: '',
        }
    },
    props: {
        msg: String
    },

    methods: {
        getResult () {
            // 反向做空策略
            if (parseFloat(this.startNum) < parseFloat(this.endNum)) {
                // 差值
                let num1 = this.endNum - this.startNum
                // 波动率
                let num2 = '+' + (num1 / this.startNum * 100).toFixed(2) + "%"
                // 反向波动率
                let num3 = '-' + (num1 * this.eatNum / this.endNum * 100).toFixed(2) + "%"
                // 指导价格
                let num4 = (parseFloat(this.endNum) - parseFloat(num1 * this.eatNum)).toFixed(4)
                // 追求翻倍收益的杠杆倍数
                let num5 = 1 / (num1 * this.eatNum / this.endNum)
                this.percent = num2
                this.reversePer = num3
                this.resPrice = num4
                this.resLeverage = Math.ceil(num5)
                return
            }
            // 反向做多策略
            if (parseFloat(this.startNum) > parseFloat(this.endNum)) {
                // 差值
                let num1 = this.startNum - this.endNum
                // 波动率
                let num2 = '-' + (num1 / this.startNum * 100).toFixed(2) + "%"
                // 反向波动率
                let num3 = '+' + (num1 * this.eatNum / this.endNum * 100).toFixed(2) + "%"
                // 指导价格
                let num4 = (parseFloat(this.endNum) + parseFloat(num1 * this.eatNum)).toFixed(4)
                // 追求翻倍收益的杠杆倍数
                let num5 = 1 / (num1 * this.eatNum / this.endNum)
                this.percent = num2
                this.reversePer = num3
                this.resPrice = num4
                this.resLeverage = Math.ceil(num5)
                return
            }
        }
    }
}
</script>

<style scoped>
.container {
    margin: 0 auto;
    width: 50%;
}
</style>
