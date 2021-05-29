<template>
  <div>
    <!-- <v-divider></v-divider> -->
    <v-app-bar app dense clipped-left style="padding: 0px 0px">
      <v-btn class="rounded-lg" text> DeBiM </v-btn>
    <v-spacer></v-spacer>
    <v-btn icon>
      <v-icon>mdi-moon-waning-crescent</v-icon>
    </v-btn>

    <v-badge color="red" content="6" offset-x="24" offset-y="24">
      <v-btn icon>
        <v-icon>mdi-bell</v-icon>
      </v-btn>
    </v-badge>

    <v-menu left bottom>
      <template v-slot:activator="{ on, attrs }">
        <v-btn elevation="0" rounded v-bind="attrs" v-on="on">
          <v-avatar size="24">
            <img src="https://randomuser.me/api/portraits/men/1.jpg" />
          </v-avatar>
          <v-icon>mdi-menu-down</v-icon>
        </v-btn>
      </template>

      <v-list>
        <v-list-item v-for="n in 5" :key="n" @click="() => {}">
          <v-list-item-title>Option {{ n }}</v-list-item-title>
        </v-list-item>
      </v-list>
    </v-menu>
    </v-app-bar>
  </div>
</template>

<script>
export default {
  name: "NavBar",
  components: {
    // HelloWorld,
    // SideBar: SideBar
    // TestChart,
  },
  data: () => ({
    items: [
      { title: "Dashboard", icon: "mdi-home-city", link: "/" },
      { title: "History", icon: "mdi-history", link: "/history" },
      { title: "Statistics", icon: "mdi-chart-bar", link: "/about" },
      { title: "Alert Control", icon: "mdi-home-city", link: "/about" },
      { title: "My Account", icon: "mdi-account", link: "/about" },
      { title: "Users", icon: "mdi-account-group-outline", link: "/about" },
    ],
  }),
};
</script>
