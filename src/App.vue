<template>
  <v-app>
    
    <NavBar></NavBar>
    
  
    <SideBar></SideBar>

    
    <!-- Sizes your content based upon application components -->
    <v-main>
      <!-- Provides the application the proper gutter -->
      <v-container fluid style="padding: 24px 32px">
        <!-- If using vue-router -->
        <router-view />
      </v-container>
    </v-main>

    <v-footer app>
      <!-- -->
    </v-footer>
  </v-app>
</template>

<script>
import NavBar from '@/components/NavBar';
import SideBar from "@/components/SideBar";
// import TestChart from '@/components/TestChart.vue'
// import QueryChart from '@/components/QueryChart.vue';
export default {
  name: "App",
  components: {
    NavBar,
    // HelloWorld,
    SideBar
    // TestChart,
  },
  data: () => ({
    drawer: true,
    items: [
      { title: "Dashboard", icon: "mdi-home-city", link: "/" },
      { title: "History", icon: "mdi-history", link: "/history" },
      { title: "Statistics", icon: "mdi-chart-bar", link: "/about" },
      { title: "Alert Control", icon: "mdi-home-city", link: "/about" },
      { title: "My Account", icon: "mdi-account", link: "/about" },
      { title: "Users", icon: "mdi-account-group-outline", link: "/about" },
    ],
    mini: true,
  }),
};
</script>

<style scoped>

</style>