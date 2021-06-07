<template>
  <v-card>
    <v-list-item>
      <v-list-item-content>
        <!-- <v-list-item-title class="headline"> Total Query (last 5 min) </v-list-item-title> -->
        <h3 class="font-weight-regular">
          IP Suspected <span class="font-weight-light"> (Last 5 min)</span>
        </h3>
      </v-list-item-content>
    </v-list-item>

    <v-card-text>
      <h1>
        18
      </h1>
      <hr>
      
      <v-icon small color="#91cc75">mdi-arrow-up-thick</v-icon>
      <span class="green__text">
        34 %
      </span>
      
      <span> From last 10 min</span>

    </v-card-text>
  </v-card>
</template>

<style scoped>
.v-card__text{
    padding: 3px 16px 16px 16px;
}
.v-card__text h1 {
  padding: 0px 0px 16px 0px
}
.green__text{
  color: #91cc75;
}
h3 span {
  font-size: 75%;
}
</style>