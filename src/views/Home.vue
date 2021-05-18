<template>
  <!-- <v-card elevation="2" outlined> aaa</v-card> -->
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
      <v-col><TotalQuery></TotalQuery></v-col>
      
    </v-row>
  </div>
  <!-- <hello-world /> -->
</template>

<script>
// import HelloWorld from "../components/HelloWorld";
import TotalQuery from "@/components/TotalQuery";

export default {
  name: "Home",

  components: {
    TotalQuery: TotalQuery,
  },
};
</script>
