<template>
  <v-card>
    <v-list-item>
      <v-list-item-content>
        <!-- <v-list-item-title class="headline"> Total Query (last hour)</v-list-item-title> -->

        <h2 class="font-weight-regular">
          Top Suspected Destination IP <span class="font-weight-light"> (Last Hour)</span>
        </h2>
      </v-list-item-content>
    </v-list-item>
    <hr class="outside__hr"/>
    <v-row>
      <v-col cols="10">
        <v-chart class="chart" :option="option" autoresize />
      </v-col>
    </v-row>
    <v-card-text>
      <hr />
      <v-icon small>mdi-clock</v-icon>
      <span> Last Updated: {{date}}</span>
    </v-card-text>
  </v-card>
</template>

<script>
import { use } from "echarts/core";
import { CanvasRenderer } from "echarts/renderers";
import { PieChart } from "echarts/charts";
import {
  TitleComponent,
  TooltipComponent,
  LegendComponent,
  CalendarComponent,
} from "echarts/components";
import VChart, { THEME_KEY } from "vue-echarts";

use([
  CanvasRenderer,
  PieChart,
  TitleComponent,
  TooltipComponent,
  LegendComponent,
  CalendarComponent,
]);

export default {
  name: "TopSusDestIP",
  components: {
    VChart,
  },
  provide: {
    [THEME_KEY]: "light",
  },
  data() {
    return {
      date: new Date(),
      option: {
        title: {
          left: "center",
        },
        legend: {
          show: true,
          orient: "vertical",
          right: 0,
          top: 30,
          bottom: 20,
          textStyle: {
            fontFamily: "Roboto",
            fontSize: 16,
          },
        },
        tooltip: {
          trigger: "item",
          formatter: "{b}       {c} ({d}%)",
        },
        series: [
          {
            type: "pie",
            radius: ["30%", "75%"],
            center: ["30%", "50%"],
            label: {
              fontSize: 10,
              show: true,
              formatter: "{b}\n{c} ({d}%)",
            },
            labelLine: {
              show: true,
              lineStyle: {
                width: 3,
              },
            },
            itemStyle: {
              borderRadius: 10,
              borderColor: "#fff",
              borderWidth: 2,
            },
            data: [
              { value: 1806, name: "192.168.1.1 36.75%" },
              { value: 1329, name: "192.168.1.2 27.04%" },
              { value: 928, name: "192.168.1.3 18.88%" },
              { value: 561, name: "192.168.1.4 11.41%" },
              { value: 291, name: "Other 5.92%" },
            ],
          },
        ],
      },
    };
  },
};
</script>

<style scoped>
.chart {
  height: 200px;
  width: 500px;
}
h2 span {
  font-size: 65%;
}
.outside__hr {
  margin: 3px 16px 3px 16px;
}
</style>
