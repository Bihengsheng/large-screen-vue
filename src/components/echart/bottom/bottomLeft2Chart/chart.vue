<template>
  <div>
    <div id="peopleEcharts1" style="width: 380px; height: 350px"></div>
  </div>
</template>

<script>
import echarts from "echarts";

export default {
  mounted() {
    this.init()
  },
  methods: {
    init() {
      let myChart = echarts.init(document.getElementById('peopleEcharts1'));

      myChart.setOption({
        title: {
          text: '区域施工扬尘',
          top: '2%',
          left: 'left',
          textStyle: {
            color: '#FFF'
          },
        },
        grid: {
          left: '3%',
          right: '4%',
          bottom: '3%',
          containLabel: true
        },
        xAxis: {
          type: 'value',
          splitLine:{
            show:false
          },
          axisLine: {
            lineStyle: {
              color: '#FFF' // 设置X轴颜色为红色
            }
          }
        },
        yAxis: {
          type: 'category',
          data: ['严重污染', '重度污染', '轻度污染', '良', '优'],
          axisLine: {
            lineStyle: {
              color: '#FFF' // 设置X轴颜色为红色
            }
          }
        },
        series: [
          {
            type: 'bar',
            data: [
              {
                value: 1,
                itemStyle: {
                  color: 'rgb(203,71,43)',
                  borderRadius:[0,50,50,0]
                }
              },
              {
                value: 1,
                itemStyle: {
                  color: 'rgb(195,91,22)',
                  borderRadius:[0,50,50,0]
                }
              },
              {
                value: 1,
                itemStyle: {
                  color: 'rgb(196,157,56)',
                  borderRadius:[0,50,50,0]
                }
              },

              {
                value: 1,
                itemStyle: {
                  color: 'rgb(104,227,217)',
                  borderRadius:[0,50,50,0]
                }
              },
              {
                value: 18,
                itemStyle: {
                  color: 'rgb(118,214,118)',
                  borderRadius:[0,50,50,0]
                }
              },
            ]
          }
        ]
      });
      myChart.on('click', function (params) {
        console.log(params)
      })
    },
  }
}
</script>
