<template>
  <div>
    <Chart :cdata="cdata" />
  </div>
</template>

<script>
import Chart from './chart.vue';
export default {
  data () {
    return {
      cdata: {
        xData: ["建设单位", "施工单位", "监理单位", "检测单位", "其他"],
        seriesData: [
          { value: 10, name: "建设单位" },
          { value: 5, name: "施工单位" },
          { value: 15, name: "监理单位" },
          { value: 25, name: "检测单位" },

          { value: 35, name: "其他" }
        ]
      }
    }
  },
  components: {
    Chart,
  },
}
</script>

<style lang="scss" scoped>
</style>
