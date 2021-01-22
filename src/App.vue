<template>
  <v-app class="container">
    <div class="ma-4">
      <div class="input">
        <v-text-field
          v-model="text"
          class="mr-4"
          label="Post something"
          single-line
          outlined
        ></v-text-field>
        <v-btn @click="post" elevation="0" color="primary" x-large>post</v-btn>
      </div>

      <Post
        class="pb-4"
        v-for="post in posts"
        :key="post.id"
        :post="post"
      ></Post>
    </div>
  </v-app>
</template>

<script>
import axios from "axios";
import Post from "./components/Post";

export default {
  name: "App",

  components: {
    Post,
  },

  data: () => ({
    posts: null,
    text: "",
  }),
  methods: {
    post: function () {
      axios
        .post("https://hidden-earth-37796.herokuapp.com/posts", {
          text: this.text,
          userName: "Ich",
        })
        .then((response) => {
          console.log(response);
        })
        .catch((err) => {
          console.log(err);
        });
    },
  },
  mounted() {
    axios
      .get("https://hidden-earth-37796.herokuapp.com/new-posts")
      .then((result) => {
        this.posts = result.data;
      })
      .catch((err) => {
        console.log(err);
      });
  },
};
</script>

<style scoped>
.container {
  max-width: 60em;
  margin: 0 auto;
}

.content {
}

.input {
  display: flex;
  align-items: baseline;
}
</style>
