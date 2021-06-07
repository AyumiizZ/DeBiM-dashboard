<template>
  <v-card>
    <v-list-item one-line>
      <v-list-item-content>
        <v-list-item-title class="headline"> Queries </v-list-item-title>
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
              <template v-slot="{ inputValue, inputEvents }">
                <v-row>
                  <v-col cols="auto">
                    <v-text-field
                      label="From"
                      :value="inputValue.start"
                      v-on="inputEvents.start"
                    ></v-text-field>
                  </v-col>
                  <v-col cols="auto">
                    <v-icon>mdi-chevron-right</v-icon>
                  </v-col>
                  <v-col cols="auto">
                    <v-text-field
                      label="To"
                      :value="inputValue.end"
                      v-on="inputEvents.end"
                    ></v-text-field>
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
              <v-icon color="grey lighten-1" @click="submitRange"
                >mdi-magnify</v-icon
              >
            </v-btn>
          </v-col>
        </v-row>
      </v-list-item-action>
    </v-list-item>
    <hr />
    <v-chart
      v-if="isMounted"
      ref="totalquerychart"
      class="chart"
      :option="option"
      autoresize
    />
    <v-card-text> </v-card-text>
  </v-card>
</template>

<script>
// import { use } from "echarts/core";
// import { CanvasRenderer } from "echarts/renderers";
// import { LineChart } from "echarts/charts";
// import {
//   TitleComponent,
//   TooltipComponent,
//   LegendComponent,
//   CalendarComponent,
// } from "echarts/components";
import { THEME_KEY } from "vue-echarts";

// use([
//   CanvasRenderer,
//   LineChart,
//   TitleComponent,
//   TooltipComponent,
//   LegendComponent,
//   CalendarComponent,
// ]);

export default {
  name: "QueryChart",
  components: {
    // VChart,
  },
  provide: {
    [THEME_KEY]: "light",
  },
  data() {
    return {
      isMounted: true,
      option: null,
      date: new Date(),
      range: null,
      showingRange: null,
      masks: {
        input: "YYYY-MM-DD h:mm A",
      },
    };
  },
  methods: {
    timeInit: function () {
      var currentTime = new Date();
      var OneHour = 60000 * 60;
      this.range = {
        start: new Date(currentTime.getTime() - OneHour),
        end: currentTime,
      };
      this.submitRange();
    },
    submitRange: async function () {
      this.showingRange = this.range;
      var dateRange = await this.genDateStep(1000);
      var option = {
        legend: {
          top: "0%",
          data: ["Total", "Infected"],
          textStyle: {
            fontFamily: "Roboto",
            fontSize: 16,
          },
        },
        grid: {
          left: "2%",
          top: "11%",
          right: "2%",
          bottom: "7%",
          containLabel: true,
        },
        xAxis: {
          name: "Time",
          nameLocation: "center",
          nameGap: 25,
          nameTextStyle: {
            fontSize: 16,
          },
          type: "time",
          boundaryGap: false,
        },
        yAxis: {
          name: "# Queries",
          nameLocation: "middle",
          nameGap: 45,
          nameTextStyle: {
            fontSize: 16,
            padding: [0, 0, 0, 0],
          },
          type: "value",
          boundaryGap: false,
        },

        series: [
          {
            name: "Total",
            data: await this.genData(dateRange, 1),
            type: "line",
            areaStyle: {},
            // color: '#73c0de'
          },
          {
            name: "Infected",
            data: await this.genData(dateRange, 0.1),
            type: "line",
            areaStyle: {},
            color: "#ee6666",
          },
        ],
      };
      setTimeout(this.testMethod, 50, this.$refs.totalquerychart, option);
    },
    genDateStep: function (interval) {
      var dateRange = new Array();
      var timediff = (this.range.end - this.range.start) / interval;
      for (var i = 1; i < interval; i++) {
        dateRange.push(new Date(this.range.start.getTime() + i * timediff));
      }
      dateRange.push(this.range.end);
      return dateRange;
    },
    genData: function (dateRange, percent) {
      var mask = [
        1400, 1200, 1000, 900, 800, 750, 700, 800, 1150, 1800, 2300, 2600, 2800,
        2900, 3000, 3050, 3000, 2950, 2700, 2400, 2100, 1900, 1600, 1550, 1400,
      ];
      var dataSeries = new Array();
      for (var i = 0; i < 1000; i++) {
        // console.log(dateRange[i])
        var hr = dateRange[i].getHours();
        var min = dateRange[i].getMinutes();
        var rawdata = mask[hr] + (min / 60) * (mask[hr + 1] - mask[hr]);
        var rand_percent = percent + (Math.random() * 0.1 - 0.05);
        dataSeries.push([dateRange[i], rawdata * rand_percent]);
      }
      return dataSeries;
    },
    testMethod: function (chartInstance, option) {
      chartInstance.setOption(option);
    },
  },
  mounted() {
    this.timeInit();
    this.isMounted = true;
  },
};
</script>

<style scoped>
.chart {
  height: 350px;
}
.v-list-item__action {
  padding: 18px 4px 0px 0px;
  margin: 0px 0px;
}
hr {
  margin: 3px 16px 3px 16px;
}
</style>
