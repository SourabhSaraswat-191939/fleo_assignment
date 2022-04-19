<template>
  <v-app-bar app elevate-on-scroll style="min-height: 70px">
    <v-app-bar-nav-icon
      class="hidden-md-and-up"
      @click.stop="drawer = !drawer"
    ></v-app-bar-nav-icon>

    <v-toolbar-title
      class="hidden-sm-and-down"
      style="font-weight: bold; color: #000"
      ><v-icon>mdi-github</v-icon> Github Repositories</v-toolbar-title
    >

    <v-spacer></v-spacer>

    <v-spacer></v-spacer>
  </v-app-bar>
</template>

<script>
export default {
  data() {
    return {
      sortStar: ["Ascending", "Descending"],
      sortName: ["Alphabetically", "Reverse Alphabetically"],
    };
  },
  methods: {
    sortByStar() {
      console.log("printing");
    },
    sortByName() {
      console.log("printing");
    },
  },
};
</script>
