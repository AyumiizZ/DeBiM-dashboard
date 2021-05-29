<template>
  <div>
    <v-row>
      <v-col>
        <TotalQuery></TotalQuery>
      </v-col>
      <v-col>
        <TotalQuery></TotalQuery>
      </v-col>
      <v-col>
        <TotalQuery></TotalQuery>
      </v-col>
      <v-col>
        <TotalQuery></TotalQuery>
      </v-col>
      <v-col>
        <TotalQuery></TotalQuery>
      </v-col>
      <v-col>
        <TotalQuery></TotalQuery>
      </v-col>
    </v-row>
    <v-row>
      <v-col>
        <QueryChart></QueryChart>
      </v-col>
    </v-row>
    <v-row>
      <v-col>
        <Donut></Donut>
      </v-col>
      <v-col>
        <Donut></Donut>
      </v-col>
      <v-col>
        <Donut></Donut>
      </v-col>
    </v-row>
    
    
  </div>
  <!-- <hello-world /> -->
</template>

<script>
// import HelloWorld from "../components/HelloWorld";
import TotalQuery from "@/components/TotalQuery";
import QueryChart from '@/components/QueryChart.vue';
import Donut from '@/components/Donut.vue';
// import TestChart from '@/components/TestChart.vue'

export default {
  name: "Home",

  components: {
    TotalQuery: TotalQuery,
    QueryChart: QueryChart,
    Donut,
  },
};
</script>
