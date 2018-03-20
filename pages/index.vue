<template>
  <section class="container">
    <h2>Blog</h2>
    <ul>
      <li v-for="post in posts" :key="post.id">{{ post.title }}</li>
    </ul>
  </section>
</template>

<script>
import AppLogo from '~/components/AppLogo.vue';
export default {
  components: {
    AppLogo
  },
  data() {
    return {
    posts: null
    }
    
  },
  created() {
    this.load()
  },
  methods: {
    load() {
       // GET /someUrl
      this.$http.get('https://jsonplaceholder.typicode.com/posts').then(response => {

        // get body data
        this.posts = response.body

      }, response => {
        // error callback
      });
    }
  }
};
</script>

<style>
.container {
  min-height: 100vh;
  display: flex;
  justify-content: center;
  align-items: center;
  text-align: center;
}

.title {
  font-family: 'Quicksand', 'Source Sans Pro', -apple-system, BlinkMacSystemFont,
    'Segoe UI', Roboto, 'Helvetica Neue', Arial, sans-serif; /* 1 */
  display: block;
  font-weight: 300;
  font-size: 100px;
  color: #35495e;
  letter-spacing: 1px;
}

.subtitle {
  font-weight: 300;
  font-size: 42px;
  color: #526488;
  word-spacing: 5px;
  padding-bottom: 15px;
}

.links {
  padding-top: 15px;
}
</style>
