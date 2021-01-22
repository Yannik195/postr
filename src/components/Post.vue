<template>
  <div>
    <p>{{ post.userName }}</p>
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
p {
  margin: 0;
}
</style>