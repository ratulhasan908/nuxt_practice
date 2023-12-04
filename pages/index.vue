<script>
  export default {
    data() {
      return {
        posts: []
      };
    },
    created() {
      fetch('https://jsonplaceholder.typicode.com/photos')
        .then((res) => res.json())
        .then((posts) => {
          this.posts = posts;
        });
    },


computed: {
  posts: function () {
     return this.posts.slice(0, 10)
     }
  }
  };
</script>

<template>
  <ul>
    <li v-for="post in posts" :key="post.id">
        <div>{{ post.id }}</div>
        <div><img :src="post.url" alt=""></div>
    </li>
  </ul>
</template>