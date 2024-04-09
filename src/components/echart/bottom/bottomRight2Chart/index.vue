<template>
  <div>
    <div id="bottomRightChats2" style="width: 100%; height: 510px"></div>
  </div>
</template>

<script>
import echarts from "echarts";

export default {
  data() {
    return {
      seriesData: [
        {value: 52, name: '在线', itemStyle: {color: 'rgb(76,171,253)'}},
        {value: 8, name: '离线', itemStyle: {color: 'rgb(240,214,114)'}},

      ],
    }
  },
  mounted() {
    this.init()
  },
  methods: {
    init() {
      let that = this
      let myChart = echarts.init(document.getElementById('bottomRightChats2'));

      myChart.setOption({
        title: {
          text: '区域视频监控',
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
          top: '25%',
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
              formatter:'总数'+'\n'+'\n'+' 60'
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
            top: '-20%',
            left: '-20%',
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
