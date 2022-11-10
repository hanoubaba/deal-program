<template>
    <div class="container">
        <img src="../assets/hs.png" alt="">
        <div class="data">
            <!-- <p class="date">{{date}}</p> -->
            <h1 class="time">{{time}}</h1>
        </div>
    </div>
</template>

<script>
export default {
    name: 'HelloWorld',
    data () {
        return {
            date: '',
            time: ''
        }
    },
    mounted () {
        this.run()
    },
    methods: {
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
.container {
    position: relative;
}
.data {
    /* border: 1px solid red; */
    position: absolute;
    left: 0;
    top: 760px;
    width: 1080px;
    height: 200px;
    display: flex;
    flex-direction: column;
    justify-content: center;
    align-items: center;
}
.date {
    /* border: 1px solid blue; */
    width: 760px;
    height: 100px;
}
.time {
    /* border: 1px solid blue; */
    width: 760px;
    height: 200px;
    /* line-height: 80px; */
    font-size: 160px;
    color: #000;
    font-weight: bolder;
    background-color: #fff;
    letter-spacing: 15px;
}
</style>
