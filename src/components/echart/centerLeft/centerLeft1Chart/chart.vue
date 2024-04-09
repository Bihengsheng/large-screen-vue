<template>
  <div>
    <div id="echarts" style="width: 400px; height: 510px"></div>
<!--    <Echart-->
<!--        :options="options"-->
<!--        id="centreLeft1Chart"-->
<!--        height="300px"-->
<!--        width="460px"-->
<!--    ></Echart>-->
  </div>
</template>

<script>
import echarts from "echarts";


export default {
  data(){
    return{
      seriesData:[
        { value: 1048, name: '建设单位' ,itemStyle:{color:'rgb(255,212,92)'}},
        { value: 735, name: '施工单位' ,itemStyle:{color:'rgb(255,112,112)'} },
        { value: 580, name: '监理单位' ,itemStyle:{color:'rgb(115,192,222)'}},
        { value: 484, name: '检测单位' ,itemStyle:{color:'rgb(86,117,206)'}},
        { value: 300, name: '预拌混凝土企业' ,itemStyle:{color:'rgb(158,223,128)'}},
        { value: 300, name: '其他' ,itemStyle:{color:'rgb(86,171,247)'}}
      ],
    }
  },
  mounted() {
    this.init()
  },
  methods:{
    init() {
      let that = this
      let myChart = echarts.init(document.getElementById('echarts'));

      myChart.setOption({
        title: {
          text: '企业统计',
          left: 'center',
          textStyle:{
            color:'#FFF'
          },
        },
        tooltip: {
          trigger: 'item'
        },
        legend: {
          orient: 'vertical',
          bottom:'10%',
         left:'center',
          textStyle:{
            color:'#FFF'
          },
          formatter: function (name) {
            let value
            that.seriesData.forEach(item=>{
              if (item.name === name) {
                value = item.value;
              }
            })
            return name+ " "+value ;
          }
        },
        series: [
          {
            type: 'pie',
            radius: '50%',
            top:'-35%',
            data: that.seriesData
            // emphasis: {
            //   itemStyle: {
            //     shadowBlur: 10,
            //     shadowOffsetX: 0,
            //     shadowColor: 'rgba(0, 0, 0, 0.5)'
            //   }
            // }
          }
        ]
      });
      myChart.on('click', function (params) {
        console.log(params)
      })
    },
  }
};
</script>

<style lang="scss" scoped>
</style>
