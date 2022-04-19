<template>
  <v-footer dark padless id="footer">
    <v-card class="flex" flat tile>
      <v-card-title
        style="background: linear-gradient(120deg, #f46b45, #eea849)"
      >
        <strong class="subheading"
          >Get connected with me on social networks!</strong
        >

        <v-spacer></v-spacer>

        <v-btn v-for="(icon, i) in icons" :key="i" class="mx-4" dark icon>
          <a :href="icon.link" target="_blank">
            <v-icon size="24px" style="color: #fff">
              {{ icon.name }}
            </v-icon>
          </a>
        </v-btn>
      </v-card-title>

      <v-card-text class="py-2 white--text text-center">
        Designed and Developed by Sourabh Saraswat (9460907785, 9352403071)
      </v-card-text>
    </v-card>
  </v-footer>
</template>

<script>
export default {
  data: () => ({
    icons: [
      {
        name: "mdi-github",
        link: "https://github.com/SourabhSaraswat-191939",
      },
      {
        name: "mdi-facebook",
        link: "https://www.facebook.com/sourabh.saraswat.73/",
      },
      {
        name: "mdi-twitter",
        link: "https://twitter.com/SourabhSarasw15",
      },
      {
        name: "mdi-linkedin",
        link: "https://www.linkedin.com/in/sourabh-saraswat-1681b61a5/",
      },
      {
        name: "mdi-instagram",
        link: "https://www.instagram.com/ssaraswat/",
      },
    ],
  }),
};
</script>

<style scoped>
a {
  text-decoration: none;
  text-decoration-color: #fff;
}
</style>