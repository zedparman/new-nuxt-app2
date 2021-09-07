<template>
  <div class="container p-5 todos">
      <div class="row">
        <div v-for="post in posts" :key="post.id" class="py-5 todo col-4 position-relative border border-primary text-center">
          <nuxt-link to="single">{{ post.id }}</nuxt-link>
          <div>{{ post.title }}</div>
        </div>
      </div>
  </div>
</template>

<script>
import axios from "axios";
export default {
  data() {
    return {
      posts: [],
    };
  },
  mounted() {
    // Simple GET request using axios
    const posts = axios
      .get("https://jsonplaceholder.typicode.com/posts")
      .then((response) => (this.posts = response.data));
  },
};
</script>

<style scoped>
.todos {
  background-color: crimson;
}

.todo {
  background-color: cyan;
}
</style>