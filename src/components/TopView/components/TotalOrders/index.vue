<template>
  <common-card title="累计订单量" value="4263781">
    <template>
      <div
        id="total-orders-chart"
        :style="{ width: '100%', height: '100%' }"
      ></div>
    </template>
    <template v-slot:footer>
      <span>昨日订单量 </span>
      <span class="emphasis">20,300,000</span>
    </template>
  </common-card>
</template>

<script>
import CommonCardMixin from "@/mixins/CommonCardMixin";

export default {
  mixins: [CommonCardMixin],
  mounted() {
    const chartDom = document.getElementById("total-orders-chart");
    const chart = this.$echarts.init(chartDom);
    chart.setOption({
      xAxis: {
        type: "category", //value表示线
        show: false,
        boundaryGap: false, //充满整个x轴没有
      },
      yAxis: {
        show: false, //隐藏y 轴
      },
      series: [
        {
          type: "line",
          data: [
            620, 432, 220, 534, 790, 430, 220, 320, 532, 320, 834, 690, 530,
            220, 620,
          ],
          areaStyle: {
            color: "purple",
          },
          lineStyle: {
            width: 0,
          },
          itemStyle: {
            opacity: 0,
          },
          smooth: true,
        },
      ],
      grid: {
        top: 0,
        bottom: 0,
        right: 0,
        left: 0,
      },
    });
  },
};
</script>