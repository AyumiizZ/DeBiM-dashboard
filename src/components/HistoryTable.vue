<template>
  <v-card>
    <v-list-item>
      <v-list-item-content>
        <v-list-item-title class="headline">
          Queries History
        </v-list-item-title>
      </v-list-item-content>
    </v-list-item>
    <v-data-table
      :headers="headers"
      :items="desserts"
      multi-sort
      class="elevation-1"
    ></v-data-table>
  </v-card>
</template>

<script>
export default {
  data() {
    return {
      headers: [
        {
          text: "Source IP",
          value: "srcip",
        },
        {
          text: "Source Port",
          value: "srcpo",
        },
        {
          text: "Destination IP",
          value: "destip",
        },
        {
          text: "Destination Port",
          value: "destpo",
        },
        {
          text: "Timestamp",
          value: "timestamp",
        },
        {
          text: "Query Data",
          value: "qd",
        },
      ],
      desserts: [
        {
          srcip: "192.168.1.1",
          srcpo: 38323,
          destip: "158.108.0.2",
          destpo: 53,
          timestamp: "2021-06-07 17:25:01.105",
          qd: "eeoahxj.info",
        },
        {
          srcip: "192.168.1.1",
          srcpo: 51490,
          destip: "158.108.0.3",
          destpo: 53,
          timestamp: "2021-06-07 17:25:01.105",
          qd: "eeoahxj.info",
        },
        {
          srcip: "192.168.1.1",
          srcpo: 47081,
          destip: "158.108.0.2",
          destpo: 53,
          timestamp: "2021-06-07 17:25:01.743",
          qd: "www.ku.ac.th",
        },
        {
          srcip: "192.168.1.1",
          srcpo: 47845,
          destip: "158.108.0.3",
          destpo: 53,
          timestamp: "2021-06-07 17:25:01.743",
          qd: "www.ku.ac.th",
        },
        {
          srcip: "192.168.1.1",
          srcpo: 60642,
          destip: "158.108.0.3",
          destpo: 53,
          timestamp: "2021-06-07 17:25:01.743",
          qd: "www.ku.ac.th",
        },
        {
          srcip: "192.168.1.1",
          srcpo: 46538,
          destip: "158.108.0.2",
          destpo: 53,
          timestamp: "2021-06-07 17:25:01.105",
          qd: "jzsqsq.net",
        },
        {
          srcip: "192.168.1.1",
          srcpo: 34764,
          destip: "158.108.0.2",
          destpo: 53,
          timestamp: "2021-06-07 17:25:01.743",
          qd: "www.ku.ac.th",
        },
        
        {
          srcip: "192.168.1.1",
          srcpo: 36983,
          destip: "158.108.0.3",
          destpo: 53,
          timestamp: "2021-06-07 17:25:02.013",
          qd: "oflpzfgeviq.com",
        },
        {
          srcip: "192.168.1.1",
          srcpo: 44639,
          destip: "158.108.0.2",
          destpo: 53,
          timestamp: "2021-06-07 17:25:02.013",
          qd: "oflpzfgeviq.com",
        },
        {
          srcip: "192.168.1.1",
          srcpo: 60540,
          destip: "158.108.0.3",
          destpo: 53,
          timestamp: "2021-06-07 17:25:02.013",
          qd: "oflpzfgeviq.com",
        },
        {
          srcip: "192.168.1.1",
          srcpo: 53462,
          destip: "158.108.0.2",
          destpo: 53,
          timestamp: "2021-06-07 17:25:01.105",
          qd: "www.ku.ac.th",
        },
      ],
    };
  },
};
</script>

<style scoped>
th {
  font-size: 24px;
}
tr {
  font-size: 24px;
}
</style>