<template>
    <div class="container">
        <h4>half双保险机制</h4>
        <div class="fl">
            <el-form ref="dataForm" label-width="100px">
                <el-form-item label="现价：" prop="num">
                    <el-input v-model="num"></el-input>
                </el-form-item>
                <el-form-item label="止损价：" prop="leave">
                    <el-input v-model="leave"></el-input>
                </el-form-item>
                <el-form-item label="">
                    <el-button type="primary" style="width:100%;margin-bottom:20px" @click="getResult">开始计算</el-button>
                </el-form-item>
                <el-form-item label="最大倍数">
                    <el-tag style="width:100%" type="success">{{res}}</el-tag>
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
            leave: '',
            res: ''
        }
    },
    methods: {
        getResult () {
            if (this.num > this.leave) {
                let absolute = this.num - this.leave
                this.res = this.num / absolute
                console.log('21')
            } else {
                console.log('111')
                let absolute = this.leave - this.num
                this.res = this.num / absolute
            }
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
