<template>
  <div>
    <v-row>
      <v-col>
        <TotalQueryFiveMin></TotalQueryFiveMin>
      </v-col>
      <v-col>
        <QuerySusFiveMin></QuerySusFiveMin>
      </v-col>
      <v-col>
        <IPSusFiveMin></IPSusFiveMin>
      </v-col>
      <v-col>
        <TotalQueryWeek></TotalQueryWeek>
      </v-col>
      <v-col>
        <QuerySusWeek></QuerySusWeek>
      </v-col>
      <v-col>
        <IPSusWeek></IPSusWeek>
      </v-col>
    </v-row>
    <v-row>
      <v-col>
        <QueryChart></QueryChart>
      </v-col>
    </v-row>
    <v-row>
      <v-col>
        <TopSusDomain></TopSusDomain>
      </v-col>
      <v-col>
        <TopSusDestIP></TopSusDestIP>
      </v-col>

      <v-col>
        <TopSusSourceIP></TopSusSourceIP>
      </v-col>
    </v-row>
  </div>
  <!-- <hello-world /> -->
</template>

<script>
import TotalQueryFiveMin from "@/components/TotalQueryFiveMin";
import TotalQueryWeek from "@/components/TotalQueryWeek";
import QuerySusFiveMin from "@/components/QuerySusFiveMin";
import QuerySusWeek from "@/components/QuerySusWeek";
import IPSusFiveMin from "@/components/IPSusFiveMin";
import IPSusWeek from "@/components/IPSusWeek";
import QueryChart from "@/components/QueryChart.vue";
import TopSusDestIP from "@/components/TopSusDestIP.vue";
import TopSusDomain from "@/components/TopSusDomain.vue";
import TopSusSourceIP from "@/components/TopSusSourceIP.vue";

export default {
  name: "Home",

  components: {
    TotalQueryFiveMin,
    TotalQueryWeek,
    QuerySusFiveMin,
    QuerySusWeek,
    IPSusFiveMin,
    IPSusWeek,
    QueryChart,
    TopSusDestIP,
    TopSusDomain,
    TopSusSourceIP,
  },
};
</script>

<style scoped>
.col {
  padding: 6px;
}
.v-input {
    font-size: 1.2em;
}
</style>
