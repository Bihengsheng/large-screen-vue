<template>
  <div id="centerLeft1">
    <div class="bg-color-black">
<!--      <div class="d-flex pt-2 pl-2">-->
<!--        <span>-->
<!--          <icon name="chart-pie" class="text-icon"></icon>-->
<!--        </span>-->
<!--&lt;!&ndash;        <div class="d-flex">&ndash;&gt;-->
<!--&lt;!&ndash;          <span class="fs-xl text mx-2">地图数据</span>&ndash;&gt;-->
<!--&lt;!&ndash;          <dv-decoration-1 class="dv-dec-1" />&ndash;&gt;-->
<!--&lt;!&ndash;        </div>&ndash;&gt;-->
<!--      </div>-->
      <div class="d-flex jc-center">
        <CenterLeft2Chart />
      </div>
    </div>
  </div>
</template>

<script>
import CenterLeft2Chart from "@/components/echart/centerLeft/centerLeft2Chart";
export default {
  components: {
    CenterLeft2Chart
  },
};
</script>

<style lang="scss" scoped>
#centerLeft1 {
  $box-width: 1090px;
  $box-height: 510px;
  padding: 16px;
  height: $box-height;
  min-width: $box-width;
  border-radius: 5px;
  .bg-color-black {
    height: $box-height - 30px;
    border-radius: 10px;
  }
  .text {
    color: #c3cbde;
  }
  .dv-dec-1 {
    position: relative;
    width: 100px;
    height: 20px;
    top: -3px;
  }
  .chart-box {
    margin-top: 16px;
    width: 170px;
    height: 170px;
    .active-ring-name {
      padding-top: 10px;
    }
  }
}
</style>
