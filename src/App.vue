<template>
  <div id="app">
    <textarea v-model="inputText"/>
    <button @click="sendPost">投稿</button>
    <post v-for="post in reversePosts" :key="post.id" :text="post.text"/>
  </div>
</template>

<script>
import Post from "./components/Post.vue";

export default {
  name: "app",
  updated: function() {
    console.log(this.posts);
  },
  data: function() {
    return {
      inputText: "",
      currentId: 0,
      posts: []
    };
  },
  computed: {
    reversePosts: function() {
      return this.posts.slice().reverse();
    }
  },
  methods: {
    sendPost: function() {
      this.posts = [
        ...this.posts,
        {
          id: this.currentId++,
          text: this.inputText
        }
      ];
    }
  }
};
</script>

<style>
#app {
  font-family: "Avenir", Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}
</style>
