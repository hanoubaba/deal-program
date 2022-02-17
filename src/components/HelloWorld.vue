<template>
    <div class="container">
        <h2>{{msg}}</h2>
        <div class="fl">
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
                    <el-button type="primary" style="width:100%;margin-bottom:20px" @click="getResult1">开始计算</el-button>
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
        <!-- <div class="fl">
            <el-form ref="dataForm" label-width="100px">
                <el-form-item>
                    <h2>止盈止损</h2>
                </el-form-item>
                <el-form-item label="3连介入：" prop="endNum">
                    <el-input v-model="newNum"></el-input>
                </el-form-item>
                <el-form-item label="止盈点：">
                    <el-tag style="width:100%">{{stopProfitPrice}}</el-tag>
                </el-form-item>
                <el-form-item label="止损点：">
                    <el-tag style="width:100%">{{stopLoss}}</el-tag>
                </el-form-item>
                <el-form-item>
                    <el-button type="primary" style="width:100%;margin-bottom:20px" @click="getResult2">开始计算</el-button>
                </el-form-item>
                <el-form-item label="预计盈利：">
                    <el-tag style="width:100%" type="success">{{profitPer}}</el-tag>
                </el-form-item>
                <el-form-item label="预计亏损：">
                    <el-tag style="width:100%" type="success">{{lossPer}}</el-tag>
                </el-form-item>
                <el-form-item label="盈亏比：">
                    <el-tag style="width:100%" type="success">{{profitLoss}}</el-tag>
                </el-form-item>
            </el-form>
        </div> -->
    </div>
</template>

<script>
export default {
    name: 'HelloWorld',
    data () {
        return {
            // 1
            startNum: '',
            endNum: '',
            eatNum: 0.618,
            percent: '',
            reversePer: '',
            resPrice: '',
            resLeverage: '',
            // 2
            newNum: '',
            stopProfitPrice: '',
            stopLoss: '',
            profitPer: '',
            lossPer: '',
            profitLoss: '',
            u50: '',
            u100: ''
        }
    },
    props: {
        msg: String
    },
    methods: {
        getResult1 () {
            // 反向做空策略
            if (parseFloat(this.startNum) < parseFloat(this.endNum)) {
                // 差值
                let num1 = this.endNum - this.startNum
                // 波动率
                let num2 = '+' + (num1 / this.startNum * 100).toFixed(2) + "%"
                // 反向波动率
                let num3 = '-' + (num1 * this.eatNum / this.endNum * 100).toFixed(2) + "%"
                // 指导价格
                let len = 0
                if (this.startNum < 10000) {
                    len = 1
                }
                if (this.startNum < 1000) {
                    len = 2
                }
                if (this.startNum < 100) {
                    len = 3
                }
                if (this.startNum < 10) {
                    len = 4
                }
                let num4 = (parseFloat(this.endNum) - parseFloat(num1 * this.eatNum)).toFixed(len)
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
                let len = 0
                if (this.startNum < 10000) {
                    len = 1
                }
                if (this.startNum < 1000) {
                    len = 2
                }
                if (this.startNum < 100) {
                    len = 3
                }
                if (this.startNum < 10) {
                    len = 4
                }
                let num4 = (parseFloat(this.endNum) + parseFloat(num1 * this.eatNum)).toFixed(len)
                // 追求翻倍收益的杠杆倍数
                let num5 = 1 / (num1 * this.eatNum / this.endNum)
                this.percent = num2
                this.reversePer = num3
                this.resPrice = num4
                this.resLeverage = Math.ceil(num5)
                return
            }
        },
        getResult2 () {
            if (!this.startNum || !this.endNum || !this.newNum) {
                return
            }
            let newNum = parseFloat(this.newNum)
            // 反向做空策略
            if (parseFloat(this.startNum) < parseFloat(this.endNum)) {
                // 差值
                let num1 = this.endNum - this.startNum
                // 波动率
                let num2 = '+' + (num1 / this.startNum * 100).toFixed(2) + "%"
                // 反向波动率
                let num3 = '-' + (num1 * this.eatNum / this.endNum * 100).toFixed(2) + "%"
                // 指导价格
                let len = 0
                if (this.startNum < 10000) {
                    len = 1
                }
                if (this.startNum < 1000) {
                    len = 2
                }
                if (this.startNum < 100) {
                    len = 3
                }
                if (this.startNum < 10) {
                    len = 4
                }
                let num4 = (parseFloat(this.endNum) - parseFloat(num1 * this.eatNum)).toFixed(len)
                // 追求翻倍收益的杠杆倍数
                let num5 = 1 / (num1 * this.eatNum / this.endNum)
                this.percent = num2
                this.reversePer = num3
                this.resPrice = num4
                this.resLeverage = Math.ceil(num5)
                // 止盈价格
                this.stopProfitPrice = this.resPrice
                // 止损价格
                this.stopLoss = this.endNum
                // 预计盈利
                this.profitPer = ((newNum - this.stopProfitPrice) / newNum * 100 * this.resLeverage).toFixed(2) + "%"
                // 预计亏损
                this.lossPer = ((this.stopLoss - newNum) / newNum * 100 * this.resLeverage).toFixed(2) + "%"
                // 盈亏比
                this.profitLoss = ((newNum - this.stopProfitPrice) / (this.stopLoss - newNum) * 100).toFixed(2) + "%"
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
                let len = 0
                if (this.startNum < 10000) {
                    len = 1
                }
                if (this.startNum < 1000) {
                    len = 2
                }
                if (this.startNum < 100) {
                    len = 3
                }
                if (this.startNum < 10) {
                    len = 4
                }
                let num4 = (parseFloat(this.endNum) + parseFloat(num1 * this.eatNum)).toFixed(len)
                // 追求翻倍收益的杠杆倍数
                let num5 = 1 / (num1 * this.eatNum / this.endNum)
                this.percent = num2
                this.reversePer = num3
                this.resPrice = num4
                this.resLeverage = Math.ceil(num5)
                // 止盈价格
                this.stopProfitPrice = this.resPrice
                // 止损价格
                this.stopLoss = this.endNum
                // 预计盈利
                this.profitPer = ((this.stopProfitPrice - newNum) / newNum * 100 * this.resLeverage).toFixed(2) + "%"
                // 预计亏损
                this.lossPer = ((newNum - this.stopLoss) / newNum * 100 * this.resLeverage).toFixed(2) + "%"
                // 盈亏比
                this.profitLoss = ((newNum - this.stopProfitPrice) / (this.stopLoss - newNum) * 100).toFixed(2) + "%"
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
