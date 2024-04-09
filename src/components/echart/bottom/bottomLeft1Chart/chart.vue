<template>
  <div>
    <div id="peopleEcharts" style="width: 380px; height: 410px"></div>
  </div>
</template>

<script>
import echarts from "echarts";

export default {
  data() {
    return {
      seriesData: [
        {value: 1, name: '建设方', itemStyle: {color: 'rgb(255,112,112)'}},
        {value: 81, name: '施工方', itemStyle: {color: 'rgb(255,212,92)'}},
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
      let that = this
      let myChart = echarts.init(document.getElementById('peopleEcharts'));

      myChart.setOption({
        title: {
          text: '人员统计',
          top: '2%',
          left: 'left',
          textStyle: {
            color: '#FFF'
          },
        },
        tooltip: {
          trigger: 'item'
        },
        legend: {
          orient: 'vertical',
          right: '0',
          top:'30%',
          textStyle: {
            color: '#FFF'
          },
          formatter: function (name) {
            let value
            that.seriesData.forEach(item => {
              if (item.name === name) {
                value = item.value;
              }
            })
            return name + " " + value;
          }
        },
        series: [
          {
            type: 'pie',
            radius: ['30%', '50%'],
            avoidLabelOverlap: false,
            itemStyle: {
              borderRadius: 5,
              borderColor: 'rgb(13,18,35)',
              borderWidth: 2
            },
            label: {
              show: true,
              position: 'center',
              fontSize: 30,
              formatter:'总数'+'\n'+' 110'
            },
            // emphasis: {
            //   label: {
            //     show: true,
            //     fontSize: 40,
            //     fontWeight: 'bold'
            //   }
            // },
            labelLine: {
              show: false
            },
            top: '-10%',
            left: '-25%',

            data: that.seriesData

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
