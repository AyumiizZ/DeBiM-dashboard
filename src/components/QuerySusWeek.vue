<template>
  <v-card>
    <v-list-item>
      <v-list-item-content>
        <!-- <v-list-item-title class="headline"> Total Query (last 5 min) </v-list-item-title> -->
        <h3 class="font-weight-regular">
         Queries Suspected <span class="font-weight-light"> (This week)</span>
        </h3>
      </v-list-item-content>
    </v-list-item>

    <v-card-text>
      <h1>
        3,732
      </h1>
      <hr>
      
      <v-icon small color="#ee6666">mdi-arrow-down-thick</v-icon>
      <span class="red__text">
        12 %
      </span>
      
      <span> From last week</span>

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
.red__text{
  color: #ee6666;
}
h3 span {
  font-size: 75%;
}
</style>