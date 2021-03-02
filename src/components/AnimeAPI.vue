<template>
  <v-container>
    <v-row>
      <v-col cols="12" md="3" v-for="index in dataList.results" :key="index">
        <v-card class="mx-auto my-5" width="400" height="auto">
          <a :href="index.url">
            <v-img
              :src="index.image_url"
              class="white--text align-end"
              height="auto"
              width="auto"
            />
          </a>

          <v-card-title> {{ index.title }} </v-card-title>

          <v-card-subtitle> Rate : {{ index.rated }} </v-card-subtitle>

          <v-card-actions>
            <v-btn color="orange lighten-2" text> Explore </v-btn>

            <v-spacer></v-spacer>

            <v-btn icon @click="show = !show">
              <v-icon>{{
                show ? "mdi-chevron-up" : "mdi-chevron-down"
              }}</v-icon>
            </v-btn>
          </v-card-actions>

          <v-expand-transition>
            <div v-show="show">
              <v-divider></v-divider>

              <v-card-text>{{ index.synopsis }}</v-card-text>
            </div>
          </v-expand-transition>
        </v-card>
      </v-col>
    </v-row>
  </v-container>
</template>

<script>
import axios from "axios";
export default {
  data: () => ({
    show: false,
    dataList: {},
  }),
  mounted() {
    axios
      .get("https://api.jikan.moe/v3/search/anime?q=Fate/Zero&page=1")
      .then((res) => {
        this.dataList = res.data;
      })
      .catch((err) => {
        console.log(err);
      });
  },
};
</script>

<style></style>