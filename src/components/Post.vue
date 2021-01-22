<template>
  <div>
    <p class="ma-0">{{ post.userName }}</p>
    <p>{{ post.text }}</p>
  </div>
</template>

<script>
export default {
  name: "Post",
  props: ["post"],
  data: () => ({}),
  mounted() {},
};
</script>

<style scoped>
</style>