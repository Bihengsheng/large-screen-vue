<template>
  <div id="bottomRight">
    <div class="bg-color-black">
      <div>
        <bottomRight1Chart />
      </div>
    </div>
  </div>
</template>

<script>
import bottomRight1Chart from "../components/echart/bottom/bottomRight1Chart";
export default {
  components: {
    bottomRight1Chart
  }
};
</script>

<style lang="scss" scoped>
$box-height: 420px;
$box-width: 100%;
#bottomRight {
  padding: 14px 16px;
  height: $box-height;
  width: $box-width;
  border-radius: 5px;
  .bg-color-black {
    height: $box-height - 30px;
    border-radius: 10px;
  }
  .text {
    color: #c3cbde;
  }
  //下滑线动态
  .decoration2 {
    position: absolute;
    right: 0.125rem;
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
