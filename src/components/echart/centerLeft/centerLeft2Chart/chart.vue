<template>
  <div>
    <!--    <div id="main" style="width: 550px; height: 460px"></div>-->
    <div id="map" class="map-container"></div>
    <!--    <Echart id="centreLeft2Chart" ref="centreLeft2ChartRef" :options="options" height="460px" width="550px"/>-->
  </div>
</template>
<script>
import * as echarts from 'echarts';
import shandongData from "@/assets/liaochengData.json"
import AMapLoader from '@amap/amap-jsapi-loader'
import liaocheng from "@/store/liaocheng";
window._AMapSecurityConfig = {
  securityJsCode: '7ebaf7fb898f2d072d1222b5b59790ce' // '「申请的安全密钥」',
}
export default {
  data() {
    return {
      map: null,
      zoom:0
    }
  },
  activated() {
    // this.init()
    this.initAMap()
  },
  mounted() {
    // this.init()
    this.initAMap()
  },
  methods: {
    // 开启定时器
    init() {
      let myChart = echarts.init(document.getElementById('main'));
      myChart.hideLoading();
      echarts.registerMap('山东', shandongData);
      console.log(myChart)
      myChart.setOption({

        tooltip: {
          trigger: 'item',
        },
        series: [
          {
            name: '山东',
            type: 'map',
            map: '山东',
            label: {
              show: true
            },
          }
        ]
      });
      myChart.on('click', function (params) {
        console.log(params)
      })
    },
    initAMap() {
      AMapLoader.load({
        key: "3c2a5615edc0205a9e5b238dd823cdde", // 申请好的Web端开发者Key，首次调用 load 时必填
        version: "2.0", // 指定要加载的 JSAPI 的版本，缺省时默认为 1.4.15
        plugins: ["AMap.Scale", "AMap.ToolBar", "AMap.ControlBar", 'AMap.Geocoder', 'AMap.Marker',
          'AMap.CitySearch', 'AMap.Geolocation', 'AMap.AutoComplete', 'AMap.InfoWindow'], // 需要使用的的插件列表，如比例尺'AMap.Scale'等
      }).then((AMap) => {
        // 获取到作为地图容器的DOM元素，创建地图实例
        this.map = new AMap.Map("map", { //设置地图容器id
          rotateEnable:true,
          pitchEnable:true,
          pitch: 50,
          rotation: -15,
          zooms:[2,20],
          resizeEnable: true,
          zoom: 9, // 地图显示的缩放级别
          viewMode: "2D", // 使用3D视图
          zoomEnable: true, // 地图是否可缩放，默认值为true
          dragEnable: true, // 地图是否可通过鼠标拖拽平移，默认为true
          doubleClickZoom: true, // 地图是否可通过双击鼠标放大地图，默认为true

          center: [115.985371, 36.456703], // 初始化中心点坐标 广州
          mapStyle: "amap://styles/grey", // 设置颜色底层
        })

          var polygon = new AMap.Polygon({
            path: liaocheng, //路径
            fillColor: '#ccebc5',
            strokeOpacity: 1,
            fillOpacity: 0.5,
            strokeColor: '#2b8cbe',
            strokeWeight: 1,
            strokeStyle: 'dashed',
            strokeDasharray: [5, 5],
          });
          this.map.add(polygon);
//将覆盖物调整到合适视野



      }).catch(e => {
        console.log(e)
      })


    }
  }
}
</script>
<style>
.map-container {
  width: 1060px;
  height: 480px;
}
</style>
