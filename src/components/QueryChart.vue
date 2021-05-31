<template>
  <v-card>
    {{timeInit()}}
    <v-list-item one-line>
      <v-list-item-content>
        <v-list-item-title class="headline"> Total Query </v-list-item-title>
        <!-- <v-list-item-subtitle>last 5 Minutes</v-list-item-subtitle> -->
      </v-list-item-content>
      <v-list-item-action>
        <v-row justify="end">
          <v-col cols="2">
            <v-menu
              ref="menuFrom"
              v-model="menuFrom"
              :close-on-content-click="false"
              :return-value.sync="dateFrom"
              transition="scale-transition"
              offset-y
              min-width="auto"
            >
              <template v-slot:activator="{ on, attrs }">
                <v-text-field
                  v-model="dateFrom"
                  label="From"
                  prepend-icon="mdi-calendar"
                  readonly
                  v-bind="attrs"
                  v-on="on"
                ></v-text-field>
              </template>
              <v-date-picker v-model="dateFrom" no-title scrollable>
                <v-spacer></v-spacer>
                <v-btn text color="primary" @click="menuTo = false">
                  Cancel
                </v-btn>
                <v-btn
                  text
                  color="primary"
                  @click="$refs.menuFrom.save(dateFrom)"
                >
                  OK
                </v-btn>
              </v-date-picker>
            </v-menu>
          </v-col>
          <v-col cols="1">
            <v-menu
              ref="menuTimeFrom"
              v-model="menuTimeFrom"
              :close-on-content-click="false"
              :nudge-right="40"
              :return-value.sync="timeFrom"
              transition="scale-transition"
              offset-y
              max-width="290px"
              min-width="290px"
            >
              <template v-slot:activator="{ on, attrs }">
                <v-text-field
                  v-model="timeFrom"
                  readonly
                  v-bind="attrs"
                  v-on="on"
                ></v-text-field>
              </template>
              <v-time-picker
                v-if="menuTimeFrom"
                v-model="timeFrom"
                format="24hr"
                use-seconds
              >
                <v-btn text color="primary" @click="menuTimeFrom = false">
                  Cancel
                </v-btn>
                <v-spacer></v-spacer>

                <v-btn
                  text
                  color="primary"
                  @click="$refs.menuTimeFrom.save(timeFrom)"
                >
                  OK
                </v-btn>
              </v-time-picker>
            </v-menu>
          </v-col>
          <v-col cols="2">
            <v-menu
              ref="menuTo"
              v-model="menuTo"
              :close-on-content-click="false"
              :return-value.sync="dateTo"
              transition="scale-transition"
              offset-y
              min-width="auto"
            >
              <template v-slot:activator="{ on, attrs }">
                <v-text-field
                  v-model="dateTo"
                  label="To"
                  prepend-icon="mdi-calendar"
                  readonly
                  v-bind="attrs"
                  v-on="on"
                ></v-text-field>
              </template>
              <v-date-picker v-model="dateTo" no-title scrollable>
                <v-spacer></v-spacer>
                <v-btn text color="primary" @click="menuTo = false">
                  Cancel
                </v-btn>
                <v-btn text color="primary" @click="$refs.menuTo.save(dateTo)">
                  OK
                </v-btn>
              </v-date-picker>
            </v-menu>
          </v-col>
          <v-col cols="1">
            <v-menu
              ref="menuTimeTo"
              v-model="menuTimeTo"
              :close-on-content-click="false"
              :nudge-right="40"
              :return-value.sync="timeTo"
              transition="scale-transition"
              offset-y
              max-width="290px"
              min-width="290px"
            >
              <template v-slot:activator="{ on, attrs }">
                <v-text-field
                  v-model="timeTo"
                  readonly
                  v-bind="attrs"
                  v-on="on"
                ></v-text-field>
              </template>
              <v-time-picker
                v-if="menuTimeTo"
                v-model="timeTo"
                format="24hr"
                use-seconds
              >
                <v-btn text color="primary" @click="menuTimeTo = false">
                  Cancel
                </v-btn>
                <v-spacer></v-spacer>

                <v-btn
                  text
                  color="primary"
                  @click="$refs.menuTimeTo.save(timeTo)"
                >
                  OK
                </v-btn></v-time-picker
              >
            </v-menu>
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
      dateTo: null,
      menuTo: false,
      dateFrom: null,
      menuFrom: false,
      timeFrom: null,
      menuTimeFrom: false,
      timeTo: null,
      menuTimeTo: false,
    };
  },
  methods: {
    timeInit: function() {
        var currentTime = new Date()
        var timeZoneOffset = currentTime.getTimezoneOffset() * 60000
        var localISOTime = (new Date(currentTime - timeZoneOffset)).toISOString().slice(0, -1);
        var halfMin = 30000
        var halfMinBeforeISOTime = (new Date(currentTime - timeZoneOffset - halfMin)).toISOString().slice(0, -1)
        console.log(currentTime.toISOString().substr(11, 8))
        console.log(localISOTime)
        console.log(halfMinBeforeISOTime)
        this.dateFrom = halfMinBeforeISOTime.substr(0,10)
        this.dateTo = localISOTime.substr(0,10)
        this.timeFrom= halfMinBeforeISOTime.substr(11,8)
        this.timeTo = localISOTime.substr(11,8)
    }
  }
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
