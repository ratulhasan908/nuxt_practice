<script>
  export default {
    data() {
      return {
        posts: []
      };
    },
    created() {
      fetch('https://jsonplaceholder.typicode.com/posts')
        .then((res) => res.json())
        .then((posts) => {
          this.posts = posts;
        });
    }
  };
</script>

<template>
  <ul>
    <li v-for="post in posts" :key="post.id">{{ post.title }}</li>
  </ul>
</template>