<template>
  <div id="app">
    <div class="post" v-for="post of posts" :key="post.id">
      <h2>{{post.title}}</h2>
      <p>{{post.body}}</p>
    </div>
    <router-view />
  </div>
</template>


<script>
export default {
  name: "app",
  data() {
    return {
      posts: []
    };
  },
  async mounted() {
    const res = await fetch(
      "https://jsonplaceholder.typicode.com/posts?_limit=10"
    );
    const posts = await res.json();
    this.posts = posts;
    console.log(posts);
  }
};
</script>
<style lang="scss">
#app {
  margin: 60px auto;
  width: 400px;
  text-align: center;
}

.post {
  border: 1px solid #ccc;
  border-radius: 5px;
  margin-bottom: 1rem;
}
</style>
