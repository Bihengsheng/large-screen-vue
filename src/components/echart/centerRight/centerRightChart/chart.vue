<template>
  <div>
    <div id="centerRightChat" style="width: 400px; height: 510px"></div>
  </div>
</template>

<script>
import echarts from "echarts";

export default {
  data() {
    return {
      seriesData: [
        {value: 0, name: 'AAA', itemStyle: {color: 'rgb(255,112,112)'}},
        {value: 0, name: 'AA', itemStyle: {color: 'rgb(255,212,92)'}},
        {value: 0, name: 'A', itemStyle: {color: 'rgb(115,192,222)'}},
      ],
    }
  },
  mounted() {
    this.init()
  },
  methods: {
    init() {
      let that = this
      let myChart = echarts.init(document.getElementById('centerRightChat'));

      myChart.setOption({
        title: {
          text: '智慧工地评级',
          top: '2%',
          left: 'center',
          textStyle: {
            color: '#FFF'
          },
        },
        tooltip: {
          trigger: 'item'
        },
        legend: {
          orient: 'vertical',
          bottom:'20%',
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
              formatter:'总数'+'\n'+' 0'
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
            top:'-35%',

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
