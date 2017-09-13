<template>
  <div id="app">
    <button @click="fetchPosts">불러오기</button>
    <ul>
      <li v-for="post in posts">
        <h1>{{ post.title }}</h1>
        <p>{{ post.body }}</p>
      </li>
    </ul>
  </div>
</template>

<script>
export default {
  name: 'app',
  data () {
    return {
      posts: []
    }
  },
  methods: {
    fetchPosts () {
      this.axios.get('https://jsonplaceholder.typicode.com/posts', {
        params: {
          userId: 1
        }
      })
        .then((response) => {
          console.log(response)
          this.posts = response.data
        })
      // this 스코프 해결 방법
      // =>
      // (function () {}).bind()
      // this 대신 self
    }
  }
}
</script>
<style lang="scss">
$point-color: #ffffff;

ul {
  li {
    h1 {
      font-size: 20pt;
      color: red;
    }

    p {
      font-size: 10pt;
      color: blue;
    }
  }
}  
</style>