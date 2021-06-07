<template>
  <div>
    <v-navigation-drawer
      clipped
      flat
      v-model="drawer"
      :mini-variant.sync="mini"
      permanent
      app
      width="200"
    >
      <v-list-item class="px-2">
        <v-list-item-avatar>
          <v-img src="@/assets/ayumiizz-image.jpg"></v-img>
        </v-list-item-avatar>

        <v-list-item-title>Korrawit C.</v-list-item-title>

        <v-btn icon @click.stop="mini = !mini">
          <v-icon>mdi-chevron-left</v-icon>
        </v-btn>
      </v-list-item>

      <v-divider></v-divider>

      <v-list dense>
        <!-- <router-link :to="item.link"> -->
        <v-list-item
          v-for="item in items"
          :key="item.title"
          link
          :to="item.link"
        >
          <v-list-item-icon>
            <v-icon>{{ item.icon }}</v-icon>
          </v-list-item-icon>

          <v-list-item-content>
            <v-list-item-title>{{ item.title }}</v-list-item-title>
          </v-list-item-content>
        </v-list-item>
        <!-- </router-link> -->
      </v-list>
    </v-navigation-drawer>
  </div>
</template>

<script>
export default {
  name: "App",
  components: {
    // HelloWorld,
    // SideBar: SideBar
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
