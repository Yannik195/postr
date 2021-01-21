<template>
  <v-app>
    <div>
      <v-text-field label="Solo" placeholder="Placeholder" solo></v-text-field>
      <v-btn elevation="2">post</v-btn>
      {{ posts }}
    </div>
  </v-app>
</template>

<script>
import axios from "axios";

export default {
  name: "App",

  components: {},

  data: () => ({
    posts: null,
  }),
  mounted() {
    axios
      .get("https://hidden-earth-37796.herokuapp.com/posts")
      .then((result) => {
        this.posts = result.data;
      })
      .catch((err) => {
        console.log(err);
      });
  },
};
</script>
