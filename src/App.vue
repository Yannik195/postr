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
        <v-btn
          :loading="loading"
          @click="rickroll"
          elevation="0"
          color="primary"
          x-large
          >post</v-btn
        >
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
    loading: false,
  }),
  methods: {
    post: function () {
      this.loading = true;
      axios
        .post("https://hidden-earth-37796.herokuapp.com/posts", {
          text: this.text,
          userName: "Ich",
        })
        .then((response) => {
          console.log(response);
          this.loadPosts();
        })
        .catch((err) => {
          console.log(err);
        });
    },
    loadPosts: function () {
      axios
        .get("https://hidden-earth-37796.herokuapp.com/new-posts")
        .then((result) => {
          this.posts = result.data.reverse();
          this.text = "";
          this.loading = false;
        })
        .catch((err) => {
          console.log(err);
        });
    },
    rickroll: function () {
      window.open(
        "https://www.youtube.com/watch?v=dQw4w9WgXcQ&ab_channel=RickAstleyVEVO"
      );
    },
  },
  mounted() {
    this.loadPosts();
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
