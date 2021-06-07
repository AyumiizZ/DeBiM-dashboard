<template>
  <v-card>
    <v-list-item>
      <v-list-item-content>
        <!-- <v-list-item-title class="headline"> Total Query (last 5 min) </v-list-item-title> -->
        <h3 class="font-weight-regular">
          Total Queries <span class="font-weight-light"> (This week)</span>
        </h3>
      </v-list-item-content>
    </v-list-item>

    <v-card-text>
      <h1>
        52,315
      </h1>
      <hr>
      
      <v-icon small color="#91cc75">mdi-arrow-up-thick</v-icon>
      <span class="green__text">
        26 %
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
.green__text{
  color: #91cc75;
}
h3 span {
  font-size: 75%;
}
</style>