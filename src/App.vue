<template>
  <v-app>
    <AppBar />

    <v-main>
      <Repositories />
    </v-main>
    <FooterComponent />
  </v-app>
</template>

<script>
import AppBar from "./components/AppBar";
import Repositories from "./components/RepositoriesComponent";
import FooterComponent from "./components/FooterComponent";

export default {
  name: "App",

  components: {
    AppBar,
    Repositories,
    FooterComponent,
  },

  data: () => ({
    //
  }),
};
</script>
