<template>
  <div id="centerRight1">
    <div class="d-flex jc-center">
      <centerRightChart/>
    </div>
  </div>
</template>

<script>
import centerRightChart from "_c/echart/centerRight/centerRightChart/index.vue";
export default {
  components:{
    centerRightChart
  },
}
</script>

<style lang="scss" scoped>
$box-height: 510px;
$box-width: 400px;
#centerRight1 {
  padding: 16px;
  padding-top: 20px;
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

  .body-box {
    border-radius: 10px;
    overflow: hidden;

    .dv-scr-board {
      width: 270px;
      height: 340px;
    }
  }
}
</style>
