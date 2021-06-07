<template>
  <div>
    <v-row>
      <v-col>
        <QueryChart></QueryChart>
      </v-col>
    </v-row>
    <v-row>
      <v-col>
        <HistoryTable></HistoryTable>
      </v-col>
    </v-row>
  </div>
</template>

<script>
import QueryChart from "@/components/QueryChart.vue";
import HistoryTable from "@/components/HistoryTable.vue";
export default {
  name: "History",
  components: {
    QueryChart,
    HistoryTable,
  },
};
</script>
