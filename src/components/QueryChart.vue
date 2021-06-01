<template>
  <v-card>
    <v-list-item one-line>
      <v-list-item-content>
        <v-list-item-title class="headline"> Total Query </v-list-item-title>
        <!-- <v-list-item-subtitle>last 5 Minutes</v-list-item-subtitle> -->
      </v-list-item-content>
      <v-list-item-action>
        <v-row justify="end">
          <v-col cols="auto">
            <vc-date-picker
              v-model="range"
              mode="dateTime"
              :masks="masks"
              is-range
            >
              <template v-slot="{ inputValue, inputEvents}">
                <v-row>
                  <v-col cols="auto">
                    <v-text-field label="From" :value="inputValue.start"
                      v-on="inputEvents.start"></v-text-field>
                  </v-col>
                  <v-col cols="auto">
                    <v-icon>mdi-chevron-right</v-icon>
                  </v-col>
                  <v-col cols="auto">
                    <v-text-field label="To" :value="inputValue.end"
                      v-on="inputEvents.end"></v-text-field>
                  </v-col>
                </v-row>
              </template>
            </vc-date-picker>
          </v-col>
          <v-col cols="auto">
            <v-btn icon>
              <v-icon color="grey lighten-1">mdi-filter</v-icon>
            </v-btn>
          </v-col>
          <v-col cols="auto">
            <v-btn icon>
              <v-icon color="grey lighten-1">mdi-magnify</v-icon>
            </v-btn>
          </v-col>
        </v-row>
      </v-list-item-action>
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
import { LineChart } from "echarts/charts";
import {
  TitleComponent,
  TooltipComponent,
  LegendComponent,
  CalendarComponent,
} from "echarts/components";
import VChart, { THEME_KEY } from "vue-echarts";

use([
  CanvasRenderer,
  LineChart,
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
  name: "HelloWorld",
  components: {
    VChart,
  },
  provide: {
    [THEME_KEY]: "light",
  },
  data() {
    return {
      option: {
        grid: {
          left: "3%",
          top: "3%",
          right: "1%",
          bottom: "7%",
        },
        tooltip: {
          trigger: "axis",
          formatter: function (params) {
            params = params[0];
            var date = new Date(params.name);
            return (
              date.getDate() +
              "/" +
              (date.getMonth() + 1) +
              "/" +
              date.getFullYear() +
              " : " +
              params.value[1]
            );
          },
          axisPointer: {
            animation: false,
          },
        },
        toolbox: {
          feature: {
            dataZoom: {
              yAxisIndex: "none",
            },
            restore: {},
            saveAsImage: {},
          },
        },
        xAxis: {
          type: "time",
          boundaryGap: false,
        },
        yAxis: {
          type: "value",
          boundaryGap: false,
        },
        dataZoom: [
          {
            type: "inside",
            start: 0,
            end: 20,
          },
          {
            start: 0,
            end: 20,
          },
        ],
        series: [
          {
            name: "User",
            type: "line",
            smooth: true,
            symbol: "none",
            // areaStyle: {},
            data: data,
          },
        ],
      },
      datetimeTo: null,
      datetimeFrom: null,
      dateTo: null,
      menuTo: false,
      dateFrom: null,
      menuFrom: false,
      timeFrom: null,
      menuTimeFrom: false,
      timeTo: null,
      menuTimeTo: false,
      dateRange: {
        start: new Date(2020, 0, 6),
        end: new Date(2020, 0, 10),
      },
      date: new Date(),
      range: {
        start: new Date(2020, 9, 12),
        end: new Date(2020, 9, 16),
      },
      masks: {
        input: "YYYY-MM-DD h:mm A",
      },
    };
  },
  methods: {
    timeInit: function () {
      var currentTime = new Date();
      var timeZoneOffset = currentTime.getTimezoneOffset() * 60000;
      var localISOTime = new Date(currentTime - timeZoneOffset)
        .toISOString()
        .slice(0, -1);
      var halfMin = 30000;
      var halfMinBeforeISOTime = new Date(
        currentTime - timeZoneOffset - halfMin
      )
        .toISOString()
        .slice(0, -1);
      console.log(currentTime.toISOString().substr(11, 8));
      console.log(localISOTime);
      console.log(halfMinBeforeISOTime);
      this.dateFrom = halfMinBeforeISOTime.substr(0, 10);
      this.dateTo = localISOTime.substr(0, 10);
      this.timeFrom = halfMinBeforeISOTime.substr(11, 8);
      this.timeTo = localISOTime.substr(11, 8);
      this.datetimeTo = {
        date: halfMinBeforeISOTime.substr(0, 10),
        time: halfMinBeforeISOTime.substr(11, 8),
      };
      this.datetimeFrom = {
        date: localISOTime.substr(0, 10),
        time: localISOTime.substr(11, 8),
      };
    },
    // switchToMenu: function(ref, datetime, newref) {
    //   ref.save(datetime)
    //   newref = true
    //   console.log(newref)
    // }
  },
  mounted() {
    this.timeInit();
  },
};
</script>

<style scoped>
.chart {
  height: 300px;
}
.v-list-item__action {
  padding: 18px 4px 0px 0px;
  margin: 0px 0px;
}
</style>
