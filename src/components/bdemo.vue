<template>
    <div class="all">
        <div class="before" v-if="flag">
            <p v-for="(name,i) in nameLs" :key="'name'+i" class="history" @click="clickHis(name)">{{name}}</p>
            <el-input style="width:300px;margin-bottom:20px" v-model="name" placeholder="请输入小区" clearable></el-input>
            <el-button type="primary" @click="showInfo">点击确认</el-button>
        </div>
        <div class="container" v-else>
            <div class="box">
                <p class="name">{{name}}</p>
            </div>
            <div class="box1">
                <p class="date">{{date}}</p>
            </div>
            <div class="box2">
                <h1 class="time">{{time}}</h1>
            </div>
        </div>
    </div>
</template>

<script>
export default {
    name: 'HelloWorld',
    data () {
        return {
            name: "牛寨3号院",
            date: '',
            time: '',
            flag: true,
            nameLs: [
                '牛寨3号院',
                '万科城小世界',
                '牛寨3号院',
            ]
        }
    },
    mounted () {
        this.run()
    },
    methods: {
        clickHis (name) {
            this.name = name
            this.flag = false
        },
        showInfo () {
            this.flag = false
        },
        run () {
            var time = new Date();//获取系统当前时间
            var year = time.getFullYear();
            var month = time.getMonth() + 1;
            var date = time.getDate();//系统时间月份中的日
            // var day = time.getDay();//系统时间中的星期值
            // var weeks = ["星期日", "星期一", "星期二", "星期三", "星期四", "星期五", "星期六"];
            // var week = weeks[day];//显示为星期几
            var hour = time.getHours();
            var minutes = time.getMinutes();
            var seconds = time.getSeconds();
            // console.log(seconds);
            if (month < 10) {
                month = "0" + month;
            }
            if (date < 10) {
                date = "0" + date;
            }
            if (hour < 10) {
                hour = "0" + hour;
            }
            if (minutes < 10) {
                minutes = "0" + minutes;
            }
            if (seconds < 10) {
                seconds = "0" + seconds;
            }
            //var newDate = year+"年"+month+"月"+date+"日"+week+hour+":"+minutes+":"+seconds;
            // document.getElementById("show").innerHTML = year + "年" + month + "月" + date + "日" + week + hour + ":" + minutes + ":" + seconds;
            this.date = year + "年" + month + "月" + date + "日"
            this.time = hour + ":" + minutes + ":" + seconds;
            setTimeout(() => {
                this.run()
            }, 1000);
        },
    }
}
</script>

<style scoped>
.all {
    margin: -8px;
    padding: 0;
}
.container {
    margin: 0;
    padding: 0;
    position: relative;
    margin: 0 auto;
    max-width: 750px;
    height: 800px;
    /* border: 1px solid red; */
    background: url('../assets/hs.png') no-repeat center/100%;
}
.box {
    /* border: 1px solid red; */
    position: absolute;
    left: 0;
    top: 132px;
    width: 100%;
    /* height: 100px; */
    display: flex;
    flex-direction: column;
    justify-content: center;
    align-items: center;
}
.name {
    width: 80%;
    /* height: 100px; */
    padding: 0;
    margin: 0;
    font-size: 24px;
    letter-spacing: 2px;
    font-weight: bold;
    color: #fff;
    background-color: rgba(23, 173, 38, 0.2);
}
.box1 {
    /* border: 1px solid red; */
    position: absolute;
    left: 0;
    top: 224px;
    width: 100%;
    /* height: 100px; */
    display: flex;
    flex-direction: column;
    justify-content: center;
    align-items: center;
}
.date {
    /* border: 1px solid blue; */
    width: 80%;
    /* height: 100px; */
    padding: 0;
    margin: 0;
    font-size: 20px;
    letter-spacing: 2px;
    font-weight: bold;
    color: #999;
    background-color: #fff;
}
.box2 {
    /* border: 1px solid red; */
    position: absolute;
    left: 0;
    top: 240px;
    width: 100%;
    height: 100px;
    display: flex;
    flex-direction: column;
    justify-content: center;
    align-items: center;
}
.time {
    /* border: 1px solid blue; */
    width: 80%;
    height: 80px;
    font-size: 48px;
    color: #000;
    font-weight: bolder;
    background-color: #fff;
    letter-spacing: 5px;
}
.before {
    width: 100%;
    height: 800px;
    /* border: 1px solid red; */
    display: flex;
    flex-direction: column;
    justify-content: center;
    align-items: center;
}
.history {
    text-decoration: underline;
    color: blue;
    cursor: pointer;
}
</style>
