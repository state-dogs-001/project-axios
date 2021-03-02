<template>
  <v-app>
    <v-app-bar app color="orange" dark fixed>
      <div class="d-flex align-center">
        <v-btn text href="./App.vue">
          <h1 class="mr-2">ANIME</h1>
          <v-icon>mdi-open-in-new</v-icon>
        </v-btn>
      </div>

      <v-spacer />

      <v-btn target="_blank" text @click="toTop">
        <span class="mr-2">Back to the Top Page</span>
        <v-icon>mdi-navigation</v-icon>
      </v-btn>
    </v-app-bar>

    <v-main>
      <Anime style="margin-top: 10px" />
    </v-main>

    <v-footer padless dark color="orange" style="margin-top: 60px">
      <v-col class="text-center">
        {{ new Date().getFullYear() }} — <strong>ANIME Website</strong>
      </v-col>
    </v-footer>
  </v-app>
</template>

<script>
import Anime from "./components/AnimeAPI";

export default {
  name: "App",
  components: {
    Anime,
  },
  methods: {
    toTop() {
      this.$vuetify.goTo(0);
    },
  },
};
</script>
