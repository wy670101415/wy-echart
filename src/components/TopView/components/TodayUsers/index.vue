<template>
  <common-card title="累计用户数" value="1,890,00">
    <template>
      <div
        id="today-users-char"
        :style="{ width: '100%', height: '100%' }"
      ></div>
    </template>
    <template v-slot:footer>
      <div class="total-users-footer">
        <span>日同比 </span>
        <span class="emphasis">8.14%</span>
        <div class="increase"></div>
        <span class="month">月同比 </span>
        <span class="emphasis">8.14%</span>
        <div class="decrease"></div>
      </div>
    </template>
  </common-card>
</template>

<script>
import CommonCardMixin from "@/mixins/CommonCardMixin";

export default {
  mixins: [CommonCardMixin],
  mounted() {
    const chartDom = document.getElementById("today-users-char");
    const chart = this.$echarts.init(chartDom);
    chart.setOption({
      color: ["#3398DB"],
      xAxis: {
        show: false,
        type: "value",
      },
      yAxis: {
        type: "category",
        show: false,
      },
      series: [
        {
          type: "bar",
          stack: "总量",
          data: [100],
          barWidth: "10",
          itemStyle: {
            color: "#45c946",
          },
        },
        {
          stack: "总量",
          type: "bar",
          data: [250],
          itemStyle: {
            color: "#eee",
          },
        },
        {
          stack: "总量",
          type: "custom", //custom表示自定义
          data: [100],
          renderItem: (params, api) => {
            const value = api.value(0);
            const end = api.coord([value, 0]);
            return {
              type: "group",
              position: end,
              children: [
                {
                  type: "path",
                  shape: {
                    d: "M0 767.909l512.029-511.913L1024 767.909 0 767.909z",
                    x: -10,
                    y: 8,
                    width: 20,
                    height: 20,
                    layout:'cover'
                  },
                  style: {
                    fill: "#45c946",
                  },
                },
                {
                  type: "path",
                  shape: {
                    d: "M1024 255.996 511.971 767.909 0 255.996 1024 255.996z",
                    x: -10,
                    y: -25,
                    width: 20,
                    height: 20,
                    layout:'cover'

                  },
                  style: {
                    fill: "#45c946",
                  },
                },
              ],
            };
          },
          itemStyle: {
            color: "green",
          },
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

<style lang="scss" scoped>
.total-users-footer {
  display: flex;
  align-items: center;
  .month {
    margin-left: 10px;
  }
}
</style>
<svg t="1629771437401" class="icon" viewBox="0 0 1024 1024" version="1.1" xmlns="http://www.w3.org/2000/svg" p-id="2074" width="200" height="200"><path d="M1024 255.996 511.971 767.909 0 255.996 1024 255.996z" p-id="2075"></path></svg>