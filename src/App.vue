<template>
  <div>
    <button @click="increment += 1">+1</button>
    <button @click="increment -= 1">-1</button>
    <p>Кнопка выше была нажата {{ increment }} раз</p>
  </div>
</template>


<script>
export default {
  name: "app",
  data() {
    return {
      increment: 0
    };
  },
  computed: {
    allPosts() {
      return this.$store.getters.allPosts;
    }
  },
  async mounted() {
    const res = await fetch(
      "https://jsonplaceholder.typicode.com/posts?_limit=3"
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
