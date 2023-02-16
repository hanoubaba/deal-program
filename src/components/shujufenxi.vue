<template>
    <div class="container">
        <div class="fl">
            <h2>数据分析</h2>
            <div class="main" id="main"></div>
        </div>
        <div class="fr">
            <h2>历史仓位</h2>
            <div class="scrollbox">
                <el-table :data="tableData" stripe style="width: 100%">
                    <!-- <el-table-column prop="cTime1" label="开仓时间">
                    </el-table-column>
                    <el-table-column prop="uTime1" label="平仓时间">
                    </el-table-column> -->
                    <el-table-column prop="openAvgPx" label="成本均价">
                    </el-table-column>
                    <el-table-column prop="closeAvgPx" label="平仓均价">
                    </el-table-column>
                    <el-table-column prop="closeTotalAmount1" label="最大持仓量">
                    </el-table-column>
                    <el-table-column prop="closeUpl" label="收益">
                        <template slot-scope="scope">
                            <p :class="[scope.row.closeUpl>0?'blue':'red']">{{ scope.row.closeUpl }}</p>
                        </template>
                    </el-table-column>

                </el-table>
            </div>
        </div>
    </div>
</template>

<script>
import aaaa from "./data/a.json"
import * as echarts from 'echarts';
export default {
    name: 'HelloWorld',
    data () {
        return {
            tableData: []
        }
    },
    mounted () {
        console.log(aaaa)
        this.tableData = aaaa
        this.tableData.forEach(el => {
            el.closeTotalAmount1 = el.closeTotalAmount / 10
            // el.cTime1 = this.toBirthDate(el.cTime)
        })

        var chartDom = document.getElementById('main');
        var myChart = echarts.init(chartDom);
        var option;
        option = {
            color: ['#05c28c', '#fc0048'],
            title: {
                // text: 'Referer of a Website',
                // subtext: 'Fake Data',
                // left: 'center'
            },
            tooltip: {
                trigger: 'item'
            },
            legend: {
                orient: 'vertical',
                // left: 'left'
            },
            series: [
                {
                    name: 'Access From',
                    type: 'pie',
                    radius: '50%',
                    data: [
                        { value: 1048, name: '收益单' },
                        { value: 300, name: '亏损单' }
                    ],
                    emphasis: {
                        itemStyle: {
                            shadowBlur: 10,
                            shadowOffsetX: 0,
                            shadowColor: 'rgba(0, 0, 0, 0.5)'
                        }
                    }
                }
            ]
        };
        option && myChart.setOption(option);

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
    height: 960px;
    display: flex;
    flex-direction: row;
    justify-content: center;
    align-items: center;
}
.fl {
    height: 100%;
    flex: 1;
    /* border: 1px solid red; */
}
.fr {
    height: 100%;
    flex: 2;
}
.main {
    height: 600px;
}
.scrollbox {
    overflow: scroll;
    /* border: 1px solid blue; */
    height: 900px;
}
h2 {
    margin: 10px;
}
.blue {
    color: #05c28c;
}
.red {
    color: #fc0048;
}
</style>
