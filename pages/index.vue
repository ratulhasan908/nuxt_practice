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
    <li v-for="post in posts" :key="post.id">
        <div>{{ post.id }}</div>
        <div>{{ post.title }}</div>
        
    </li>
  </ul>
</template>