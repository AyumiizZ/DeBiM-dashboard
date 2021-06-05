<template>
  <v-card>
    <v-list-item>
      <v-list-item-content>
        <!-- <v-list-item-title class="headline"> Total Query (last hour)</v-list-item-title> -->

        <h2 class="font-weight-regular">
          Total Query <span class="font-weight-light"> (Last Hour)</span>
        </h2>
      </v-list-item-content>
    </v-list-item>
    <v-chart class="chart" :option="option" autoresize />
    <v-card-text>
      <hr />
      <v-icon small>mdi-clock</v-icon>
      <span> Just Updated</span>
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

function randomData() {
  now = new Date(+now + oneDay);
  value = Math.random() * 600;
  return {
    name: now.toString(),
    value: [
      [now.getFullYear(), now.getMonth() + 1, now.getDate()].join("/"),
      Math.round(value),
    ],
  };
}

var data = [];
var now = +new Date(2020, 9, 3);
var oneDay = 24 * 3600 * 1000;
var value = Math.random() * 1000;
for (var i = 0; i < 200; i++) {
  data.push(randomData());
}

export default {
  name: "DonutExample",
  components: {
    VChart,
  },
  provide: {
    [THEME_KEY]: "light",
  },
  data() {
    return {
      option: {
        title: {
          left: "center",
        },
        legend: {
          show: true,
          orient: 'vertical',
          right: 70,
        top: 30,
        bottom: 20,
        textStyle: {
          fontFamily: 'Roboto'
        }
        },
        tooltip: {
          trigger: "item", formatter: '{b}       {c} ({d}%)'
        },
        series: [
          {
            type: "pie",
            radius: ["30%", "75%"],
            center: ['30%', '50%'],
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
              { value: 1048, name: "eeoahxj.info"},
              { value: 735, name: "xvcgythoxtdjxp.pm"},
              { value: 580, name: "irmgrdclr.org"},
              { value: 484, name: "0darchu3gd2z.net"},
              { value: 300, name: "Other"},
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
}
h2 span {
  font-size: 75%;
}
</style>
