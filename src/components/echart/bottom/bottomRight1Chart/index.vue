<template>
  <div>
    <div id="bottomRightChats1" style="width: 100%; height: 410px"></div>
  </div>
</template>

<script>
import echarts from "echarts";
export default {
  data() {
    return {
      seriesData: [
        {value: 1, name: '建设方', itemStyle: {color: 'rgb(255,112,112)'}},
        {value: 142, name: '施工方', itemStyle: {color: 'rgb(255,212,92)'}},
        {value: 23, name: '监理单位', itemStyle: {color: 'rgb(115,192,222)'}},
        {value: 5, name: '劳务公司', itemStyle: {color: 'rgb(86,117,206)'}},

      ],
    }
  },
  mounted() {
    this.init()
  },
  methods: {
    init() {
      let myChart = echarts.init(document.getElementById('bottomRightChats1'));

      myChart.setOption({
        grid:{
          show:false,
        },
        title: {
          text: '危大工程统计',
          top: '2%',
          left: 'left',
          textStyle: {
            color: '#FFF'
          },
        },
        xAxis: {
          type: 'category',
          data: ['高支模', '卸料台', '塔机', '深基坑', '升降机',],
          axisLine: {
            lineStyle: {
              color: '#FFF' // 设置X轴颜色为红色
            }
          }
        },
        yAxis: {
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
        series: [
          {
            data:[
              {
                value: 10,
                itemStyle: {
                  color: 'rgb(79,128,236)'
                }
              },
              {
                value: 0,
                itemStyle: {
                  color: 'rgb(79,128,236)'
                }
              },
              {
                value: 22,
                itemStyle: {
                  color: 'rgb(90,189,198)'
                }
              },
              {
                value: 10,
                itemStyle: {
                  color: 'rgb(218,146,242)'
                }
              },
              {
                value: 34,
                itemStyle: {
                  color: 'rgb(229,95,127)'
                }
              },
            ],
            type: 'bar'
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
